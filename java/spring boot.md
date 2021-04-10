### Spring boot
Spring Boot是一个快速开发框架,可以迅速搭建出一套基于Spring框架体系的应用  

* 如何使用  
 1.创建Maven工程,在pom.xml中导入相关依赖  

```
<!--继承父包-->
<parent>
<groupId>org. spr ingfr amework。boot</groupId>
<artifactId>spring-boot-starter -parent</artifactId>
<version>2.0.7. RELEASB</version>
</parent>
cdependene ies>
<1-- web启动jar -->
<dependency>
<groupId>org . spr ingfranework . boot</groupId>
<artifactId>spring-boot-starter -webc/ artifactId>
</ dependency>
<dependency>
<groupId>org . projectlombok</groupId>
<artif actId> lombok</ artifactId>
cversion>1.18.6</version>
<scope>provided< / scope>
</ dependeney>
</dependencies>
```
2.创建一个接口,并实现它,并在类上标注@repository交给ioc容器实例  
3.在handler中使用@autowired自动装配,通过实例接口的形式==实际创建一个实现类的对象==.  
4.springboot中不需要tomcat来实现服务器功能,而是需要创建一个启动类Application类(并在其上标注@SpringBootApplication),main方法中使用SpringApplication.run(xx)
> 修改服务器端口需要在resources中创建一个application.yml中写如下,即可修改端口  

```
server:
    port:9090
```


```
package com. southwind;
import org . spr ingframework . boot . Spr ingApplication;
import org . spr ingframework。boot . autoconf igure . Spr ingBootApplicat ion;
0Spr. ingBootApplication
public class Application (
public static void main(String[ ] args) {
SpringApplication. run(Application. class, args);
}
}
```

* RESTful风格的url方式:  
 1.map("/xxx/{id}"):参数需要用{}括起,且没有key只有value  
2.在业务方法获得参数时:在形参列表在参数前面要加上 @Pathvariable("id"),才能是参数映射到后面的形参  

### 数据检验
xxx



### 整合Mybatis  
* 1.建立一个maven工程,在pom.xml中导入相关依赖  

```
<parent>
<groupId>org. spr ingfr amework . boot</groupId>
<artifactId> spr ing-boot-parent</artifactId>
cversion>2.1.5。RELEASE</version>
</parent>
<dependencies>
<dependency>
sgroupId>org. spr ingfr amework。bootc/ groupId>
<artifactId> spr ing-boot -starter -web</artifactId>
</dependency>
<dependency>
groupId>org. mybat 18。spring. boot</ groupId>
<artifactId>mybatis- spr ing-boot-s tarter</artifactId>
<version>1.3.1</version>
</dependency>
<dependency>
<groupId>mysq1</groupId>
<artifactId>mysql- connector - java</artifactId>
<version>8.0.15</version>
</dependency>
<dependeney>
<groupId>org. projectlombok</ groupId>
<artifactId> lombok</ artifactId>
</ dependency>
</ dependencies>
```

* 2.在数据库中创建表
* 3.在java文件夹中创建一个包,再在包中创建一个表类.java文件(类中属性要与表中字段对应,再添加@Ddata自动生成类的基础方法)  
* 4.创建Repository接口(用于将其实现类的实例对象交给ioc管理)  

```
package com. southwind.repository;
import com. southwind。entity. student ;
import java. util .List;
publie inter face StudentRepos itory {
public List<student> findA11();
public Student findById(Long id);
public vold save (Student student);
public vold update(student student);
public vold deleteById(Long id);
```

* 5.在resources/mapping路径下创建repository接口对应的Mapper.xml(其实现接口中具体方法的sql语句)  
 在mapper.xml中,namespace等于接口类的路径全名  
然后再逐个实现接口中方法对应的sql语句  

```
<?xml version="1.0" encoding-"UTF-8" ?2>
<IDOCTYPE mapper PUBLIC "-//mybatis. org//DTD Mapper 3.0//EN"
"http://mybatis .org/dtd/mybatis-3-mapper . dtd">
<mapper nanespace=" com. southwind. repository . StudentRepository">
<select id=" findAll" resultType= " Student">
select* from student
</select>
<select id=" findById" par ameterType- " java. lang.Long" resultType-" Student">
se1ect申from student where id■#(id}
</nelect>
<ingert id=" save" parameterType- " Student">
insert into student (name , score , birthday) values (#(name},#(score) ,#(birthday))
</insert>
<update id= "update”par ameterType- " Student">
update student set name■#{name },score■#{score} 。birthday=#(birthday) where id■
{id}
</update>
<delete id= ”deleteById" par ameterType-" java. lang . Long">
delete from student where id = #{id}
</delete>
</mapper>
```

* 6.创建handler,在handler上加@repository就可以在业务方法中使用接口名来使用实现类对象(与数据库连接不需要repository?只要创建接口对象使用@autowire的?)
* 7.创建配置文件,在resources下创建application.yml(用于连接数据库)  

```
spring:
    datasource :
        url: jdbc :mysql://localhost:3306/mbtest?useUnicode=true &characterEncoding=UTF-8
        username: root
        password: 19900310
        driver-class-name: com. mysql.cj . jdbc . Driver
mybatis:
    mapper-locations: classpath: /mapping/* . xml
    type-aliases-package: com. southwind.entity
```
* 8.创建启动类application(要在启动类上添加@MapperScan("xx.xx.repository")来扫描repository(其由mybatis管理))



* 与Mybatis整合流程  
 1.在entity中创建实体类,(@Data)   
2.在repository中创建实体类的接口(接口中定义与数据库操作相关的基础方法)  
3.在resources/mapping中在接口文件.xml中实现在接口中定义的方法(其中参数需要用#{参数})  
4.在control文件夹中创建相关handler,在业务中要操作相关表,只需要定义相关的接口,使用其中定义的方法即可(接口需要@autowired)