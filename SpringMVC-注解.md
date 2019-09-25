# SpringMVC注解

SpringMVC有很多需要配置的地方,比方说用注解来配置拦截器.

在SpringMVC的上下文中加入&lt;mvc:annotation-driven/&gt;后, 这样配置处理器映射器和适配器, 让controller-注解的对象能够开始工作.

读下面的帖子:

@EnableWebMvc is equivalent to &lt;mvc:annotation-driven /&gt; in XML. 
It enables support for @Controller-annotated classes that use @RequestMapping to map incoming requests to a certain method. 
You can read detailed information about what it configures by default and how to customise the configuration in the reference documentation.

我的理解是@EnableWebMvc可以注解多个类, 这些类负责的SpringMVC配置不相同,有的类负责View有关的配置, 有类负责有关Interceptor的配置.
