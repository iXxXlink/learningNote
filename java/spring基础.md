### spring框架两大核心机制
 * IOC(控制翻转)  
 * AOP(面向切面编程)
 


#### IOC
* 在XML中配置添加需要管理的对象,并可以赋初值proper  
* 当需要从ioc中获得对象时,需要先加载配置文件,再获得相应需要的对象  
* di,注入,即对象成员中有其他对象,需要用rer,或者自动装配autowire=byname/byType



#### AOP
* 将多个业务handle?中的公共功能统一管理,提高代码复用率
* 在运行时,动态地将代码切入到类的指定方法、指定位置
* 使用  
 1.创建maven工程，再porm.xml中添加  

```
<dependeneies>
<dependency>
<groupI d>org. spr ingframework</ groupId>
<artifactId> apr ing- aop/artifactId>
<version>5.0.11. RELEASE</version>
</dependency>
<dependeney>
<groupId>org. spr ingtframowork</ groupId>
cartifactId> spring- aspecta</artifactId>
<version>5.0.11。RELEASE</vers ion>
</ dependeney>
</dependencies>
```
* AOP使用过程
 1.实例化一个委托对象(对对象内的业务方法进行面向切口编程)  
2.实例一个代理对象(通过使用MyInvocationHandler implements Invocation类中band()来实现代理类)
3.调用代理对象中的方法.(代理对象中方法与业务对象中方法一样)


* MyInvocationHandler类  
1.作用:创建代理类  
2.实现InvocationHandler类  
3.invoke(Object proxy,Method method,Object[] args)(参数分别为代理对象,使用的方法,参数列表)  
4.在invoke中抽象写出所有方法的流程,其中method.incoke(this.object,args);表示委托对象调用某一方法后的返回值

* AOP流程  
1.创建一个委托对象  
2.创建一个InvocationHandler对象  
3.使用InvocationHandler的bind(委托对象)返回一个代理对象.  
4.由于代理对象实现了委托对象中的全部接口,所以代理对象能使用与委托对象同名的方法  
5.但代理对象使用了方法(所有方法)后进入的是InvocationHandler的invoke(Object proxy,Method method,Object[])方法,在此invoke方法中的method.incoke(this.object,args)表示委托对象使用相同方法返回的值  
6.因此可以在InvocationHandler的invoke()中统一修改委托对象中的方法,实现非业务代码和业务代码(method.incoke(this.object,args))的分割


### 以上是动态代理实现,较为繁琐,下面是spring封装的方法  


```
package com. southwind.aop;
import org. aspectj. lang . JoinPoint;
import org. aspectj. lang . annotation .Aspect;
import org. aspectj. lang . annotation . Before;
import org. spr ingfr amework。stereotype。Component;
import java. util .Arrays;
@Aspect
@component
public class LoggerAspect (
//此处表示Before时要执行before()的方式是CalImpl类中的全部方法.
@Before( "execution(public int com. southwind. utils. impl .CalImpl.*(..))")
public void before (JoinPoint joinPoint){
//获取方法名
String name =joinPoint .getSignature(). getName();
//获取参数
String args =Arrays. tostr ing( joinPoint.getArga());
System.out.println name+"方法的参数是:”+ args);
```
* 注解含义  
 1.@Aspect:表示该类是切面类  
 2.@Component:将该类添加到beans中,加载时实现该类.(委托类也要加次注释)  
 3.方法处的@Before,表示方法执行的具体位置和时机  
4.@Data : 注解在类上, 为类提供读写属性, 此外还提供了 equals()、hashCode()、toString() 方法  
5.@Getter/@Setter : 注解在类上, 为类提供读写属性
6.@ToString : 注解在类上, 为类提供 toString() 方法  
7.

* 还要在spring.xml中配置自动扫描和使Aspect注释生效  



```
<?xml version="1.0" encoding= "UTF-8" ?>
<beans xmlns= ”http: / /ww。spr ingfr amework。org/ schema/ beans "
xm1ns : xsi=" http:/ /ww. wW3。org/ 2001/XMLSchema- instance "
xmlns : context= " http://www。spr ing fr amework。org/ schema/ context'
xmlns:aop-”http:/ /www. spr ingframework . org/ schema/ aop"
xmIns:p= "http:/www. springf ramework. org/ schema/p"
xsi: schemaLocat ion- http:/www. spr ingframework. org/ schema/ aop
http: //www. spr ingf r amework .org/ schema/ aop/ spring- aop-4.3.xsd
http://www. spr ingfr amework. org/ schema/ beans
http://ww. apr ingfranework.org/ schema/beans/spr ing-beang-4.3.xsd
http:/ /www。spr ingfr amework。org/ schema/ context
http: //www. spr ingfr amework .org/ schema/ context/ spr ing-context-4.3.xsd
<l-- 自动扫描-->
context tcomponent-scan base-package”com. southwind"></context tcomponent-sean>
<!--是Aspect注解生效， 为目标类自动生成代理对象-->
<aop: aspectj-autoproxy></ aop:aspectj- autoproxy>
</beans>
```
* 使用方法

```
//加载配置文件
Applicat ionContext applicationContext = new Clas sPathXmLAppl
//获取代理对象
Cal proxy = (Cal) applicat ionContext. getBean( S: "calImpl");
proxy.add(1,1);
proxy. sub(2,1);|
proxy . mul(2,3);
proxy.div(6,0);
```

