## 过滤器 Filter

(对于客户端所有的请求或服务端所有的相应进行拦截并作出一定处理,==目的是提高代码复用率==)  
* 功能:  
1.用于拦截传入的请求或传出的响应  
2.修改或以某种方式处理正在客户端和服务端之间交换的数据流  
* 使用方法:  
 1.在src文件夹中创建filter文件夹,里面的java文件中创建类实现Filter接口  
 2.在doFilter方法中对request或response进行处理  
 3.和servlet一样在xml中进行映射,绑定过滤器和相应的url(如果有servlet也绑定了同一个url,则==先经过过滤器在进入servlet==)
``` jsp
<filter>
<filter-name>charcater</filte r-name>
<filter-c las s>com. southwind. filter . CharacterFilter</filter-c1
</filter>
<filte r-mapping>
<filte r-name>charcater</If ilte r-name>
<url-pattern>/ login</ur l-pattern>
</filter-mapp ing>
```
 4.也可通过@webFilter("url")的方式配置(但对多个过滤器不能决定过滤顺序)  
 
 5.调用filterChain的方法,将请求传递下去(
==必须添加,否则过滤器会拦截请求,但不会自动接着传递下去==
)
```
filterChain.doFilter(servletRequest,servletResponse) ;
```
* 同时配置多个Filter,Filter执行的顺序按照xml中写入的先后顺序
* 过滤器的使用场景:  
 1.统一处理中文乱码  
 2.屏蔽敏感词  
 3.控制资源访问权限(==就是一个私密资源url,别人获取的url,但只在地址栏输入url是无法获取资源==的)


