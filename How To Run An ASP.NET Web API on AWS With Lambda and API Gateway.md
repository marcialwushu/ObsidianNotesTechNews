---
link: https://www.howtogeek.com/devops/how-to-run-an-asp-net-web-api-on-aws-with-lambda-and-api-gateway/
author: {{author}}
published: {{published}}
tags: [{{tags:,}}]
date: July 17, 2022 (Sun)
---

---
# How To Run An ASP.NET Web API on AWS With Lambda and API Gateway
![lambda logo](https://www.howtogeek.com/wp-content/uploads/csit/2019/06/58095fd3.png?width=1198&trim=1,1&bg-color=000&pad=1,1)

AWS Lambda is a serverless platform for running code without managing the underlying hardware. It’s very flexible, and can run many different workloads, including full C# APIs using ASP.NET Core.

How to Speed Up a Slow PC


## Wait, You Can Do This On Lambda?

Yep! Not only can you run functions based on .NET runtimes, you can respond to requests using all the tools provided to you from ASP.NET. You can create APIs that talk to databases, like AWS’s managed RDS database, all while being perfectly scalable running on serverless functions.

While previous versions of ASP.NET run on .NET Framework (the older, Windows-only runtime) have been known to be bulky, the new ASP.NET Core stack running on .NET Core 3.1 and the newer .NET 5 have made significant performance and memory usage improvements.

This wouldn’t normally be possible, as ASP.NET uses its own HTTP web server called Kestrel to respond to requests, which wouldn’t work as that is handled by the Lambda runtime. However, AWS has provided an ingenious fix for this; traditionally, an ASP.NET setup usually involves their Kestrel web server behind IIS or NGINX. This talks to the ASP.NET framework to handle requests.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/06d33702.png?trim=1,1&bg-color=000&pad=1,1)

AWS has created a proxy class, `Amazon.Lambda.AspNetCoreServer`, which takes care of everything in front of ASP.NET. This lets you reuse most of your code while bridging your API to Lambda.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/2a11f4e8.png?trim=1,1&bg-color=000&pad=1,1)

This means you will need to use API Gateway, but that’s not a bad thing as API Gateway is very useful for managing your API. It allows you to strictly define all the rules that make your API function; of course, you will need to have your ASP.NET app configured to handle all requests from API Gateway.

However, this isn’t going to be the greatest experience in terms of startup time. Compared to lightweight scripting languages like JavaScript and Python, .NET packages have much more overhead.  There are [some tricks you can do](https://medium.com/slalom-build/solving-cold-starts-on-aws-lambda-when-using-dotnet-core-51f244f08f60) to speed up performance, and you can even [pay for it with provisioned capacity](https://aws.amazon.com/blogs/compute/new-for-aws-lambda-predictable-start-up-times-with-provisioned-concurrency/?tag=hotoge-20). Otherwise, you should be prepared for cold startup times around 1-2 seconds.

This doesn’t mean every execution is going to take 2 seconds to load the page. Once the first load happens, everything is initialized, and it’s kept “hot” in Lambda for 5 minutes. If someone else requests it, the function will handle the request like it normally would running on an actual server.

## Setting Up ASP.NET

AWS includes a generator for ASP.NET Lambda projects that is pre-configured with the boilerplate code and deployment to CloudFormation. We recommend that you start here, test things out, and then move your API code over, but if you’d like to jam it into an existing project, [AWS has a guide for that as well](https://aws.amazon.com/blogs/developer/net-core-3-0-on-lambda-with-aws-lambdas-custom-runtime/?tag=hotoge-20).

You’ll need the AWS Toolkit for Visual Studio extension installed, which you can manage from “Extensions” in the menu bar. This is what contains the project templates for AWS applications.

![](https://www.howtogeek.com/pagespeed_static/1.JiBnMqyl6S.gif)

From the main Visual Studio splash screen, create a new project:

![](https://www.howtogeek.com/pagespeed_static/1.JiBnMqyl6S.gif)

You’ll probably want to put this in its own solution, so select “Blank Solution” under “Other.”

![](https://www.howtogeek.com/pagespeed_static/1.JiBnMqyl6S.gif)

Then, you can right click in the file pane to add a new project, and select “AWS Serverless Application,” or “AWS Serverless Application with Tests,” whichever you prefer.

Make sure this is in C#, unless you want to use F# for some reason.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/901dcb3e.png?trim=1,1&bg-color=000&pad=1,1)

Also keep in mind that this is a “Serverless Application” project, which manages all the resources through AWS’s infrastructure-as-code service, CloudFormation. If you just wanted to make some Lambda functions, there’s a project for that too.

You’ll be taken to a sub-menu where you can choose what type of blueprint you want to build. Select “ASP.NET Core Web API” and create the project.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/cc1fdb6b.png?trim=1,1&bg-color=000&pad=1,1)

For the most part, this is configured like a standard ASP.NET project. The main difference is that the traditional `Program.cs` is replaced by `LambdaEntryPoint.cs` as the main entrypoint, and it contains the shim class that bridge’s AWS’s code to ASP.NET’s `IWebHostBuilder`, which is used to start the application.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/a09bcf20.png?trim=1,1&bg-color=000&pad=1,1)

Once it’s all up and running, you will need to copy over your controllers, models, and services, and replace `Startup.cs` with your configuration.

## Using Your API

To deploy this project, AWS includes built in publish options using the AWS Toolkit Extension. Right click your project and select “Publish to AWS Lambda…”

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/6b4fd909.png?trim=1,1&bg-color=000&pad=1,1)

You’ll need to give it a bucket to upload to, and set a name for the CloudFormation deployment.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/e21e02be.png?trim=1,1&bg-color=000&pad=1,1)

It will take a second to upload and publish, but you’ll then be able to go to the [AWS Lambda Management Console](https://console.aws.amazon.com/lambda/home?tag=hotoge-20) to view your function. It will have an auto-generated name using the CloudFormation stack name as the prefix.

Under Configuration > Triggers, you can view all the API Gateway triggers that call this function, and test it out for yourself using the endpoint.

![](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/fe6d014c.png?trim=1,1&bg-color=000&pad=1,1)

You can also view the full CloudFormation stack that is created automatically using your configuration.

![](https://www.howtogeek.com/pagespeed_static/1.JiBnMqyl6S.gif)

If you want to change it, you’ll need to edit the `serverless.template` in your project. For more info, you can refer to [our guide on using AWS CloudFormation](https://www.howtogeek.com/devops/codify-your-aws-infrastructure-with-cloudformation/).

**RELATED:** [**_Codify Your AWS Infrastructure With CloudFormation_**](https://www.howtogeek.com/devops/codify-your-aws-infrastructure-with-cloudformation/)

READ NEXT

-   › [How Much Is Your Computer Heating Your Home?](https://www.howtogeek.com/815116/how-much-heat-does-your-computer-add-to-your-home/)
-   › [NASA’s New Space Photos Are the Perfect Desktop Wallpapers](https://www.howtogeek.com/817813/nasas-new-space-photos-are-the-perfect-desktop-wallpapers/)
-   › [How Much Does It Cost to Charge an Electric Car?](https://www.howtogeek.com/814849/how-much-does-it-cost-to-charge-an-electric-car/)
-   › [7 Little-Known Gmail Features You Should Try](https://www.howtogeek.com/813437/gmail-features-you-should-try/)
-   › [XGIMI Horizon Pro 4K Projector Review: Shining Bright](https://www.howtogeek.com/815363/xgimi-horizon-pro-4k-projector-review/)
-   › [Upgrade Your TV and Gaming Experience With These Bias Lights](https://www.howtogeek.com/813580/upgrade-your-tv-and-gaming-experience-with-these-bias-lights/)