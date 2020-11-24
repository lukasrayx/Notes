## 基础（ioc控制反转，DI依赖注入）

**框架分层：**

- web层（表现层）： struts， spring-MVC
- service层（业务层）：spring
- dao层（持久层）：hibernate， mybatis， jdbcTemplate， spring-data
  - dao：数据访问层 Data Access Object

![](https://i.imgur.com/OzwA4GD.jpg)















## AOP切面编程，JdbcTemplate

## 事务管理，SSH整合







# Spring MVC 

- M: Model ( JavaBean ) 
- V:  View ( JSP or html )
- C:  Controller

Spring MVC的入口是Servlet，是基于方法设计



# Spring Boot



# Spring-data

**Hibernate**是一个对象关系映射框架，将POJO与数据库表建立映射关系，是一个全自动的orm框架，可以自动生成sql语句，自动执行。

**JPA**（标准）是Java Persistence API的简称，中文名Java持久层API，是JDK 5.0注解或XML描述对象－关系表的映射关系，并将运行期的实体<u>对象持久化</u>到数据库中。是一套规范。（对象持久化是指将内存中的对象保存到可永久保存的存储设备中（如磁盘，xml数据文件）的一种技术。）

**Hibernate JPA**： Hibernate根据JPA规范提供了一套操作持久层的API （熟悉JPA规范的特点）

Spring Data是一个平台，包含了很多其他的模块，用于访问不同的存储模型。

**Spring Data JPA**：Spring Data JPA是Spring Data家族的一部分，可以轻松实现基于JPA的存储库。 此模块处理对基于JPA的数据访问层的增强支持。 它使构建使用数据访问技术的Spring驱动应用程序变得更加容易。底层默认使用的是Hibernate来做的JPA实现。（是Spring Data项目下的一个子模块，提供了一套JPA标准化操作数据库的简化方案，底层默认的依赖是hibernate JPA来实现）**特点：**我们只需要定义接口并继承Spring Data JPA中所提供的接口即可，不需要编写接口实现类。

**Spring Data Redis** ：Spring Data Redis, part of the larger Spring Data family, provides easy configuration and access to Redis from Spring applications. It offers both low-level and high-level abstractions for interacting with the store, freeing the user from infrastructural concerns.提供了一套对于Redis操作的API，可以简化并帮助我们更方便的去操作Redis内存型数据库。

**CRUD**是指在做计算处理时的增加(**Create**)、检索(**Retrieve**)、更新(Update)和删除(**Delete**)几个单词的首字母简写。crud主要被用在描述软件系统中数据库或者[持久层](https://baike.baidu.com/item/持久层/3584971)的基本操作功能。

**POJO**（Plain Ordinary Java Object）简单的Java对象，实际就是普通JavaBeans，是为了避免和EJB混淆所创造的简称。但是它通指没有使用Entity Beans的普通java对象，可以把POJO作为支持业务逻辑的协助类。POJO实质上可以理解为简单的实体类，顾名思义POJO类的作用是方便程序员使用数据库中的数据表，对于广大的程序员，可以很方便的将POJO类当做对象来进行使用，当然也是可以方便的调用其get,set方法。POJO类也给我们在struts框架中的配置带来了很大的方便。

POJO和JavaBean的区别：

- POJO其实是比javabean更纯净的简单类或接口。POJO严格地遵守简单对象的概念，而一些JavaBean中往往会封装一些简单逻辑。
- POJO主要用于数据的临时传递，它只能装载数据， 作为数据存储的载体，而不具有业务逻辑处理的能力。
- Javabean虽然数据的获取与POJO一样，但是javabean当中可以有其它的方法。

**HQL查询**： Hibernate Query Language

**QBC查询：** Query By Criteria，把对数据库的查询形式换成了用对象和方法来替代

通过Name查询：

```java
List<Users> selectUserByName(String uesrname);


@Override
public List<Users> selectUserByName(String usesrname){
  Session session = this.hibernateTemplate. ........
  
}

// P6 HQL查询
```

![](https://i.imgur.com/ge1y8GD.jpg)



**Repository接口：** 所有接口的顶层接口，支持两种查询方式的支持

- 基于方法名称命名规则查询
  - 规则：findBy(关键字) + 属性名称(首字母大写) + 查询条件(首字母大写)
  - 判断相等的条件
    - 什么都不写，默认做相等判断
    - Is
      - `List<Users> findByUsernameIs(String string);`
      - `List<Users> list = this.userDao.findByUsernameIs("Jeff")`
    - Equal
- 基于@Query注解查询



# Thymeleaf

## 使用 th:text

### 



















