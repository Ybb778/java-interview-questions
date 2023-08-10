JSP 技术
======

## 说一说 Servlet 的生命周期？

1.  `Servlet` 有良好的生存期的定义，包括加载和实例化、初始化、处理请求以及服务结束。这个生存期由 javax.servlet.Servlet 接口的 `init()`,`service ()` 和 `destroy` 方法表达。
2.  `Servlet` 被服务器实例化后，容器运行其 `init` 方法，请求到达时运行其 `service` 方法，service 方法自动派遣运行与请求对应的 do\*\*\*() 方法（doGet，doPost）等，当服务器决定将实例销毁的时候调用其 `destroy` 方法。
3.  `Web` 容器加载 `Servlet`，生命周期开始。通过调用 `Servlet` 的 `init ()` 方法进行 `Servlet` 的初始化。通过调用 `service()` 方法实现，根据请求的不同调用不同的 do\*\*\*() 方法。结束服务，`Web` 容器调用 `Servlet` 的 destroy () 方法。

## JSP 和 Servlet 的区别、共同点、各自应用的范围？

JSP 是 Servlet 技术的扩展，本质上就是 Servlet 的简易方式。JSP 编译后是 “类 servlet”。Servlet 和 JSP 最主要的不同点在于：Servlet 的应用逻辑是在 Java 文件中，并且完全从表示层中的 HTML 里分离开来。而 JSP 的情况是 Java 和 HTML 可以组合成一个扩展名为.jsp 的文件。JSP 侧重于视图，Servlet 主要用于控制逻辑。在 struts 框架中，JSP 位于 MVC 设计模式的视图层，而 Servlet 位于 控制层.

## Servlet API 中 forward () 与 redirect () 的区别？

*   从地址栏显示来说

1. `forward` 是服务器请求资源，服务器直接访问目标地址的 URL, 把那个 URL 的响应内容读取过来，然后把这些内容再发给浏览器。浏览器根本不知道服务器发送的内容从哪里来的，所以它的地址栏还是原来的地址。
2. `redirect` 是服务端根据逻辑，发送一个状态码，告诉浏览器重新去请求那个地址。所以地址栏显示的是新的 URL. 所以 redirect 等于客 户端向服务器端发出两次 request，同时也接受两次 response。

*   从数据共享来说

1. `forward`: 转发页面和转发到的页面可以共享 request 里面的数据.
2. `redirect`: 不能共享数据.redirect 不仅可以重定向到当前应用程序的其他资源，还可以重定向到同一个站点上的其他应用程序中的资源，甚至是使用绝对 URL 重定向到其他站点的资源.forward 方法 只能在同一个 Web 应用程序内的资源之间转发请求.forward 是服务器内部的一种操作.redirect 是服务器通知客户端，让客户端重新发起请求。
> 所以，你可以说 redirect 是一种间接的请求，但是你不能说” 一个请求是属于 forward 还是 redirect “。

*   从运用地方来说

1. `forward`: 一般用于用户登陆的时候，根据角色转发到相应的模块. 
2. `redirect`: 一般用于用户注销登陆时返回主页面和跳转到其它的网站等。

*   从效率来说

1. `forward`: 高。

2. `redirect`: 低。

## request.getAttribute () 和 request.getParameter () 有何区别？

1.  `getParameter()` 取得是通过容器的实现来取得通过类似 post，get 等方式传入的数据。
2.  `getAttribute()` 是返回对象，`getParameter()` 返回字符串。
3.  `getAttribute()` 一向是和 `setAttribute()` 一起使用的，只有先用 `setAttribute()` 设置之后，才能够通过 `getAttribute()` 来获得值，它们传递的是 Object 类型的数据。而且必须在同一个 request 对象中使用才有效。, 而 `getParameter()` 是接收表单的 get 或者 post 提交过来的参数。

## MVC 的各个部分都有那些技术来实现？如何实现？

MVC 是 Model－View－Controller 的简写。Model 代表的是应用的业务逻辑（通过 JavaBean，EJB 组件实现），View 是应用的表示面（由 JSP 页面产生），Controller 是提供应用的处理过程控制（一般是一个 Servlet），通过这种设计模型把应用逻辑，处理过程和显示逻辑分成不同的组件实现。这些组件可以进行交互和重用。

## JSP 有哪些内置对象？作用分别是什么？

1.  `request` 用户端请求，此请求会包含来自 GET/POST 请求的参数；
2.  `response` 网页传回用户端的回应；
3.  `pageContext` 网页的属性是在这里管理；
4.  `session` 与请求有关的会话期；
5.  `application` 封装服务器运行环境的对象；
6.  `out` 输出服务器响应的输出流对象；
7.  `config Web` 应用的配置对象；
8.  `page JSP` 网页本身；
9.  `exception` 封装页面抛出异常的对象。

## 说一下 JSP 的 4 种作用域？

1.  page：代表与一个页面相关的对象和属性。
2.  request：代表与客户端发出的一个请求相关的对象和属性。一个请求可能跨越多个页面，涉及多个 Web 组件；需要在页面显示的临时数据可以置于此作用域。
3.  session：代表与某个用户与服务器建立的一次会话相关的对象和属性。跟某个用户相关的数据应该放在用户自己的 Session 中。
4.  application：代表与整个 Web 应用程序相关的对象和属性，它实质上是跨越整个 Web 应用程序，包括多个页面、请求和会话的一个全局作用域。

## Session 和 Cookie 有什么区别？

1.  存储位置不同：Session 存储在服务器端；Cookie 存储在浏览器端。
2.  安全性不同：Cookie 安全性一般，在浏览器存储，可以被伪造和修改。
3.  容量和个数限制：Cookie 有容量限制，每个站点下的 Cookie 也有个数限制。
4.  存储的多样性：Session 可以存储在 Redis 中、数据库中、应用程序中；而 Cookie 只能存储在浏览器中。

## 说一下 Session 的工作原理？

Session 的工作原理是客户端登录完成之后，服务器会创建对应的 Session，Session 创建完之后，会把 Session 的 ID 发送给客户端，客户端再存储到浏览器中。这样客户端每次访问服务器时，都会带着 Session ID，服务器拿到 Session ID 之后，在内存找到与之对应的 Session 这样就可以正常工作了。

## JSP 三大指令是什么？

1.  Page ：指令是针对当前页面的指令；
2.  Include ：用于指定如何包含另一个页面；
3.  Taglib ：用于定义和指定自定义标签。

## http 的响应码 200，404，302，500 表示的含义分别是？

*   200 – 确定。客户端请求已成功
*   404 – 未找到文件或目录
*   302 – 临时移动转移，请求的内容已临时移动新的位置
*   500 – 服务器内部错误

## 如何解决表单提交的中文乱码问题？

*   设置页面编码，若是 jsp 页面，需编写代码:

```jsp
<%@page language="java" pageEncoding="UTF-8" contentType="text/html;charset=UTF-8" %>
```

若是 html 页面，在网页头部（ <head>< /head> ）中添加下面这段代码:

```html
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
```

*   将 form 表单提交方式变为 post 方式，即添加 `method="post"`；在 Servlet 类中编写代码 `request.setCharacterEncoding("UTF-8")`，而且必须写在第一行。
*   如果是 get 请求，在 Servlet 类中编写代码 `byte [] bytes = str.getBytes("iso-8859-1")`;`String cstr = newString(bytes,"utf-8")`; 或者直接修改 Tomcat 服务器配置文件 server.xml 增加内容：`URIEncoding="utf-8"`

## 你的项目中使用过哪些 JSTL 标签？

项目中主要使用了 JSTL 的核心标签库，包括 `<c:if>`、`<c:choose>`、`<c:when>`、`<c:otherwise>`、`<c:forEach>` 等，主要用于构造循环和分支结构以控制显示逻辑。虽然 JSTL 标签库提供了 `core`、`sql`、`fmt`、`xml` 等标签库，但是实际开发中建议只使 用核心标签库（core），而且最好只使用分支和循环标签并辅以表达式语言（EL），这样才能真正做到数据显示和业务逻辑的分离，这才是最佳实践。

## 怎么防止重复提交？

1.  禁掉提交按钮。表单提交后使用 Javascript 使提交按钮 disable。这种方法防止心急的用户多次点击按钮。但有个问题，如果客户端把 Javascript 给禁止掉，这种方法就无效了。
2.  Post/Redirect/Get 模式。在提交后执行页面重定向，这就是所谓的 Post-Redirect-Get (PRG) 模式。简言之，当用户提交了表单后，你去执行一个客户端的重定向，转到提交成功信息页面。这能避免用户按 F5 导致的重复提交，而其也不会出现浏览器表单重复提交的警告，也能消除按浏览器前进和后退按导致的同样问题。
3.  在 session 中存放一个特殊标志。当表单页面被请求时，生成一个特殊的字符标志串，存在 session 中，同时放在表单的隐藏域里。接受处理表单数据时，检查标识字串是否存在，并立即从 session 中删除它，然后正常处理数据。如果发现表单提交里没有有效的标志串，这说明表单已经被提交过了，忽略这次提交。
4.  在数据库里添加约束。在数据库里添加唯一约束或创建唯一索引，防止出现重复数据。这是最有效的防止重复提交数据的方法。

## Request 对象的主要方法有哪些？

<table><tbody><tr><td>方法</td><td>解释</td></tr><tr><td>setAttribute(String name,Object)</td><td>设置名字为 name 的 request 的参数值</td></tr><tr><td>getAttribute(String name)</td><td>返回由 name 指定的属性值</td></tr><tr><td>getAttributeNames()</td><td>返回 request 对象所有属性的名字集合，结果是一个枚举的实例</td></tr><tr><td>getCookies()</td><td>返回客户端的所有</td></tr><tr><td>getCharacterEncoding()</td><td>返回请求中的字符编码方式 = getContentLength () ：返回请求的 Body 的长度</td></tr><tr><td>getParameter(String name)</td><td>获得客户端传送给服务器端的有 name 指定的参数值</td></tr><tr><td>getRequestURI()</td><td>获取发出请求字符串的客户端地址</td></tr><tr><td>getRemoteAddr()</td><td>获取客户端的 IP 地址</td></tr><tr><td>getRemoteHost()</td><td>获取客户端的名字</td></tr><tr><td>getServletPath()</td><td>获取客户端所请求的脚本文件的路径</td></tr><tr><td>getServerPort()</td><td>获取服务器的端口号</td></tr><tr><td>removeAttribute(String name)</td><td>删除请求中的一个属性</td></tr></tbody></table>

## JSP 中动态 include 和静态 include 的区别？

*   静态 include：语法：

```jsp
<%@ include file="文件名" %>
```

相当于复制，编辑时将对应的文件包含进来，当内容变化时，不会再一次对其编译，不易维护。

*   动态 include：语法：

能够自动检查被包含文件，当客户端对 JSP 文件进行请求时，会重新将对应的文件包含进来，进行实时的更新。

## 什么情况下调用 doGet () 和 doPost ()?

默认情况是调用 `doGet()` 方法，JSP 页面中的 Form 表单的 method 属性设置为 post 的时候，调用的为 `doPost()` 方法；为 get 的时候，调用 `deGet()` 方法。

## get 和 post 的区别？

1.  get 是用来从服务器上获取数据，而 post 是用来向服务器传递数据；
2.  get 将表单中数据按照 variable=value 的形式，添加到 action 所指向的 URL 后面，并且两者用”？” 连接，变量之间用”&” 连接而 post 是将表单中的数据放在 form 的数据体中，按照变量与值对应的方式，传递到 action 所指定的 URL；
3.  get 是不安全的，因为在传输过程中，数据是被放在请求的 URL 中；而 post 的所有操作对用户来说都是不可见的；
4.  get 传输的数据量小，这主要应为受 url 长度限制；而 post 可以传输大量的数据，所有上传文件只能用 post 提交；
5.  get 限制 form 表单的数据集必须为 ASCII 字符；而 post 支持整个 IS01 0646 字符集；
6.  get 是 form 表单的默认方法。