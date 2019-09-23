1) Client sends an HTTP request to a specific URL

2) DispatcherServlet of Spring MVC receives the request

2) It passes the request to a specific controller depending on the URL requested using @Controller and @RequestMapping annotations.

3) Spring MVC Controller then returns a logical view name and model to DispatcherServlet.

4) DispatcherServlet consults view resolvers until actual View is determined to render the output

5) DispatcherServlet contacts the chosen view (e.g. Thymeleaf, Freemarker, JSP) with model data and it renders the output depending on the model data

6) The rendered output is returned to the client as response

来源：https://learningsolo.com/spring-mvc-framework/



1、The first request will be received by DispatcherServlet.

2、DispatcherServlet will take the help of HandlerMapping and get to know the @Controller class name associated with the given request.

3、So request transfer to the @Controller, and then @Controller will process the request by executing appropriate methods and returns ModelAndView object (contains Model data and View name) back to the DispatcherServlet

4、Now DispatcherServlet send the model object to the ViewResolver to get the actual view page.

5、Finally, DispatcherServlet will pass the Model object to the View page to display the result.

来源：https://stackoverflow.com/questions/27918643/spring-mvc-request-and-response-flow-explanation
