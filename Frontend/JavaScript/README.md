JavaScript 语言和 jQuery 技术
========================

## JavaScript 中如何将页面重定向到另一个页面？

1.  使用 `location.href`：
```javascript
window.location.href ="https://www.baidu.com/"
```
2.  使用 `location.replace`：
```javascript
window.location.replace ("https://www.baidu.com/")
```

## Undefined，Null 和 Undeclared 有什么区别？

1.  `Undefined` 表示” 缺少值”，就是此处应该有一个值，但是还没有定义，转为数值时为 `NaN`。典型用法是：变量被声明了，但没有赋值时，就等于 `Undefined`。调用函数时，应该提供的参数没有提供，该参数等于 `Undefined`。对象没有赋值的属性，该属性的值为 `Undefined`。函数没有返回值时，默认返回 `Undefined`。
2.  `Null` 表示” 没有对象”，即该处不应该有值，转为数值时为 0。典型用法是：作为函数的参数，表示该函数的参数不是对象。作为对象原型链的终点。
3.  `Undeclared`：js 语法错误，没有申明直接使用，js 无法找到对应的上下文。

## 如何在 JavaScript 中每 x 秒调用一个函数？

```javascript
setInterval(function (){ alert("Hello"); }, 3000); // 每隔 3000 毫秒（即 3 秒），执行一次匿名函数 `function (){ alert("Hello");
```

## JavaScript 中 == 和 === 区别是什么？

1.  对于 `String`,`Number` 等基础类型，`==` 和 `===`有区别：不同类型间比较，`==` 之比较 “转化成同一类型后的值” 看 “值” 是否相等，`===` 如果类型不同，其结果就是不等。同类型比较，直接进行 “值” 比较，两者结果一样。
    - "==" 运算符：它执行的是弱类型比较，即在比较之前会进行类型转换。如果比较的两个值的类型不同，它会尝试将它们转换为相同的类型，然后再进行比较。例如：
    ```javascript
    console.log(1 == "1"); // 输出 true，因为 "1" 会被转换为数字 1
    console.log(true == 1); // 输出 true，因为 true 会被转换为数字 1
    console.log(null == undefined); // 输出 true，因为它们被认为是相等的特殊值
    ```
    - "===" 运算符：它执行的是严格类型比较，不会进行类型转换。只有在比较的两个值的类型和值都相等时，才会返回 true。例如：
    ```javascript
    console.log(1 === "1"); // 输出 false，因为它们的类型不同
    console.log(true === 1); // 输出 false，因为它们的类型不同
    console.log(null === undefined); // 输出 false，因为它们的类型不同
    ```
2.  对于 `Array`,`Object` 等高级类型，`==` 和 `===` 没有区别，进行 “指针地址” 比较。

## JavaScript 内置可用类型

`String`、`Number`、`Boolean`、`Null` 和 `Undefined`、`Object`、`Symbol`（ES6 新语法）

## jQuery 库中的 $() 是什么？

`$()` 函数是 `jQuery ()` 函数的别称。`$()` 函数用于将任何对象包裹成 jQuery 对象，接着你就被允许调用定义在 jQuery 对象上的多个不同方法。你可以将一个选择器字符串传入 `$()` 函数，它会返回一个包含所有匹配的 DOM 元素数组的 jQuery 对象。

## jQuery 有几种选择器？

1.  基本选择器：`#id`，`class`,`element`，`*`;
2.  层次选择器：`parent > child`，`prev + next` ，`prev ~ siblings`
3.  基本过滤器选择器：`:first`，`:last` ，`:not` ，`:even`
4.  表单选择器： `:input` ，`:text` ，`:password` ，`:radio` ，`:checkbox` ，`:submit` 等；
5.  表单过滤器选择器：`:enabled` ，`:disabled` ，`:checked` ，`:selected`

## jQuery 中 $.get () 提交和 $.post () 提交有区别吗？

相同点：都是异步请求的方式来获取服务端的数据；

异同点：

*   请求方式不同：`$.get ()` 方法使用 `GET` 方法来进行异步请求的。`$.post ()` 方法使用 `POST` 方法来进行异步请求的。
*   参数传递方式不同：`GET` 请求会将参数跟在 URL 后进行传递，而 `POST` 请求则是作为 `HTTP` 消息的实体内容发送给 `Web` 服务器的，这种传递是对用户不可见的。
*   数据传输大小不同：`GET` 方式传输的数据大小不能超过 2KB 而 `POST` 要大的多
*   安全问题： `GET` 方式请求的数据会被浏览器缓存起来，因此有安全问题。

## window.onload () 函数和 jQuery 中的 document.ready () 有什么区别？

1.  执行时间：`window.onload` 必须等到页面内包括图片的所有元素加载完毕后才能执行。`$(document).ready()` 是 DOM 结构绘制完毕后就执行，不必等到加载完毕。`$(document).ready ()` 在 `window.onload` 之前执行。
2.  简化写法：`window.onload` 没有简化写法。`$(document).ready (function(){})` 可以简写成 `$(function(){})`;
3.  出现地方不同：`window.onload` 是 js 标准，可出现在任何 js 脚本中。`$(document).ready()` 只有在 jq 库中出现。

## 什么是 CDN？哪些是流行的 jQuery CDN？使用 CDN 有什么好处？

内容传送网络或内容分发网络（CDN）是部署在因特网上的多个数据中心的大型分布式服务器系统。CDN 的目标是为具有高可用性和高性能的最终用户提供内容。

有 3 个流行的 jQuery CDN：谷歌，微软 jQuery。

使用 CDN 的优势：它减少了服务器的负载。它节省了带宽。jQuery 框架将从这些 CDN 加载更快。最重要的好处是，如果用户访  
问过使用任何这些 CDN 的 jQuery 框架的任何站点，它将被缓存

## 如何从 CDN 加载 jQuery？

下面是从 3 个 CDN 加载 jQuery 的代码。

*   从 `Google CDN` 加载 jQuery Framework 的代码

```javascript
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
```

*   从 `Microsoft CDN` 加载 jQuery Framework 的代码

```javascript
<script type="text/javascript" src="http://ajax.microsoft.com/ajax/jquery/jquery-1.9.1.min.js"> </script>
```

*   从 `jQuery` 站点加载 jQuery Framework 的代码（EdgeCast CDN）

```javascript
<script type="text/javascript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
```
