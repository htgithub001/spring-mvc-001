# difference-between-jsp-forward-and-redirect

redirect sets the response status to 302 [1], and the new url in a Location header, and sends the response to the browser. Then the browser, according to the http specification, makes another request to the new url

forward happens entirely on the server. The servlet container just forwards the same request to the target url, without the browser knowing about that. Hence you can use the same request attributes and the same request parameters when handling the new url. And the browser won't know the url has changed (because it has happened entirely on the server)

来源:https://stackoverflow.com/questions/6068891/difference-between-jsp-forward-and-redirect

## 关于使用哪个?
forward的操作对于客户端是透明的, 为什么要透明? 假设有这样一种场景, 那就是旧页面P0已经转移到旧页面了P1, 客户端显然不必知道这次转移, 
所以对于这样的场景, 应该使用forward. 

对于redirect, 如果服务器B收到一个请求, 发现用户还没有登录, 而且管理用户登录模块的服务器是A,不是B, 这样的场景, B就会将请求redirect给A服务完成登录, 
而A那边登录成功会redirect到B, 这样B就能处理已经登录的用户的请求了.
