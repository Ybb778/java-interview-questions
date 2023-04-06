JavaScript 语言和 jQuery 技术
------------------------

### JS 中如何将页面重定向到另一个页面？

1.  使用 location.href：window.location.href =”https://www.baidu.com/”
2.  使用 location.replace：window.location.replace (“https://www.baidu.com/;”);

### undefined，null 和 undeclared 有什么区别？

1.  undefined 表示” 缺少值”，就是此处应该有一个值，但是还没有定义，转为数值时为 NaN。典型用法是：变量被声明了，但没有赋值时，就等于 undefined。调用函数时，应该提供的参数没有提供，该参数等于 undefined。对象没有赋值的属性，该属性的值为 undefined。函数没有返回值时，默认返回 undefined。
2.  null 表示” 没有对象”，即该处不应该有值，转为数值时为 0。典型用法是：作为函数的参数，表示该函数的参数不是对象。作为对象原型链的终点。
3.  undeclared：js 语法错误，没有申明直接使用，js 无法找到对应的上下文。

### 如何在 JavaScript 中每 x 秒调用一个函数？

```
	setInterval(function (){ alert("Hello"); }, 3000);
```

### JS 中 == 和 === 区别是什么？

1.  对于 string,number 等基础类型，== 和 === 有区别：不同类型间比较，== 之比较 “转化成同一类型后的值” 看 “值” 是否相等，=== 如 果类型不同，其结果就是不等。同类型比较，直接进行 “值” 比较，两者结果一样。
2.  对于 Array,Object 等高级类型，== 和 === 没有区别，进行 “指针地址” 比较。

### JavaScript 内置可用类型

string，number，boolean，null 和 undefined，object，symbol（ES6 新语法）

### jQuery 库中的 $() 是什么？

$() 函数是 jQuery () 函数的别称。$() 函数用于将任何对象包裹成 jQuery 对象，接着你就被允许调用定义在 jQuery 对象上的多个不同方法。你可以将一个选择器字符串传入 $() 函数，它会返回一个包含所有匹配的 DOM 元素数组的 jQuery 对象。

### jQuery 有几种选择器？

1.  基本选择器：`#id`，`class`,`element`，`*`;
2.  层次选择器：`parent > child`，`prev + next` ，`prev ~ siblings`
3.  基本过滤器选择器：`:first`，`:last` ，`:not` ，`:even`
4.  表单选择器： `:input` ，`:text` ，`:password` ，`:radio` ，`:checkbox` ，`:submit` 等；
5.  表单过滤器选择器：`:enabled` ，`:disabled` ，`:checked` ，`:selected`

### jQuery 中 $.get () 提交和 $.post () 提交有区别吗？

相同点：都是异步请求的方式来获取服务端的数据；

异同点：

*   请求方式不同：$.get () 方法使用 GET 方法来进行异步请求的。$.post () 方法使用 POST 方法来进行异步请求的。
*   参数传递方式不同：get 请求会将参数跟在 URL 后进行传递，而 POST 请求则是作为 HTTP 消息的实体内容发送给 Web 服务器的，这种传递是对用户不可见的。
*   数据传输大小不同：get 方式传输的数据大小不能超过 2KB 而 POST 要大的多
*   安全问题： GET 方式请求的数据会被浏览器缓存起来，因此有安全问题。

### window.onload () 函数和 jQuery 中的 document.ready () 有什么区别？

1.  执行时间：window.onload 必须等到页面内包括图片的所有元素加载完毕后才能执行。$(document).ready () 是 DOM 结构绘制完毕后就执行，不必等到加载完毕。$(document).ready () 在 window.onload 之前执行。
2.  简化写法：window.onload 没有简化写法。$(document).ready (function (){}) 可以简写成 $(function (){});
3.  出现地方不同：window.onload 是 js 标准，可出现在任何 js 脚本中。$(document).ready 只有在 jq 库中出现。

### 什么是 CDN？哪些是流行的 jQuery CDN？使用 CDN 有什么好处？

内容传送网络或内容分发网络（CDN）是部署在因特网上的多个数据中心的大型分布式服务器系统。CDN 的目标是为具有高可用性和高性能的最终用户提供内容。

有 3 个流行的 jQuery CDN：谷歌，微软 jQuery。

使用 CDN 的优势：它减少了服务器的负载。它节省了带宽。jQuery 框架将从这些 CDN 加载更快。最重要的好处是，如果用户访  
问过使用任何这些 CDN 的 jQuery 框架的任何站点，它将被缓存

### 如何从 CDN 加载 jQuery？

下面是从 3 个 CDN 加载 jQuery 的代码。

*   从 Google CDN 加载 jQuery Framework 的代码

```
	 <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
```

*   从 Microsoft CDN 加载 jQuery Framework 的代码

```
	 <script type="text/javascript" src="http://ajax.microsoft.com/ajax/jquery/jquery-1.9.1.min.js"> </script>
```

*   从 jQuery 站点加载 jQuery Framework 的代码（EdgeCast CDN）

```
	 <script type="text/javascript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
```

JSP 技术
------

### 说一说 Servlet 的生命周期？

1.  Servlet 有良好的生存期的定义，包括加载和实例化、初始化、处理请求以及服务结束。这个生存期由 javax.servlet.Servlet 接口的 init (),service () 和 destroy 方法表达。
2.  Servlet 被服务器实例化后，容器运行其 init 方法，请求到达时运行其 service 方法，service 方法自动派遣运行与请求对应的 do\*\*\*() 方法（doGet，doPost）等，当服务器决定将实例销毁的时候调用其 destroy 方法。
3.  web 容器加载 servlet，生命周期开始。通过调用 servlet 的 init () 方法进行 servlet 的初始化。通过调用 service () 方法实现，根据请求的不同调用不同的 do\*\*\*() 方法。结束服务，web 容器调用 servlet 的 destroy () 方法。

### jsp 和 servlet 的区别、共同点、各自应用的范围？

JSP 是 Servlet 技术的扩展，本质上就是 Servlet 的简易方式。JSP 编译后是 “类 servlet”。Servlet 和 JSP 最主要的不同点在于：Servlet 的应用逻辑是在 Java 文件中，并且完全从表示层中的 HTML 里分离开来。而 JSP 的情况是 Java 和 HTML 可以组合成一个扩展名为.jsp 的文件。JSP 侧重于视图，Servlet 主要用于控制逻辑。在 struts 框架中，JSP 位于 MVC 设计模式的视图层，而 Servlet 位于 控制层.

### Servlet API 中 forward () 与 redirect () 的区别？

*   从地址栏显示来说

forward 是服务器请求资源，服务器直接访问目标地址的 URL, 把那个 URL 的响应内容读取过来，然后把这些内容再发给浏览器。浏览器根本不知道服务器发送的内容从哪里来的，所以它的地址栏还是原来的地址. redirect 是服务端根据逻辑，发送一个状态码，告诉浏览器重新去请求那个地址。所以地址栏显示的是新的 URL. 所以 redirect 等于客 户端向服务器端发出两次 request，同时也接受两次 response。

*   从数据共享来说

forward: 转发页面和转发到的页面可以共享 request 里面的数据.redirect: 不能共享数据.redirect 不仅可以重定向到当前应用程序的其他资源，还可以重定向到同一个站点上的其他应用程序中的资源，甚至是使用绝对 URL 重定向到其他站点的资源.forward 方法 只能在同一个 Web 应用程序内的资源之间转发请求.forward 是服务器内部的一种操作.redirect 是服务器通知客户端，让客户端重新发起请求。所以，你可以说 redirect 是一种间接的请求，但是你不能说” 一个请求是属于 forward 还是 redirect “。

*   从运用地方来说

forward: 一般用于用户登陆的时候，根据角色转发到相应的模块. redirect: 一般用于用户注销登陆时返回主页面和跳转到其它的网站等。

*   从效率来说

forward: 高。

redirect: 低。