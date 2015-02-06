[[home]](../../../../home.html) 

> **Spring framework**

[oficial site]()<br/>
[oficial documentation]()
 

- [MVC Concept](#mvc_concept)


<a name="mvc_concept"></a>
> **MVC Concept:** [(more)](http://www.tutorialspoint.com/spring/spring_web_mvc_framework.htm) <br/>

- The Model encapsulates the application data and in general they will consist of POJO.
- The View is responsible for rendering the model data and in general it generates HTML output that the client's browser can interpret.
- The Controller is responsible for processing user requests and building appropriate model and passes it to the view for rendering.

***The request processing workflow of the Spring Web MVC DispatcherServlet is illustrated in the following diagram:***

<img src="Screenshot_1.png"/>

*Following is the sequence of events corresponding to an incoming HTTP request to DispatcherServlet:*

1. After receiving an HTTP request, DispatcherServlet consults the HandlerMapping to call the appropriate Controller.
2. The Controller takes the request and calls the appropriate service methods based on used GET or POST method. The service method will set model data based on defined business logic and returns view name to the DispatcherServlet.
3. The DispatcherServlet will take help from ViewResolver to pickup the defined view for the request.
4. Once view is finalized, The DispatcherServlet passes the model data to the view which is finally rendered on the browser.