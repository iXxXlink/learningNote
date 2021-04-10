* 传统java web开发  
 前端->HTML静态页面->后端->jsp  
缺点:耦合度太高  

所以需要前后端分离:前端只需要独立编写客户端代码,后端也只需要独立编写服务端代码提供数据接口即可.  

前后端开发者只需要提前约好接口文档(URL.参数.数据类型...),然后分别独立开发即可,前端可以早假数据进行测试,后端可以用postman测试,最后完成前后端集成即可.

即前后端分离就是将一个完整的服务应用拆分为2个应用,前端应用和后端应用,客户端只需要访问前端应用,然后由前端应用去使用ajax调用后端应用,然后后端应用返回json给前端应用,前端应用再将带有数据的视图返回给客户端



### Vue
* Vue只有一个主页面APP.vue,其他进行调整都只是在主页面的部分位置进行更新模板（需要在js中配置路由，即资源模板代表的url）
*  vue模板包括template、script、style三个大标签，分别写入的是HTML、js、css

* 1.点击后跳转到url页面<router-link to="url">hone<router-link>  
2.然后在router/index.js中创建相关映射,首先在最上面import name(随意取) from "组件的位置",然后在下面的const router数组中,创建一个对象,path属性对应url,name属性对应组件名

* 在一个vue中如何动态获取数据?  在vue的script标签中,即下图的return中用键值对存储数据,然后在template中调用标签时需要{{key}}来使用value(对应的value中可以写数组,然后数组中装对象)

```
export default{
    date(){
        return{
            books:[
                {
                    name='wangwu',
                    id=1    
                },
                {
                    name='zhangsan'
                    id=2
                }
            ]
        }
    }
}
```

* <tr v-for="item in arry"> </tr>就可以用item代替arry中元素遍历,然后循环整个标签内的内容
 
* 如何将数据库中数据加载到vue中呢?  
1.按下图,books即获得了一个装着对象的数组:[{},{},{}]



```
export default{
    date(){
        creat(){
           const _this=this 
           axios.get("url").then(function(resp)){
                _this.book=resp.data
                }
            }
        }
    }
}
```



* 跨域问题:在8080端口的服务请求8181端口的服务会产生跨域问题  
 在com.dbtest.dbkeshe下创建一个config包,在里面创建一个Crosconfig即可
