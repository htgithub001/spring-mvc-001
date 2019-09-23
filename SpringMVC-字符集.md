# 字符集

## 在Spring MVC之外
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
通过源码也能看见，encoding用于设置request的编码，而forceEncoding为ture时设置response的编码。

来源：https://www.jianshu.com/p/c86db27642af


## Spring MVC之内
我会划分一些界限，比如进入Spring MVC后必须都是Unicode编码，出去Sping MVC后会全是utf8，比如数据都是以utf8的格式进入mysql和redis，但是取回这些utf8编码的数据到Spring MVC后，就是全部是Unicode格式了。

至于jsp等页面，我会在页面上写明了是utf8格式，并在filter将它转化成utf8格式。
