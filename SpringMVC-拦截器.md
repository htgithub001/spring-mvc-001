 # SpringMVC的拦截器的使用
 
 <!-- 配置拦截器 	-->
	<mvc:interceptors>
    	<mvc:interceptor>
        	<mvc:mapping path="/**" />
        	<bean class="com.itheima.core.interceptor.LoginInterceptor" />
    	</mvc:interceptor>
	</mvc:interceptors>

【注意】这代码属于SpringMVC里面的代码，主要是验证用户是否已经登录成功。
