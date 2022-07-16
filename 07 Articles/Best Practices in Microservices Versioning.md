---
link: https://www.codeguru.com/dotnet/best-practices-versioning-microservices/
author: {{author}}
published: {{published}}
tags: [{{tags:,}}]
---
# Highlights
{{highlights}}

---
# Best Practices in Microservices Versioning
This article discusses what versioning is all about, why versioning in microservices is essential, the types of versioning strategies in microservices-based applications, and the best practices.

## What is Versioning and Why is it Important?

Versioning is a strategy that enables you to maintain multiple services having the same functionality. Unlike traditional applications, versioning in microservices-based applications is not straight-forward.

Versioning is an important part of API design, and it provides the developers the ability to improve the APIs without breaking the existing functionalities of the other versions of the API. As applications grow and evolve over time, businesses often need new functionalities to be available so that the customers can consume such services.

Microservices architecture preaches teams should design, build, test, and deploy the services independent of one another. As a result, versioning can be a challenge since service compatibility might be lost. You should design your microservices in such a way that you can revert to a previous version if needed.

## Microservices Versioning

Assume that you have a service that is up and running in the production environment and there are multiple consumers of it as well. Now suppose you need to add more functionality to the service to suffice customer’s requirements.

Since there are several users of the old service, you might want to keep the existing functionality intact. So, you might have some users who need the old service while there are other users who will need a version with new or extended features. Here’s exactly where API versioning comes to the rescue.

**Read: [Transitioning to Microservices – Are You Ready?](https://www.developer.com/design/transition-to-microservices/)**

## Microservices Versioning Strategies

Microservices should evolve over time – they should be able to exhibit multiple behaviors to cater to the demands of different customers. This is exactly where microservices versioning comes in.

Two of the most common ways of versioning APIs for microservices-based applications are:

-   Versioning in the URI
-   Versioning in the Header

Versioning of microservices is a bit tricky. While teams design, develop and deploy microservices that are independent of one another, it poses a problem in versioning. While you should design a microservice-based application to provide support for multiple versions of the service, this needs extra routing logic to help the application support multiple versions of the same microservice at runtime.

**Read: [Versioning REST APIs.](https://www.developer.com/java/version-rest-api/)**

### URI Versioning

In this approach, the version information is available as part of the service URL. This allows you to identify which version of the service is being used. You should redirect service requests that don’t have a version specified in the URL to the default version of the service. An example of how version information is used in the URI can be seen below:

```
http://myecommerceapp/v1.1.2/v1/GetAllProducts
http://myecommerceapp/v2.0.0/GetProducts 

```

URI revisioning is typically used to update a service’s public API. It does not make any significant changes to its backend data store. The downside to using URI versioning is that dealing with a very large URI footprint can become unmanageable over time.

The following code snippet shows how you can implement a controller with versioning enabled.

```
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;
namespace SaveRequestResponseHeader.Controllers
{
    [ApiController] 
    [ApiVersion("1.0")] 
    [Route("api/{version:apiVersion}/product")] 
    public class ProductV1Controller : ControllerBase 
    {
        [HttpGet] 
        public IActionResult Get() 
        { 
            return new OkObjectResult("Inside Product v1 Controller"); 
        } 
    }
}

```

### Header Versioning

In this approach, the version information is passed using the request header. One of the several header attributes in HTTP protocol is content version. Header-driven versioning uses this attribute to specify a service.

The main benefit of header versioning is that the name and location of your resource remain unchanged. This makes sure that the URI is not cluttered with versioning information and the API remains semantically meaningful to the developers.

This approach has one drawback: information cannot be easily encoded in hypermedia links. Here’s how you can configure header-based versioning in ASP.NET Core.

```
        public void ConfigureServices(IServiceCollection services)
        {
                services.AddControllers();
                services.AddApiVersioning(config => {
                config.DefaultApiVersion = new ApiVersion(1, 0); 
                config.AssumeDefaultVersionWhenUnspecified = true; 
                config.ReportApiVersions = true; 
                config.ApiVersionReader = 
                new HeaderApiVersionReader("x-api-version");
            });
        }

```

## Semantic Versioning

Semantic versioning is another versioning strategy in which each release is represented using three non-negative integers namely, _Major_, _Minor_, and _Patch_. The format used to specify version information using semantic versioning is given below: MAJOR.MINOR.PATCH Here’s what each of these means:

**Major** – The major version indicates breaking changes to the API. If the API is incompatible with the new version due to major changes in the version, you can increase this version.  
**Minor** – The minor version is increased when you have a compatible version of the software, but the business logic has changed.  
**Patch** – You should increase this value if the older version is compatible with the new version, but a bug was fixed in the updated version.

Both minor and patch versions are generally used for backward-compatible updates. In semantic versioning version numbers are assigned based on the severity of the change.

As an example, _v1.0.1_ is a small change and it will have just a few patches but _v1.1.0_ is a minor change. If your service has a major change, you can have the version number as _v2.0.0_.

Here’s how you can use semantic versioning to invoke an API.

```
http://api.product.com/v1.2.3/GetProducts 

```

If you’re working on a project that has several modules having interdependency between them, semantic versioning is a good choice.

### Calendar Versioning

Calendar versioning is a type of semantic versioning that takes advantage of calendar dates in lieu of non-negative integers. It doesn’t fix a particular format – rather, it uses a combination of year, month, and day and allows you to choose from various combinations of year, month, and day.

Calendar versioning is a good choice for applications that are time-bound. Unlike Semantic versioning, the format used to specify Calendar versioning is as follows:

```
MAJOR.MINOR.MICRO 

```

Note that _MICRO_ is referred to as _PATCH_ in Semantic versioning.

**Read: [Understanding Android Versioning.](https://www.developer.com/mobile/android/understanding-android-versioning/)**

## Best Practices in Versioning Microservices

Microservices Service Names Should Not Contain Version Information – You should never use version information in the service name or the API name. As an example, the following names should never be used: _Customer\_1\_2\_1_ or _Product\_1\_1\_2_.

If you have version information in the name of your API and the microservices must call them, maintaining such services would be a daunting task for you each time the service changes.

-   **Proper Documentation** – You should ensure that service versioning and documentation work for hand in hand – service documentation must be made mandatory for each version of the service.
-   **Create a Delivery Pipeline** – You should create a delivery pipeline that would ensure that version mismatches are identified and resolved earlier in the process.
-   Ensure that the service URL and Version number is configurable – It is a good practice to ensure that the URL of the service as well as version number are configurable and not hardcoded.

## Versioning Software and Microservices

It is quite unlikely that you would be able to make backward-compatible changes in your application to satisfy the needs of both old and new customers. Rather, you should build and expose a new version of your API while at the same time continuing to provide support for the older versions of the API. Although maintaining too many versions of your API might be a nightmare for you in the long run, you can deprecate older versions of your API and/or rerouting the traffic to the newer versions of the API.