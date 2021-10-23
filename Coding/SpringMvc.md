服务器分为三层框架：

- 表现层 ： SpringMvc
- 业务层
- 持久层

MVC模型：

- model 模型： JavaBean
- View 视图： JSP
- Controller 控制器： Servlet

MVC的角色划分：

- 前端控制器（DispatcherServlet)
- 请求到处理器映射（HandlerMapping)
- 处理适配器（HandlerAdapter
- 试图解析器（ViewResolver
- 处理器或页面控制器（Controller
- 验证器（Validator
- 命令对象（Command
- 表单对象（Form Object

MVC处理请求的机制是一个核心控制器

- SpringMvc 的入口是 Servlet
- SpringMvc是基于方法设计的

DispatcherServlet: 控制作用，指挥中心 

![](https://i.imgur.com/u4So8oc.jpg)

![](https://i.imgur.com/hK9z4IG.jpg)



`@RequestMapping`

可以作用在Method或者Type（类，接口）上

属性：

- Value/ Path
- Method ： GET， POST , .. ( `method={RequestMethod.POST}` )

注：超链接一定会发送GET请求方式



请求参数的绑定：



























