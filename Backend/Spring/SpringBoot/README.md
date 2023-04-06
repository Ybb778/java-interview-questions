Spring Boot 框架
==============

## 什么是 Spring Boot？

多年来，随着新功能的增加，Spring 变得越来越复杂。只需访问 https://spring.io/projects 页面，我们就会看到可以在我们的应用程序中使用的所有 Spring 项目的不同功能。如果必须启动一个新的 Spring 项目，我们必须添加构建路径或添加 Maven 依赖关系，配置应用程序服务器，添加 Spring 配置。因此，开始一个新的 Spring 项目需要很多努力，因为我们现在必须从头开始做所有事情。Spring Boot 是解决这个问题的方法。Spring Boot 已经建立在现有 Spring 框架之上。使用 Spring 启动，我们避免了之前我们必须做的所有样板代码和配置。因此，Spring Boot 可以帮助我们以最少的工作量，更加健壮地使用现有的 Spring 功能。

## Spring Boot 有哪些特点？

1.  为 Spring 开发提供一个更快、更广泛的入门体验。
2.  开箱即用，远离繁琐的配置。
3.  提供了一系列大型项目通用的非业务性功能，例如：内嵌服务器、安全管理、运行数据监控、运行状况检查和外部化配置等。
4.  绝对没有代码生成，也不需要 XML 配置。

## Spring Boot 有哪些优点？

1.  减少开发、测试时间和努力。
2.  使用 JavaConfig 有助于避免使用 XML。
3.  避免大量的 Maven 导入和各种版本冲突。
4.  通过提供默认值快速开始开发。没有单独的 Web 服务器需要。这意味着你不再需要启动 Tomcat，Glassfish 或其他任何东西。
5.  需要更少的配置 因为没有 web.xml 文件。只需添加用 `@ Configuration` 注释的类，然后添加用 `@Bean` 注释的方法，Spring 将自动加载对象并像以前一样对其进行管理。您甚至可以将 `@Autowired` 添加到 bean 方法中，以使 Spring 自动装入需要的依赖关系中。基于环境的配置 使用这些属性，您可以将您正在使用的环境传递到应用程序：-Dspring.profiles.active ={enviornment}。在加载主应用程序属性文件后，Spring 将在（application {environment} .properties）中加载后续的应用程序属性文件。

## Spring Boot、Spring MVC 和 Spring 有什么区别？

1.  Spring 最重要的特征是依赖注入。所有 SpringModules 不是依赖注入就是 IOC 控制反转。当我们恰当的使用 DI 或者是 IOC 的时候，我们可以开发松耦合应用。松耦合应用的单元测试可以很容易的进行。
2.  Spring MVC 提供了一种分离式的方法来开发 Web 应用。通过运用像 DispatcherServelet ， MoudlAndView 和 ViewResolver 等一些简单的概念，开发 Web 应用将会变得非常简单。
3.  Spring 和 SpringMVC 的问题在于需要配置大量的参数。Spring Boot 通过一个自动配置和启动的项来目解决这个问题。为了更快的构建产品就绪应用程序，Spring Boot 提供了一些非功能性特征。

## Spring Boot 的核心注解是哪个？它主要由哪几个注解组成的？

启动类上面的注解是 @SpringBootApplication，它也是 Spring Boot 的核心注解，主要组合包含了以下 4 个注解：

1.  @SpringBootConfiguration： 组 合 了 @Configuration 注 解 ， 实 现 配 置 文 件 的 功 能 。
2.  @EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：
3.  @SpringBootApplication(exclude = { DataSourceAutoConfiguration.class })。
4.  @ComponentScan：Spring 组件扫描。

## Spring Boot 需要独立的容器运行吗？

可以不需要，内置了 Tomcat/Jetty 等容器。

## 你如何理解 Spring Boot 中的 Starters？

Starters 可以理解为启动器，它包含了一系列可以集成到应用里面的依赖包，你可以一站式集成 Spring 及其他技术，而不需要到处找示例代码和依赖包。如你想使用 Spring JPA 访问数据库，只要加入 spring-boot-starter-data-jpa 启动器依赖就能使用了。

Spring Boot 是否可以使用 XML 配置？

Spring Boot 推荐使用 Java 配置而非 XML 配置，但是 Spring Boot 中也可以使用 XML 配置，通过 `@ImportResource` 注解可以引入一个 XML 配置。

## bootstrap.properties 和 application.properties 有何区别？

1.  单纯做 Spring Boot 开发，可能不太容易遇到 bootstrap.properties 配置文件，但是在结合 Spring Cloud 时，这个配置就会经常遇到了，特别是在需要加载一些远程配置文件的时侯。bootstrap.properties 在 application.properties 之前加载，配置在应用程序上下文的引导阶段生效。
2.  一般来说我们在 Spring Cloud Config 或者 Nacos 中会用到它。bootstrap.properties 被 Spring ApplicationContext 的父类加载，这个类先于加载 application.properties 的 ApplicatonContext 启动。当然，前面叙述中的 properties 也可以修改为 yaml 。

## 自动装配的原理

@EnableAutoConfiguration 的实现关键在于引入了 AutoConfigurationImportSelector，该类的核心逻辑是 selectImports 方法。在该方法中，首先会从 spring-boot-autoconfigure 包下的 META-INF/spring.factories 文件中加载所有可能用到的自动配置类；然后进行去重操作，并排除 exclude 和 excludeName 属性携带的类；最后进行过滤操作，只将满足条件（@Conditional）的自动配置类返回。这样，通过使用 @EnableAutoConfiguration 注解，就可以实现自动配置的功能。

## 如何重新加载 Spring Boot 上的更改，而无需重新启动服务器？

这可以使用 DEV 工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式 tomcat 将重新启动。Spring Boot 有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java 开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。开发人员可以重新加载 Spring Boot 上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。Spring Boot 在发布它的第一个版本时没有这个功能。这是开发人员最需要的功能。DevTools 模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供 H2 数据库控制台以更好地测试应用程序。

```xml
	<dependency>
	    <groupId>prg.springframework.boot</groupId>
	    <artifactId>spring-boot-devtools</artifactId>
	    <optional>true</opential>
	</dependency>
```

## 如何在自定义端口上运行 Spring Boot 应用程序？

为了在自定义端口上运行 Spring Boot 应用程序，您可以在 application.properties 中指定端口。