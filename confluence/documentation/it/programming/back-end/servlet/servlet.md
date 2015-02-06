[[home]](../../../../home.html) 

> **Servlet**

[oficial site]()<br/>
[oficial documentation]()
 
- [HTTP status code definitions](#http_status_codes)
- [Definition](#definition)
- [Request redirect](#req_redirect)
- [Request forward](#req_forward)

<a name="http_status_codes"></a>
> **HTTP status code definitions:**

[Mode: Status Code Definitions](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.8)

- **Informational 1xx**
	1. 100 Continue
	2. 101 Switching Protocols
- **Successful 2xx**
	1. 200 OK 
	2. 201 Created 
	3. 202 Accepted
	4. 203 Non-Authoritative Information 
	5. 204 No Content
	6. 205 Reset Content
	7. 206 Partial Content
- **Redirection 3xx**
	1. 300 Multiple Choices
	2. 301 Moved Permanently
	3. 302 Found
	4. 303 See Other
	5. 304 Not Modified
	6.  305 Use Proxy
	7.  306 (Unused)
	8.  307 Temporary Redirect
- **Client Error 4xx**
	1. 400 Bad Request
	2. 401 Unauthorized
	3. 402 Payment Required
	4. 403 Forbidden
	5. 404 Not Found
	6. 405 Method Not Allowed
	7. 406 Not Acceptable
	8. 407 Proxy Authentication Required
	9. 408 Request Timeout
	10. 409 Conflict
	11. 410 Gone
	12. 411 Length Required
	13. 412 Precondition Failed
	14. 413 Request Entity Too Large
	15. 414 Request-URI Too Long
	16. 415 Unsupported Media Type
	17. 416 Requested Range Not Satisfiable
	18. 417 Expectation Failed
- **Server Error 5xx**
	1. 500 Internal Server Error
	2. 501 Not Implemented
	3. 502 Bad Gateway
	4. 503 Service Unavailable
	5. 504 Gateway Timeout
	6. 505 HTTP Version Not Supported
	

<a name="definition"></a>
> **Definition:** <br/>

**ServletContext**

When the servletcontainer (like Apache Tomcat) starts up, it will deploy and load all webapplications. When a webapplication get loaded, the servletcontainer will create the ServletContext once and keep in server's memory. The webapp's web.xml will be parsed and every Servlet, Filter and Listener found in web.xml or annotated with respectively @WebServlet, @WebFilter and @WebListener will be created once and kept in server's memory as well. When the servletcontainer shuts down, it will unload all webapplications and the ServletContext and all Servlet, Filter and Listener instances will be trashed.

**HttpServletRequest and HttpServletResponse**

The servletcontainer is attached to a webserver which listens on HTTP requests on a certain port number, which is usually 8080 in development and 80 in production. When a client (user with a webbrowser) sends a HTTP request, the servletcontainer will create new HttpServletRequest and HttpServletResponse objects and pass it through the methods of the already-created Filter and Servlet instances whose url-pattern matches the request URL, all in the same thread.

The request object provides access to all information of the HTTP request, such as the request headers and the request body. The response object provides facility to control and send the HTTP response the way you want, such as setting headers and the body (usually with HTML content from a JSP file). When the HTTP response is committed and finished, then both the request and response objects will be trashed.

**HttpSession**

When a client visits the webapp for the first time and/or the HttpSession is to be obtained for the first time by request.getSession(), then the servletcontainer will create it, generate a long and unique ID (which you can get by session.getId()) and store it in server's memory. The servletcontainer will also set a Cookie in the Set-Cookie header of the HTTP response with JSESSIONID as cookie name and the unique session ID as cookie value.

As per the HTTP cookie specification (a contract a decent webbrowser and webserver has to adhere), the client (the webbrowser) is required to send this cookie back in the subsequent requests in the Cookie header as long as the cookie is valid. Using browser builtin HTTP traffic monitor you can check them (press F12 in Chrome / Firefox23+ / IE9+ and check Net/Network tab). The servletcontainer will determine the Cookie header of every incoming HTTP request for the presence of the cookie with the name JSESSIONID and use its value (the session ID) to get the associated HttpSession from server's memory.

The HttpSession lives until it has not been used for more than the <session-timeout> time, a setting you can specify in web.xml, which defaults to 30 minutes. So when the client doesn't visit the webapp anymore for over 30 minutes, then the servletcontainer will trash the session. Every subsequent request, even though with the cookie specified, will not have access to the same session anymore. The servletcontainer will create a new one.

On the other hand, the session cookie on the client side has a default lifetime which is as long as the browser instance is running. So when the client closes the browser instance (all tabs/windows), then the session will be trashed at the client side. In a new browser instance the cookie associated with the session won't be sent anymore. A new request.getSession() would return a brand new HttpSession and set a cookie with a brand new session ID.

**In a nutshell**

The ServletContext lives as long as the webapp lives. It's been shared among all requests in all sessions.
The HttpSession lives as long as the client is interacting with the webapp with the same browser instance and the session hasn't timed out at the server side yet. It's been shared among all requests in the same session.
The HttpServletRequest and HttpServletResponse lives as long as the client has sent it until the complete response (the webpage) is arrived. It is not being shared elsewhere.
Any Servlet, Filter and Listener lives as long as the webapp lives. They are being shared among all requests in all sessions.
Any attribute which you set in ServletContext, HttpServletRequest and HttpSession will live as long as the object in question lives.
Threadsafety

That said, your major concern is possibly threadsafety. You should now have learnt that Servlets and filters are shared among all requests. That's the nice thing of Java, it's multithreaded and different threads (read: HTTP requests) can make use of the same instance. It would otherwise have been too expensive to recreate it on every request.

But you should also realize that you should never assign any request or session scoped data as an instance variable of a servlet or filter. It will be shared among all other requests in other sessions. That's threadunsafe! The below example illustrates that:

public class ExampleServlet extends HttpServlet {

    private Object thisIsNOTThreadSafe;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
    	    Object thisIsThreadSafe;

    	    thisIsNOTThreadSafe = request.getParameter("foo"); // BAD!! Shared among all requests!
    	    thisIsThreadSafe = request.getParameter("foo"); // OK, this is thread safe.
    	} 
	}
		
		
<a name="req_redirect"></a>
> **Request redirect:**

A redirect consists in sending a response to the browser saying ***"Please go to the following URL: RedirectIfSuccessful.jsp"***.
When it receives this response, the browser sends a new request to RedirectIfSuccessful.jsp, without any parameter. So getting the parameter name from RedirectIfSuccessful.jsp will return null.
If you want to have access to the name after the redirection, you need to send a redirect to *RedirectIfSuccessful.jsp?name=[the name the user entered]*
The HTTP spec states that all redirects must be in the form of a GET (or HEAD). You can consider encrypting your query string parameters if security is an issue. Generally, you cannot send a POST request using sendRedirect() method. 


<a name="req_forward"></a>
> **Request forward:**

	RequestDispatcher dispatcher = request.getRequestDispatcher(url);
	dispatcher.forward(request, response);