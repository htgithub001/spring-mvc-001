1、The first request will be received by DispatcherServlet.

2、DispatcherServlet will take the help of HandlerMapping and get to know the @Controller class name associated with the given request.

3、So request transfer to the @Controller, and then @Controller will process the request by executing appropriate methods and returns ModelAndView object (contains Model data and View name) back to the DispatcherServlet

4、Now DispatcherServlet send the model object to the ViewResolver to get the actual view page.

5、Finally, DispatcherServlet will pass the Model object to the View page to display the result.
