## Cookie
* cookie以键值对的形式存储数据,存放在浏览器中
* 浏览器每次访问服务器都会在请求中附带cookie
* 服务器返回时也可能附带cookie,浏览器接收到这个cookie后会添加到自己的cookie文件中,==如果key相同则会覆盖原来的value==
* 服务器中创建并使用cookie的方法
```
Cookie cookie =new Cookie("key","value");
response.addCookie(cookie);
```
* 读取cookie(返回数组)  

```
Cookie[] cookies=request.getCookies();
```
* 循环获得cookie的key和value  

```
for(Cookie cookie:cookies){
        out.write(cookie.getName()+':'+cookie.getvalue()+"<br/>");
    }
```
* 获得最大存活时间 ==(-1表示关闭页面即失活)==

```
int getMaxAge()
```

* 设置最大存活时间  

```
setMaxAge(int)
```

* session与Cookie的对比

 cookie | 保存在浏览器 | String类型|长期保存在浏览器中 ==(相比session的优势,生命周期可能更长)==,与会话无关| 保存不重要信息
---|---|---|---|---
session |保存在服务器 | 类型是object| 随会话结束而销毁| 保存重要信息
### session
* 存储用户信息:  
存 
```
session: setAttribute("name","admin")
```
取

```
getAttribute("name")
```


* 生命周期:  
服务端:只要WEB应用重启就销毁，  
客户端:只要浏览器关闭就销毁。
### cookie
存

```
response.addCookie(new Cookie(name,"admin")
```

取

```
Cookie[] cookies = request . getCookies();
for (Cookie cookie:cookies){
if (cookie. getName().equals( "name")){
out.write( "欢迎回来" +cookie.getValue()); 
}
```


* 生命周期:  
服务端:不随服务端的重启而销毁，  
客户端:默认是只要关闭浏览器就销毁,我们通过setMaxAge()方法设置有效期，一旦设置了有效期，则不随浏览器的关闭而销毁，而是由设置的时间来决定。






