* spring mvc工作流程  
 1.客户端请求被DisptacherServlet捕获（DisptacherServlet需要再xml中配置）  
2.然后根据请求内容被handlerMapping映射到对应业务上（业务方法上面需要用注释@RequestMapping("URL")标明映射）（也要加@controller表明是控制器）（也可以在业务类上加@RequestMapping("URL")，这样查询某一业务方法时URL为类映射/方法映射）  
3.业务方法执行完毕后会return返回一个逻辑视图给DispatcherServlet,然后DispatcherServlet将逻辑视图交给viewResolver（需要在xml中配置，依靠添加前置和后置）进行解析，生成一个物理视图路径  
4.然后根据物理视图路径在根目录下寻找相应资源并返回给客户端  


* spring MVC 注解
1.@RequestMapping:将URL和请求于业务方法进行映射（字段value表示映射的url，method表示只接受相应类型（put、get、post、delet）的请求,params表示请求必须包括的参数）  
2.@Controller：在类定义处添加，作用为将该类交给IOC容器来管理（ioc实例一个对象），同时使其类成为一个控制器handler，可以接受客户端请求  
3.@responseBody:handler业务方法上的注释，表面该业务方法返回值不经过视图解析器寻找相应jsp，而是直接将内容返回到客户端  

4.==RestController==:在业务类上标注,表示其类中所有方法都是直接返回给客户端,不经过解析  

5.@GetMapping("yrl"),(还有Post.put,delet)标注在业务方法上,作用是映射并且只接受相应请求  

6.@Repository写在类上(该类要实现某一接口),将该类交给ioc自动创建,然后含handler中可以定义一个接口(其上表上@Autowired)(====接口名指向其实现类中自动创建的一个对象====),就可以通过创建的一个接口名使用其子类对象(因为@repository已经创建了一个对象,然后通过@Autowired自动装配使得接口名就可以使用这个ioc中自动创建的对象)

* 在handle的业务方法中如何获得请求的参数：直接在业务方法的形参列表中定义==同名==参数即可  
* 如何形参和实参名字不同时：在形参列表前加上@RequestParam（“name”）即可完成实参到形参的映射

* 在handler中获得Cookie：业务方法的形参列表中，某一形参前加上@CookieValue（value=“XXXXX”），即可使其形参获得cookie中xxxx的值  
* 业务方法的形参能能有对象，但是传递参数的id要和对象参数名相对应
* 如果形参中的对象还有某个属性为对象，则请求页面传递的参数的id需要包含该子对象属性，即将某个参数作为实参传给子对象的构造器，生成一个子对象，然后自动将此子对象添加到原对象的属性中去
* 过滤器：在web.xml中添加过滤器

```
<filter>
<filter-name>encodingFilter</filter-name>
<filter-class>org。spr ingf ramework . web. filter。CharacterEncodingFilter</filter-cla8a>
<init-param>
<par am-name>encoding</ param name>
<par am-value>UTP-8</par am-value>
</init-par am>
</filter>
<filter-mapping>
<filter -name>encodingFilter</ f ilter -name>
<url-pattern>/*</url-pattern>
</filter-mapping>
```
### 数据类型
* 数据绑定:在后端业务方法中直接获取客户端HTTP请求中的参数,将参数映射到业务方法的形参中  
* 基本数据类型:将要获取的参数写在形参列表即可获得,如果要解决没有参数传递过来的获得NULL的报错问题,将形参列表的参数格式改为包装类即可(==请求的参数名要和业务方法形参列表中的参数名一致==)  
* 如果参数名不一致,需要在形参前面加上@RequestParam(value='name',required=,defaultValue=)进行映射 
*  如果请求参数有多个重名,可以在形参列表使用数组来接受  
* 当返回给客户端出现乱码时:  
*
```
<mve: annotation-dr iven>
<!--消息转换器--> !
<mve imessage- converters register-defaults=" true">
<bean c1ass- ”org. spr ingf r anework . http. converter . Str ingHt tpMessageConverter ">
<property name=" supportedMediaTypes" value=" text/html ; charset=UTP-8">
</property>
</bean>
</mvc :message- converters>
< /mve : annotation-dr iven>

```
### json
* 形参列表参数前要加@RequestBody(表示将json格式数据赋给一个对象)  

### 模型数据
springMvc提供以下几种方法添加模型数据:  
1.map  
2.Model  
3.ModelAndView  
(前三个给request里添加)
4.@SeesionAttribute  
5.@ModelAttribute  
* Map  
1.handler先要获得map,在形参列表中添加Map<String,User> map,即可获得一个map  
2.向map中添加数据,map.put("key",value),即向request中添加了数据  
3.在handler中解析返回的jsp中,就可以直接使用requestScope.key获得从handler传递的数据  

* model与map差不多
* modelAndView
* 可以在形参列表中直接添加HttpServletRequest request然后在业务方法中使用request.setAttribute(key,value)存储数据
* @modelAtrribute  
 在某一方法上面注释@modelAtrribute ,表明此方法会在所有方法执行前先执行此方法,并且其return值会进入request.

* 向session中添加参数:  

1.在参数表添加HttpServletRequest request,然后使用httpSession session = request.getSession()获得session,使用session.setAttribute(key,value)存储参数,最后再jsp中使用sessionScape.key取出参数
 
 2.或者在直接在参数列表http Session session获取.
 
 3.......
 
 
 
 * 自定义数据转换器
   1.将客户端输入的String类型数据"2019-1-1"转为Data类型对象:  
①创建一个DataConverter转换器,实现Conveter接口  

``` 
public class DateConverter implements Converter<string, Date> {
private String pattern;
public DateConverter (String pattern){
this.pattern■pattern;
}
Qoverride
publie Date convert(String 8) {
SimpleDateFormat simpleDateFormat ■new SimpleDateFormat(this.pattern);
Date date■nu1l; !
try (
date■simpleDateFormat。parse(8); 
》catch (ParseExeeption e) {
e. printstackTrace();
return date ;
}
}
```
②在springmvc.xml中配置转换器  

```
<!--配置自定义转换器
<bean id= " convers ionService"
楠高教你学Jva
class-"org. spr ingfr amework。context。support。Convers ionServiceF actoryBean">
<property name=" converters">
<list>
<bean class=" com. southwind。converter . DateConverter ">
<constructor-arg type=" java. lang. String" value="yy-M-dd"></ const ructor-
arg>
</bean>
</li8t>
</property>
</bean>
<mve : annotation-driven conversion- servicem " conversionService">
<1--消息转换器-->
<mve imssage-converters register-dofaults- ”true">
<bean class- ”org . spr ingframework . http. converter . Str ingHttpMessageConverter">
<property name-" suppor tedMediaTypes" value=" text/html;charset=UTP-8">
</property>
</bean>
<I--配置fastjson -->
cbean class- com. alibaba. fastjson. support。spr ing。FastJsonHttpMess ageConverter4">
</bean>
</mve :message-converters>
</mve : annotation-dr iven>
```
③使用方法:和形参列表中string转为int一样,只要在形参中定义好转换后的格式和参数(例如 Data date),然后输入的值符合xxxx-xx-xx(模板格式),且传入变量name与形参name相同,则可以自动进行转换并获得Data类型的数据


* @Repository写在类上(该类要实现某一接口),将该类交给ioc自动创建,然后含handler中可以定义一个接口(其上表上@Autowired)(====接口名指向其实现类中自动创建的一个对象====),就可以通过创建的一个接口名使用其子类对象(因为@repository已经创建了一个对象,然后通过@Autowired自动装配使得接口名就可以使用这个ioc中自动创建的对象)


