4个内置对象pageContext、request、session、application，都有setAttribution和getAtreibution，用于传递参数，所以需要考虑相应的作用域范围

page<request<session<application

* pageContext:只在当前页面有效,转发,重定向都会失效(几乎用不到,范围太小了  )
* request:在当前请求有效,转发有效,重定向失效
* session:同一次打开浏览器都有效
* application:同一次服务器tomcat连续时间都有效
 
### EL表达式
* 用${变量名}可以代替<%= getAtrribution("变量名")%>来取变量
* 可以从page、request、session、application取变量，优先级依次降低

* 若要使用其属性可以用.属性的方式使用,但在其类中必须要有相应属性的get方法.  

* 指定作用域：${sessionScope.key}
 