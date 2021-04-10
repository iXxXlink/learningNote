## 一.request
* 获得==客户端==传来的参数的值  
`getParameter(key)`
* 通过键值对的形式在服务端保存数据  
`setAttribute(key,value)`
* 获得==服务器==内部的参数资源(即setArribute存储的值)的值  
`getAttribute(key)`
* 页面转向xx.jsp，并将输入、内部存入参数(上面2个函数)、和==输出任务==交给xx.jsp  
`getRequestDispatcher(“xx.jsp”).forward(request，response)`
* 获得客户端传来的所有同名参数的值(getParameter只获得第一个值),并返回一个数组  
`String[] getParameterValues()`
* 指定每个请求的编码  
`void setCharacterEncoding(String charse())`
* 获得session对象  
`HttpSession getSession()`

## 二.response
重定向:和forward一样用于页面跳转,只不过不能传递服务器内部参数.==(sendRedirect是重定向,即浏览器重新发一个新的请求到目标jsp,地址栏会变;foward是转发,即在之前的请求基础上添加参数再传递给目标jsp,地址栏不变)==
`sendRedirect("xx.jsp")`

##Session  
服务器无法识别每一次HTTP请求的出处(不知道来自哪个终端),它只会接受到一个请求信号,所以就存在问题:将用户的请求发送给其他人,必须有一种技术让服务器知道请求来自哪  

==Session会话的生命周期开始于浏览器第一次访问服务器,结束于关闭浏览器==  

==但请求request的生命周期短暂,关闭页面或更改地址栏访问其他页面当前request的生命周期都会结束.所以使用request存储参数的使用范围具有局限性,而session的使用范围大==

属于一个会话有一个相同的sessionId  

服务器会自动使用sessionId识别会话,通常不需要开发者使用
* 获得sessionId  
`getId()`
* 设置Session失效时间,单位S  
 `void setMaxInactiveInterval(int interval)`
*  获得当前的失效时间  
`int getMaxInactiveInterval()`
* 设置Session立即失效 ==(登录退出时)==  
`void invalidate()`
* session对象也可以存数据(也可用于修改)==(生命周期长于request中的参数)==  
`void setAttribute(key,value)`
* 取出session对象中的数据  
`getAttribute(key)`
* 删除key对应的值的参数  
`removeAtrribute(key)`
 




    
