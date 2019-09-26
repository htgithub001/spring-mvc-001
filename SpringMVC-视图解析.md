# 视图解释器

以下的ViewResolver是被在springmvc-config.xml声明的.

```
<!-- 配置视图解释器ViewResolver -->
    <bean id="jspViewResolver" class=
    "org.springframework.web.servlet.view.InternalResourceViewResolver">
		<property name="prefix" value="/WEB-INF/jsp/" />
		<property name="suffix" value=".jsp" />
    </bean>	
    
```
我试了一下, 直接将它放在applicationContext里也是可以, 只不过放在spring-config.xml可能是防止其他的MVC模块也用了这个视图解析器.
