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
