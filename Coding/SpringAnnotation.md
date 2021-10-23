简介：

在SpringMVC 中，控制器Controller 负责处理由DispatcherServlet 分发的请求，它把用户请求的数据经过业务处理层处理之后封装成一个Model ，然后再把该Model 返回给对应的View 进行展示。

在SpringMVC 中提供了一个非常简便的定义Controller 的方法，你无需继承特定的类或实现特定的接口，只需使用@Controller 标记一个类是Controller ，然后使用@RequestMapping 和@RequestParam 等一些注解用以定义URL 请求和Controller 方法之间的映射，这样的Controller 就能被外界访问到。此外Controller 不会直接依赖于HttpServletRequest 和HttpServletResponse 等HttpServlet 对象，它们可以通过Controller 的方法参数灵活的获取到。



`@Component` : create a bean(Object)

- `@Component("idOfBean")`

`@Configuration` : tell spring this is a configuration class ( use in config.java )

`@ComponentScan(basePackages = "packageName")` : spring is going to read this particular configuration file ( use in config.java )

`@Bean public College collegeBean()`  :  collegeBean  -  bean id

`@Controller` : 标记在一个类上

- 在Springmvn配置文件中，使用`<context:component-scan/>`， 启动包扫描，以便注册带有`@Controller @Service @repository @Component` 等注解的类成为Spring的Bean
- `<context: component-scan base-package = "路径包">`

`@RequestMapping`  :  用来处理请求地址映射，可用于类或方法上，用于类上，表示类中所有相应请求的方法都是以该地址作为父路径。

- value：制定请求的实际地址
- method：指定请求的method类型， GET、POST、PUT、DELETE等；
- consumes：指定处理请求的提交内容类型（Content-Type），例如application/json, text/html;
- produces：指定返回的内容类型，仅当request请求头中的(Accept)类型中包含该指定类型才返回；
- params：指定request中必须包含某些参数值是，才让该方法处理。
- Headers：指定request中必须包含某些指定的header值，才能让该方法处理请求。













---

`ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml")` : 从类路径加载配置文件

- Context.getBean("beanId", class)

`context:component-sacn base-package="..."` Scan bean













