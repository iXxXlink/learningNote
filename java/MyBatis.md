*ORM 对象关系映射  
即在Java中用对象来管理关系型数据库  
* 如何使用
 1.新建maven工程、在porm.xml中导入相关依赖  
 2.新建数据表对应的实体类（包含相同的属性和名字，同时用@Data注释给该类提供基础方法）  
3.在resources中新建一个xml文件，在其中配置mybatis运行环境。  

```
<7xml version="1.0" encoding="UTF-8"?>
<IDOCTYPE configuration PUBLIC ”-//mybatis.org//DTD Config 3.0//EN"
"http:/ /mybatis . org/dtd/mybatis-3-config.dtd">
conf igurat ion>
<1--配置MyBatis运行环境-->
<environments defaultm" deve lopment">
cenvironment id- " development">
<1--配置JDBC事务管理-->
<transactionManager type- ”JDBC "></transact ionManager>
<1-- POOLED配置JDBC数据源连接池-->
<dataSource type-" POOLED">
<property name-"driver" value= " com. mysq1.cj. jdbe . Driver "></property>
<property name- "url" value-" jdbe:mysql ://localhost: 3306/mybatis?
useUnicode-trues amp; characterEncoding=UTF-8"></property>
<property name-"username" value= " root "></property>
<property name" password" value=" 19900310"></property>
</dataSource>
</ environment>
</environment8>
</conf iguration>
```

* 再写一个xml实现OR映射，和sql方法的实现  

```
<?xml version="1.0" encoding- "UTP-8" ?>
<IDOCTYPE mapper PUBLIC "-/ /mybatis . org//DTD Mapper 3.0//EN"
"http://mybatis . org/ dtd/mybatis-3-mapper .dtd">
<mapper nanespace=" com. southwind . mapper。AccoutMapper ">
<insert id-"save" par ameterType-”com. southwind. entity .Aecount ">
insert into t. account(username , password, age) values (# (username} ,#(password},#{age})
</ insert>
</mapper>
```

* 使用  
*
```
public class Test {
public static void main(String[] args) {
//加载MyBatis配置文件
InputStream inputStream = Test. class . getClassLoader() . getRes
SqlSess ionFactoryBuilder sqlSess ionFactoryBuilder = new SqLS
SqlSess ionFactory sqlSess ionFactory = sqlSess ionFactoryBuild
SqlSession sqlSession = sq lSessionFactory. openSession(); 
String statement = " com. squthwind. mapper。AccQutMapper。save" ;
Account account = new Account( id: 1L，username: "张三" , password:
sqlSession. insert ( statement , account) ;
}
sqlSession. commit();
}
```

