# 字符集


```
    <filter>
        <filter-name>encodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
            <param-name>forceEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>encodingFilter</filter-name>
        <url-pattern>*.do</url-pattern>
        <url-pattern>*.jsp</url-pattern>
        <url-pattern>/api/content</url-pattern>
        <url-pattern>/servlet/userSelect</url-pattern>
    </filter-mapping>
```
设置说明
CharacterEncodingFilter类具有encoding和forceEncoding两个属性，其中encoding是表示设置request的编码，forceEncoding表示是否同时设置response的编码。
```
    @Override
    protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain filterChain)throws ServletException, IOException {

        if (this.encoding != null && (this.forceEncoding || request.getCharacterEncoding() == null)) {
            request.setCharacterEncoding(this.encoding);
            if (this.forceEncoding) {
                response.setCharacterEncoding(this.encoding);
            }
        }
        filterChain.doFilter(request, response);
    }
```
通过源码也能看见，encodin用于设置request的编码，而forceEncoding为ture时设置response的编码。

来源：https://www.jianshu.com/p/c86db27642af
