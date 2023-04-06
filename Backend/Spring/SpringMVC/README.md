Spring MVC 框架
=============

## 什么是 Spring MVC？

Spring MVC 是 Spring 的一个模块，基于 MVC 的一个框架，无需中间整合层来整合。

## Spring MVC 工作原理？

1.  客户端发送请求到 DispatcherServlet；
2.  DispatcherServlet 查询 handlerMapping 找到处理请求的 Controller、Controller 调用业务逻辑后，返回 ModelAndView；
3.  DispatcherServlet 查询 ModelAndView，找到指定视图、视图将结果返回到客户端。

## Spring MVC 流程？

1.  用户发送请求至前端控制器 DispatcherServlet。
2.  DispatcherServlet 收到请求调用 HandlerMapping 处理器映射器。
3.  处理器映射器找到具体的处理器 (可以根据 XML 配置、注解进行查找)，生成处理器对象及处理器拦截器 (如果有则生成) 一并返回给 DispatcherServlet。
4.  DispatcherServlet 调用 HandlerAdapter 处理器适配器。
5.  HandlerAdapter 经过适配调用具体的处理器 (Controller，也叫后端控制器)。
6.  Controller 执行完成返回 ModelAndView。
7.  HandlerAdapter 将 controller 执行结果 ModelAndView 返回给 DispatcherServlet。h、DispatcherServlet 将 ModelAndView 传给 ViewReslover 视图解析器。
8.  ViewReslover 解析后返回具体 View。
9.  DispatcherServlet 根据 View 进行渲染视图（即将模型数据填充至视图中）。
10.  DispatcherServlet 响应用户。

## 如果你也用过 Struts2. 简单介绍下 Spring MVC 和 Struts2 的区别有哪些？

1.  Spring MVC 的入口是一个 Servlet 即前端控制器，而 Struts2 入口是一个 Filter 过虑器。
2.  Spring MVC 是基于方法开发 (一个 URL 对应一个方法)，请求参数传递到方法的形参，可以设计为单例或多例 (建议单例)，Struts2 是基于类开发，传递参数是通过类的属性，只能设计为多例。
3.  Struts2 采用值栈存储请求和响应的数据，通过 OGNL 存取数据，Spring MVC 通过参数解析器是将 request 请求内容解析，并给方法形参赋值，将数据和视图封装成 ModelAndView 对象，最后又将 ModelAndView 中的模型数据通过 reques 域传输到页面。JSP 视图解析器默认使用 JSTL。

## @RequestMapping 注解用在类上面有什么作用？

是一个用来处理请求地址映射的注解，可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。

## Spring MVC 的控制器是不是单例模式，如果是，有什么问题，怎么解决？

是单例模式，所以在多线程访问的时候有线程安全问题，不要用同步，会影响性能的，解决方案是在控制器里面不能写字段。

## 怎么样在方法里面得到 Request, 或者 Session？

直接在方法的形参中声明 Request,Spring MVC 就自动把 Request 对象传入。

## 如果前台有很多个参数传入，并且这些参数都是一个对象的，那么怎么样快速得到这个对象？

直接在方法中声明这个对象，Spring MVC 就自动会把属性赋值到这个对象里面。

## Spring MVC 中函数的返回值是什么？

返回值可以有很多类型，有 String, ModelAndView, 当一般用 String 比较好。

## Spring MVC 怎么样设定重定向和转发的？

在返回值前面加”`forward:`“就可以让结果转发，譬如”`forward:user.do?name=method4`” 在返回值前面加”`redirect:`“就可以让返回值重定向，譬如”`redirect:http://www.baidu.com`“。

## Spring MVC 怎么和 AJAX 相互调用的？

通过 Jackson 框架就可以把 Java 里面的对象直接转化成 Js 可以识别的 Json 对象。

具体步骤如下 ：

1.  加入 Jackson.jar
2.  在配置文件中配置 Json 的映射
3.  在接受 AJAX 方法里面可以直接返回 Object,List 等，但方法前面要加上 @ResponseBody

## 如何解决 POST 请求中文乱码问题，GET 的又如何处理呢？

解决 post 请求乱码问题：在 web.xml 中配置一个 CharacterEncodingFilter 过滤器，设置成 utf-8；

```xml
	<filter>
	    <filter-name>CharacterEncodingFilter</filter-name>
	    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
	    <init-param>
	        <param-name>encoding</param-name>
	        <param-value>utf-8</param-value>
	    </init-param>
	</filter>
	<filter-mapping>
	    <filter-name>CharacterEncodingFilter</filter-name>
	    <url-pattern>/*</url-pattern>
	</filter-mapping>
```

get 请求中文参数出现乱码解决方法有两个：

*   修改 tomcat 配置文件添加编码与工程编码一致，如下：

```xml
	<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
```

*   另外一种方法对参数进行重新编码：

```java
	String userName = new String(request.getParamter("userName").getBytes("ISO8859- 1"),"utf-8")
```

ISO8859-1 是 tomcat 默认编码，需要将 tomcat 编码后的内容按 utf-8 编码。