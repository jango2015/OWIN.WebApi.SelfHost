#Owin Custom SelfHost for WebApi

1. Create Console App
2. Install-Package Microsoft.AspNet.WebApi.OwinSelfHost
	This will load OWIN components and ASP.NET WebApi components and JSON.NET
3. Add New Item... OWIN Startup class
```
// Configure Web API for self-host. 
HttpConfiguration config = new HttpConfiguration();
config.Routes.MapHttpRoute(
    name: "DefaultApi",
    routeTemplate: "api/{controller}/{id}",
    defaults: new { id = RouteParameter.Optional }
);

app.UseWebApi(config); 

```
4. Add New Item... Class - ValuesController
5. Inherit from ApiController
6. Start Host in main()
```
string baseAddress = "http://localhost:9000/";

// Start OWIN host 
WebApp.Start<Startup>(url: baseAddress);

Console.ReadLine(); 
```