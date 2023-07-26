# A-1-Click-Solution-for-CRUD-REST-API-Services

[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services#readme)
[![es](https://img.shields.io/badge/lang-es-yellow.svg)](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/blob/master/README.es.md)

# Create a New Application with the Web API

This topic contains step-by-step instructions on how to create an application with the  **Web API**. For more information on the  **Web API**, see the following topic:  [Backend Web API Service](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1).

1.  Create a new solution in Visual Studio. Select the  **DevExpress v22.1  XAF Template Gallery**  project template and click  **Next**.
    
    ![Create a new project from the XAF Template Gallery](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard.png?v=22.1)
    
2.  Specify the name and location of the new project (solution), and click  **Create**.
    
3.  Ensure that the  **.NET Core**  platform is selected and run the  **XAF Solution Wizard**.
    
    ![Tutorial launch Wizard](https://docs.devexpress.com/eXpressAppFramework/images/btutorial_bmd_lesson1_1_1.png?v=22.1)
    
4.  In the Solution Wizard, select  **Service (ASP.NET Core Web API)**  and other platforms that you wish to add to the solution.
    
    ![Select Web (ASP.NET Core Blazor)](https://docs.devexpress.com/eXpressAppFramework/images/btutor_solution_wizard_platform_select.png?v=22.1)
    
5.  Select the  **eXpress Persistent Objects**  or  **Entity Framework Core**  ORM for your application and click  **Next**.
    
    ![Select ORM](https://docs.devexpress.com/eXpressAppFramework/images/web-api-wizard-orm.png?v=22.1)
    
6.  Choose the security options for your application.
    
    ![Select authentication](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard-auth.png?v=22.1)
    
    See the following topic for details:  [Authentication in Web API projects](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    
    If you selected ASP.NET Core Blazor on the  **Choose Target Platforms**  page, you can also specify if the Web API service should be added as a separate project or integrated into Blazor application project:
    
    ![Select authentication](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard-auth-and-projects.png?v=22.1)
    
7.  [Create endpoints and test the Web API](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).


# Add a Web API Project to an Existing Solution

This topic contains step-by-step instructions on how to add a  [Web API](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  project to a .NET Core application.

1.  Use the  [Solution Wizard](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  to add a Web API project to your application. Right-click the solution in the  **Solution Explorer**  and choose  **Add DevExpress Item | New Project…**.
    
    ![Solution](https://docs.devexpress.com/eXpressAppFramework/images/solution-wizard-context-menu.png?v=22.1)
    
2.  Select the  **.NET Core**  platform and run the  **XAF Solution Wizard**.
    
    ![Tutorial launch Wizard](https://docs.devexpress.com/eXpressAppFramework/images/btutorial_bmd_lesson1_1_1.png?v=22.1)
    
3.  Choose the  **ASP.NET Core Web API Service**  option and specify the project name.
    
    ![Tutorial launch Wizard](https://docs.devexpress.com/eXpressAppFramework/images/select-web-api.png?v=22.1)
    
4.  Select the  **eXpress Persistent Objects**  or  **Entity Framework Core**  ORM for your application and click  **Next**.
    
    ![Select ORM](https://docs.devexpress.com/eXpressAppFramework/images/web-api-wizard-orm.png?v=22.1)
    
5.  _Optional._  Choose the security options for your application and click  **Finish**. See the following topic for details:  [Authentication in Web API projects](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    
    ![Select authentication](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard-auth.png?v=22.1)
    
    The wizard adds the Web API project to your application.
    
    If you use the  **Sha512**  algorithm to encrypt passwords in your application, set the  **PasswordCryptographer.SupportLegacySha512**  property to  `true`  in the Web API project  _Startup.cs_  file for backward compatibility:
    
    **File:**  _MySolution.WebApi\Startup.cs_
    

    
    ```csharp
    public class Startup {
        // ...
        public void ConfigureServices(IServiceCollection services) {
            // ...
            PasswordCryptographer.SupportLegacySha512 = true;
            // ...
        }
    }
    
    ```
    
6.  [Create endpoints and test the Web API](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).



# Add the Web API Service to a Blazor Server Project


This topic describes how to add the  [Web API](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  service to a Blazor Server project.

1.  Install the following NuGet packages to the Blazor Server project (_MySolution.Blazor.Server_):
    
    -   **DevExpress.ExpressApp.WebApi**
    -   **Swashbuckle.AspNetCore**
    -   **DevExpress.ExpressApp.WebApi.Xpo**  - in XPO applications only
    
    See the following topic for more information on how to install DevExpress NuGet packages:  [Install DevExpress Controls Using NuGet Packages](https://docs.devexpress.com/GeneralInformation/115912/installation/install-devexpress-controls-using-nuget-packages?v=22.1).
    
2.  Use the code below to configure services for the  **Web API**:
    
    **File:**  _MySolution.Blazor.Server\Startup.cs_
    

    
    ```csharp
    using DevExpress.ExpressApp.WebApi.Services;
    using DevExpress.ExpressApp.WebApi.Swashbuckle;
    using Microsoft.OpenApi.Models;
    using Microsoft.AspNetCore.OData;
    // ...
    public void ConfigureServices(IServiceCollection services) {
    // ...     
        services.AddXafWebApi(Configuration, options => {
            // Use options.BusinessObject<YourBusinessObject>() 
            // to make the Business Object available in the Web API and
            // generate the GET, POST, PUT, and DELETE HTTP methods for it.
        })
        // in XPO applications, uncomment the following line
        // .AddXpoServices(); 
        services.AddControllers().AddOData((options, serviceProvider) => {
            options
                .AddRouteComponents("api/odata", new EdmModelBuilder(serviceProvider).GetEdmModel())
                .EnableQueryFeatures(100);
        });
        services.AddSwaggerGen(c => {
            c.EnableAnnotations();
            c.SwaggerDoc("v1", new OpenApiInfo {
                Title = "MySolution API",
                Version = "v1",
                Description = @"Use AddXafWebApi(Configuration, options) in the MySolution.Blazor.Server\Startup.cs file to make Business Objects available in the Web API."
            });
        });
    }
    
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env) {
        if(env.IsDevelopment()) {
            // ...
            app.UseSwagger();
            app.UseSwaggerUI(c => {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "MySolution WebApi v1");
            });
        }
        // ...
    }
    
    ```
    
3.  _Optional._  Configure authentication settings. The  **Web API**  supports all standard ASP.NET Core  [authentication](https://docs.microsoft.com/en-us/aspnet/core/security/authentication)  techniques. See the following topic for more information:  [Authentication in Web API projects](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    
4.  [Create endpoints and test the Web API](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).



# Add CRUD Endpoints and Consume the Web API



This topic describes how to create endpoints and test the  [Web API](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  service. See the following topics for information on how to create a project with the  **Web API**:

-   [Create a New Application with the Web API](https://docs.devexpress.com/eXpressAppFramework/403401/backend-web-api-service/create-new-application-with-web-api-service?v=22.1).
-   [Add a Web API Project to an Existing Solution](https://docs.devexpress.com/eXpressAppFramework/403561/backend-web-api-service/add-web-api-to-blazor-server?v=22.1).
-   [Add the Web API Service to a Blazor Server Project](https://docs.devexpress.com/eXpressAppFramework/403561/backend-web-api-service/add-web-api-to-blazor-server?v=22.1).

## Create Endpoints for Business Objects

In the  _Startup.cs_  file, add or find the  [services.AddXafWebApi](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.WebApi.Services.WebApiStartupExtensions.AddXafWebApi(IServiceCollection--IConfiguration--Action-WebApiOptions-)?v=22.1)  method call and use the  **BusinessObject**  method to create endpoints for business objects. The following code creates endpoints for the  **ApplicationUser**  and  **Contact**  business objects:

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
using MySolution.Module.BusinessObjects;
// ...
namespace MySolution.WebApi {
    public class Startup {
        // ...
        public void ConfigureServices(IServiceCollection services) {
            // ...
            services.AddXafWebApi(Configuration, options => {
                options.BusinessObject<ApplicationUser>();
                options.BusinessObject<Contact>();
            })
            // in XPO applications, uncomment the following line
            // .AddXpoServices(); 
            // ...
        }
        // ...    
    }
}

```

## Expose or Hide Business Object Properties

[ASP.NET Core Web API/OData](https://learn.microsoft.com/en-us/odata/webapi/getting-started)  exposes public business class properties of simple/value types with a setter (writable) in a Web API response. Our Web API Service additionally exposes read-only calculated XPO properties of simple/value types without a setter (readonly) marked with  [PersistentAliasAttribute](https://docs.devexpress.com/XPO/DevExpress.Xpo.PersistentAliasAttribute?v=22.1).

To hide business class properties from a Web API response at design time, decorate them with  [IgnoreDataMemberAttribute](https://learn.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ignoredatamemberattribute?view=net-6.0), if required.

ASP.NET Core Web API/OData does include complex type, reference and collection business class properties in a Web API response by default. To include complex type, reference and collection business class properties in a Web API response, use  [OData query](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-overview)  options:

-   [Get a Reference Object](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1#get-a-reference-object)
-   [Get an Associated Collection](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1#get-an-associated-collection)
-   [Change the Expansion Depth for Related Business Objects](https://docs.devexpress.com/eXpressAppFramework/403719/backend-web-api-service/use-odata-to-send-requests/customize-odata-options?v=22.1)

For advanced OData entity model structure customizations, refer to  [Change an EDM Model Structure using ODataModelBuilder](https://docs.devexpress.com/eXpressAppFramework/403719/backend-web-api-service/use-odata-to-send-requests/customize-odata-options?v=22.1).

## Use the Swagger UI to Test the Web API

If your solution includes a  **Web API**  project, right-click the project in the  **Solution Explorer**  and choose  **Debug | Start new instance**  to run the  **Web API**  project. A browser displays the page with the available endpoints.

If your solution includes a startup  **Blazor Server**  project that contains the  **Web API**, run the application. Add  _/swagger_  to the application address (for example,  _https://localhost:44318/swagger_  ) and press  _Enter_  to display a page with available endpoints.

Refer to the following link for more information on the page’s UI:  [Swagger UI](https://swagger.io/tools/swagger-ui/).

The default configuration starts the Web API service on different ports depending on the project:

![image](https://github.com/lianhdez95/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/e91873a0-0d88-4f24-850f-d0d01353944d)


![XAF Web API](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-swagger.png?v=22.1)

Test the Web API. Expand the  **GET ApplicationUser**  endpoint and click the  **Try it out**  button. The  **Execute**  button is displayed. Click this button to see the result.

## Use the Postman Tool to Test the Web API

You can also use the  [Postman](https://learning.postman.com/docs/getting-started/installation-and-updates/)  tool to test the Web API. The Postman tool is more flexible and allows you to send complex requests with  [parameters](https://learning.postman.com/docs/sending-requests/requests/#sending-parameters)  to the  **Web API**  service. Refer to the following link for more information on how to utilize this tool:  [Sending your first request](https://learning.postman.com/docs/getting-started/sending-the-first-request/).

>TIP
To test the **Web API** service hosted on _localhost_, install the Postman desktop agent as described in the following topic: [Installing the Postman desktop agent](https://learning.postman.com/docs/getting-started/installation-and-updates/#installing-the-postman-desktop-agent).

The image below shows a request to the  _Contact_  business object filtered by  _FirstName_  in the Postman Web UI (`https://web.postman.co/home`):

![Use Postman to create a Web API request](https://docs.devexpress.com/eXpressAppFramework/images/web-api-postman.png?v=22.1)

See the following topics for more information on  [OData](https://docs.microsoft.com/en-us/odata/overview)  query options:

-   [Query options overview](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-overview)
-   [Query options usage](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-usage)

If you enable authentication for your  **Web API**  service, specify the authorization settings for the Postman tool. See the following topic for details:  [Specifying authorization details](https://learning.postman.com/docs/sending-requests/authorization/#specifying-authorization-details). If the  **Web API**  service uses the XAF JWT token from the “Authenticate” endpoint, copy it from the Swagger UI page as described in the following section:  [Use the Swagger UI to Test the JWT Authentication](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1#use-the-swagger-ui-to-test-the-jwt-authentication).

## Consume the Web API from .NET Applications

Refer to the following help article to find the example:  [Make HTTP Requests to the Web API from .NET Applications](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1).


# Make HTTP Requests to the Web API from .NET Applications


You can send requests to a  [Web API](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  service from any  [.NET application with the HttpClient](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient)  library. Use the  [OData](https://docs.microsoft.com/en-us/odata/overview)  syntax to build requests. See the following topics for more information on  [OData](https://docs.microsoft.com/en-us/odata/overview)  query options:

-   [Query options overview](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-overview)
-   [Query options usage](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-usage)

The examples below send requests to the Web API service available at the following address:  `https://localhost:44319/`.

## Get a JWT Authentication Token

To obtain the  [JWT Authentication](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1)  token for further data requests, send a request to the following endpoint:  `api/Authentication/Authenticate`. The following example uses “Sam” as a user name and an empty password:


```csharp
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();

            // Obtain a JWT token.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
        }
    }
}

```

## Operate with Business Objects

### [#](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#get-business-objects)Get Business Objects

The following code retrieves the  _LastName_  and  _Email_  fields of the  _Employee_  business object where  _FirstName_  equals “Mary”:



```csharp
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();

            // Obtain a JWT token. This example uses "Sam" as a user name and an empty password.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);

            // Send a request to fetch data.
            string requestAddress = "https://localhost:44319/api/odata/Employee";
            var employees = await httpClient.GetStringAsync($"{requestAddress}?$filter=FirstName eq 'Mary'&$select=LastName,Email");
            Console.WriteLine(employees);
        }
    }
}

```

Result

### Create a Business Object

The code below adds a new  _Employee_  instance with the  _FirstName_  field set to “Mary” and the  _LastName_  field set to “Gordon”:


```csharp
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();
            // Obtain a JWT token. This example uses "Sam" as a user name and an empty password.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);

            // Pass data to the Web API service. 
            StringContent dataHttpContent = new StringContent(@"{ ""FirstName"": ""Mary"", ""LastName"":""Gordon"" }", Encoding.UTF8, "application/json");
            var dataResponse = await httpClient.PostAsync($"{requestAddress}", dataHttpContent);
            Console.WriteLine(dataResponse.StatusCode);
        }
    }
}

```

**Result**  (the  _dataResponse.StatusCode_  value): 201 Created

### Get a Reference Object

You can use one of the following techniques:

[Technique 1 (Expand Query Parameter)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-1-expand-query-parameter)

The  [$expand](https://docs.microsoft.com/en-us/odata/webapi/odata-expand)  OData query parameter allows you to obtain a reference business object  **together with**  the main object.

[Technique 2 (Ref Endpoint)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-2-ref-endpoint)

The  [$ref](https://docs.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/odata-v4/entity-relations-in-odata-v4#getting-related-entities)  endpoint allows you to obtain a reference business object  **without**  its main object.

#### Technique 1 (Expand Query Parameter)

The example below uses  **$expand**  to get an  _Employee_  object with its related  _Department_  object:



```csharp
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();

            // Obtain a JWT token. This example uses "Sam" as a user name and an empty password.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);

            // Send a request to fetch data.
            string requestAddress = "https://localhost:44319/api/odata/Employee";
            var employees = await httpClient.GetStringAsync($"{requestAddress}?$filter=FirstName eq 'Mary'&$select=LastName,Email&$expand=Department");
            Console.WriteLine(employees);
        }
    }
}

```

Result

The  **$expand**  parameter can be applied to more than one level of related business objects. The following example retrieves a data chain that consists of two related business objects:



```csharp
// ...
string requestAddress = "https://localhost:44319/api/odata/Department";
var departments = await httpClient.GetStringAsync($"{requestAddress}?$select=Title&$expand=Employees($select=FirstName,LastName;$expand=Tasks($select=Subject))");
// ...

```

Result

The default  [max expansion depth](https://docs.microsoft.com/en-us/odata/webapi/odata-expand#expand-depth)  equals two. You can change this parameter as described in the following topic:  [Change the Expansion Depth for Related Business Objects](https://docs.devexpress.com/eXpressAppFramework/403719/backend-web-api-service/use-odata-to-send-requests/customize-odata-options?v=22.1#change-the-expansion-depth-for-related-business-objects).

#### Technique 2 (Ref Endpoint)

The example below gets the  _Employee_‘s  _Department_  reference object:


```csharp
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();

            // Obtain a JWT token. This example uses "Sam" as a user name and an empty password.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);

            // Send a request to fetch data.
            string requestAddress = "https://localhost:44319/api/odata/Employee/1/Department/$ref";
            // or 
            // string requestAddress = "https://localhost:44319/api/odata/Employee(1)/Department/$ref";
            var department = await httpClient.GetStringAsync(requestAddress);
            Console.WriteLine(department);
        }
    }
}

```

Result

### Get an Associated Collection

You can use one of the following techniques:

[Technique 1 (Expand Query Parameter)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-1-expand-query-parameter-1)

The  [$expand](https://docs.microsoft.com/en-us/odata/webapi/odata-expand)  OData query parameter allows you to obtain objects from an associated collection  **together with**  the main object.

[Technique 2 (Ref Endpoint)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-2-ref-endpoint-1)

The  [$ref](https://docs.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/odata-v4/entity-relations-in-odata-v4#getting-related-entities)  endpoint allows you to obtain objects from an associated collection  **without**  its main object.

#### Technique 1 (Expand Query Parameter)

The following example gets  _LastName_,  _Email_, and the related  _Tasks_  collection of the  _Employee_  business object where  _FirstName_  equals “Mary”:



```csharp
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();

            // Obtain a JWT token. This example uses "Sam" as a user name and an empty password.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);

            // Send a request to fetch data.
            string requestAddress = "https://localhost:44319/api/odata/Employee";
            var employees = await httpClient.GetStringAsync($"{requestAddress}?$filter=FirstName eq 'Mary'&$select=LastName,Email&$expand=Tasks");
            Console.WriteLine(employees);
        }
    }
}

```

Result

#### Technique 2 (Ref Endpoint)

The example below gets the  _Employee_‘s  _Tasks_  collection:



```csharp
using System.Net.Http;
using System.Net.Http.Headers;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1 {
    class Program {
        static async Task Main(string[] args) {
            HttpClient httpClient = new HttpClient();

            // Obtain a JWT token. This example uses "Sam" as a user name and an empty password.
            StringContent httpContent = new StringContent(@"{ ""userName"": ""Sam"", ""password"": """" }", Encoding.UTF8, "application/json");
            var response = await httpClient.PostAsync("https://localhost:44319/api/Authentication/Authenticate", httpContent);

            // Save the token for further requests.
            var token = await response.Content.ReadAsStringAsync();

            // Set the authentication header. 
            httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);

            // Send a request to fetch data.
            string requestAddress = "https://localhost:44319/api/odata/Employee(1)/Tasks/$ref";
            // or 
            // string requestAddress = "https://localhost:44319/api/odata/Employee/1/Tasks/$ref";
            var tasks = await httpClient.GetStringAsync(requestAddress);
            Console.WriteLine(tasks);
        }
    }
}

```

Result

### Assign an Object to a Reference Property

The example below sets the  _Employee_‘s  _Department_  reference property to the  _Department_  object:

#### Technique 1 (In Body)



```csharp
string requestAddress = "https://localhost:44318/api/odata/Employee/1";
string jsonBody = @"{ ""Department"": ""1""}";
// or
// string jsonBody = @"{ ""Department"": { ""Oid"": ""1"" }}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content

#### Technique 2 (Ref Endpoint)



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1/Department/$ref";
string jsonBody = "{\"@odata.id\":\"https://localhost:44319/api/odata/Department/1\"}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content

### Add an Object to a Collection

The example below adds the  _DemoTask_  object to the  _Employee_‘s  _Tasks_  collection:



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1/Tasks/$ref";
string jsonBody = "{\"@odata.id\":\"https://localhost:44319/api/odata/DemoTask(1)\"}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PostAsync(requestAddress, content);
Console.WriteLine(response);

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content

### Unlink an Object from a Reference Property

The example below removes the  _Employee_‘s  _Department_  reference property value:



```csharp
string requestAddress = @"https://localhost:44319/api/odata/Employee/1/Department/$ref?
                          $id=https://localhost:44319/api/odata/Department/1";
// or 
// string requestAddress = @"https://localhost:44319/api/odata/Employee(1)/Department/$ref?
//                           $id=https://localhost:44319/api/odata/Department(1)";
var response = await httpClient.DeleteAsync(requestAddress);
Console.WriteLine(response)

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content

### Remove an Object from a Collection

The example below removes the  _DemoTask_  object from the  _Employee_‘s  _Tasks_  collection:



```csharp
string requestAddress = @"https://localhost:44319/api/odata/Employee/1/Tasks/$ref?
                          $id=https://localhost:44319/api/odata/DemoTask/1";
// or 
// string requestAddress = @"https://localhost:44319/api/odata/Employee(1)/Tasks/$ref?
//                           $id=https://localhost:44319/api/odata/DemoTask(1)";
var response = await httpClient.DeleteAsync(requestAddress);
Console.WriteLine(response)

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content

### Modify an Object Assigned to a Reference Property

The example below modifies the  _Department_  object assigned to the  _Employee_‘s  _Department_  reference property:



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1";
string jsonBody = @"{ ""Department"": { ""Office"":""504""} }";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content

### Modify Objects Added to an Associated Collection

The example below modifies the  _DemoTask_  object with  `Oid`=1 from the  _Employee_‘s  _Tasks_  collection. If the collection does not contain the  _DemoTask_  object with this  `Oid`, this object will be added:



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1";
string jsonBody = @"{ ""Tasks"": [{ ""Oid"": ""1"", ""Subject"":""New subject""} ]}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Result**  (the  _dataResponse.StatusCode_  value): 204 No Content


# Web API Authentication


The  **Web API**  supports all standard ASP.NET Core  [authentication](https://docs.microsoft.com/en-us/aspnet/core/security/authentication)  techniques that you can specify in the  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_) file. See the following topic for more information:  [Authentication](https://docs.devexpress.com/eXpressAppFramework/119064/data-security-and-safety/security-system/authentication?v=22.1).

If you use the  [Solution Wizard](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  to create a  **Web API**  project, enable authentication on the  **Choose Security**  page:

![Select authentication](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard-auth.png?v=22.1)

**Standard Authentication**

The wizard generates  [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token)  authentication scaffolding code for the  **Web API**.

**OAuth2 Authentication**

The wizard adds the JWT and  [Azure AD](https://azure.microsoft.com/en-us/products/active-directory/)  scaffolding code to the  _MySolution.WebApi\appsettings.json_  file.

**Windows Active Directory**

The wizard adds the JWT scaffolding code to the  _MySolution.WebApi\appsettings.json_  file and the scaffolding code for Windows Active Directory to the  _MySolution.WebApi\Properties\launchSettings.json_  file.

See the following topics for information on how to configure the authentication scaffolding code and manually enable authentication:

-   [Configure the JWT Authentication](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1)
-   [Configure the OAuth2 Azure Authentication](https://docs.devexpress.com/eXpressAppFramework/403505/backend-web-api-service/authentication-in-web-api-applications/enable-oauth2-azure-authentication?v=22.1)



# Configure the JWT Authentication for the Web API


## Enable Authentication in a New Project

Use the  [Solution Wizard](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  to create a  **Web API**  project with the JWT authentication. If you choose  **Standard**  authentication on the  **Choose Security**  page, the wizard generates  [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token)  authentication scaffolding code.

![Enable the JWT authentication](https://docs.devexpress.com/eXpressAppFramework/images/web-api-wizard-auth-jwt.png?v=22.1)

You can replace the autogenerated  **IssuerSigningKey**  value with your JWT signing key and change other JWT settings in the  _appsettings.json_  file. We recommend that you use the  [Secret Manager](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets)  tool to store the signing key. You can store it in the  _appsettings.json_  file for testing purposes only.

**File:**  _MySolution.WebApi\appsettings.json_  (_MySolution.Blazor.Server\appsettings.json_)



```json
// ...
"Authentication": {
    "Jwt": {
    "Issuer": "My",
    "Audience": "http://localhost:4200",
    "IssuerSigningKey": "c1d2e0a7-405b-40be-9b36-fa93469b673a"
    }
}    
// ...

```

See the following section for information on how to test the JWT authentication:  [Use the Swagger UI to Test the JWT Authentication](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1&p=netframework#use-the-swagger-ui-to-test-the-jwt-authentication).

## Enable Authentication in an Existing Project

To add the JWT authentication to an existing  **Web API**  or  **Blazor Server**  project, follow the steps below.

### Step 1. Install the Required NuGet Packages

Install the following NuGet packages to the  _MySolution.WebApi_  (_MySolution.Blazor.Server_) and  _MySolution.Module_  projects:

-   **DevExpress.ExpressApp.Security.AspNetCore**
-   **Microsoft.AspNetCore.Authentication.JwtBearer**
-   **DevExpress.ExpressApp.Security.Xpo**  - in XPO applications
-   **DevExpress.EntityFrameworkCore.Security**  - in EF Core applications

See the following topic for details:  [Install DevExpress Controls Using NuGet Packages](https://docs.devexpress.com/GeneralInformation/115912/installation/install-devexpress-controls-using-nuget-packages?v=22.1).

### Step 2. Modify appsettings.json

Add the  **Jwt**  option to the  **Authentication**  section in the  _appsettings.json_  file.

**File:**  _MySolution.WebApi\appsettings.json_  (_MySolution.Blazor.Server\appsettings.json_)



```json
// ...
"Authentication": {
    "Jwt": {
    "Issuer": "My",
    "Audience": "http://localhost:4200",
    "IssuerSigningKey": "c1d2e0a7-405b-40be-9b36-fa93469b673a"
    }
},    
// ...

```

The  **IssuerSigningKey**  value is an autogenerated key. You can replace it with your JWT signing key. You can store it in the  _appsettings.json_  file for testing purposes only. We recommend that you use the  [Secret Manager](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets)  tool to store the signing key.

### Step 3. Modify Startup.cs

Add the following code to the  **ConfigureServices**  method to enable authentication:

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
using DevExpress.ExpressApp.Security;
using DevExpress.Persistent.BaseImpl.PermissionPolicy;
using Microsoft.AspNetCore.Authorization;
using Microsoft.Extensions.DependencyInjection;
// ...
public void ConfigureServices(IServiceCollection services) {
    //...
    services.AddXafAspNetCoreSecurity(Configuration, options => {
        options.RoleType = typeof(PermissionPolicyRole);
        options.UserType = typeof(MySolution.Module.BusinessObjects.ApplicationUser);
        options.UserLoginInfoType = typeof(MySolution.Module.BusinessObjects.ApplicationUserLoginInfo);
        // in XPO applications, uncomment the following line
        // options.Events.OnSecurityStrategyCreated = securityStrategy => ((SecurityStrategy)securityStrategy).RegisterXPOAdapterProviders();
        options.SupportNavigationPermissionsForTypes = false;
    })
    .AddAuthenticationStandard(options => {
        options.IsSupportChangePassword = true;
    });
    var authentication = services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme);
    // The AddJwtBearer method adds JWT credentials to the XAF authentication. 
    authentication
        .AddJwtBearer(options => {
            options.TokenValidationParameters = new TokenValidationParameters() {
                ValidIssuer = Configuration["Authentication:Jwt:Issuer"],
                ValidAudience = Configuration["Authentication:Jwt:Audience"],
                IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(Configuration["Authentication:Jwt:IssuerSigningKey"]))
            };
        });
    services.AddAuthorization(options => {
        options.DefaultPolicy = new AuthorizationPolicyBuilder(
            JwtBearerDefaults.AuthenticationScheme)
                .RequireAuthenticatedUser()
                .RequireXafAuthentication()
                .Build();
    });
    // ...
    services.AddSwaggerGen(c => {
        c.EnableAnnotations();
        c.SwaggerDoc("v1", new OpenApiInfo {
            Title = "MySolution API",
            Version = "v1",
            Description = @"Use AddXafWebApi(Configuration, options) in the MySolution.WebApi\Startup.cs file to make Business Objects available in the Web API."
        });
        // The AddSecurityDefinition and AddSecurityRequirement methods enable the JWT authentication for the Swagger UI.
        c.AddSecurityDefinition("JWT", new OpenApiSecurityScheme() {
            Type = SecuritySchemeType.Http,
            Name = "Bearer",
            Scheme = "bearer",
            BearerFormat = "JWT",
            In = ParameterLocation.Header
        });
        c.AddSecurityRequirement(new OpenApiSecurityRequirement()
            {
                {
                    new OpenApiSecurityScheme() {
                        Reference = new OpenApiReference() {
                            Type = Microsoft.OpenApi.Models.ReferenceType.SecurityScheme,
                            Id = "JWT"
                        }
                    },
                    new string[0]
                },
        });
    });

```

### Step 4. Add a JWT Authentication Service

You can implement your own JWT service, or use the JWT service that the  [Solution Wizard](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  generates. You can find the auto-generated service code below. To use this JWT service, create the  _JWT_  folder in the  _MySolution.WebApi_  (_MySolution.Blazor.Server_) project and add the  _AuthenticationController.cs_  file to this folder.

**File:**  _MySolution.WebApi\JWT\AuthenticationController.cs_  (_MySolution.Blazor.Server\JWT\AuthenticationController.cs_)


```csharp
using System;
using System.IdentityModel.Tokens.Jwt;
using System.Security.Claims;
using System.Text;
using DevExpress.ExpressApp.Security;
using DevExpress.ExpressApp.Security.Authentication;
using Microsoft.AspNetCore.Mvc;
using Swashbuckle.AspNetCore.Annotations;

namespace MySolution.WebApi.JWT {
    [ApiController]
    [Route("api/[controller]")]
    public class AuthenticationController : ControllerBase {
        readonly IStandardAuthenticationService securityAuthenticationService;
        readonly IConfiguration configuration;

        public AuthenticationController(IStandardAuthenticationService securityAuthenticationService, IConfiguration configuration) {
            this.securityAuthenticationService = securityAuthenticationService;
            this.configuration = configuration;
        }
        [HttpPost("Authenticate")]
        public IActionResult Authenticate(
            [FromBody]
            [SwaggerRequestBody(@"For example: <br /> { ""userName"": ""Admin"", ""password"": """" }")]
            AuthenticationStandardLogonParameters logonParameters
        ) {
            ClaimsPrincipal user = securityAuthenticationService.Authenticate(logonParameters);

            if(user != null) {
                var issuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(configuration["Authentication:Jwt:IssuerSigningKey"]));
                var token = new JwtSecurityToken(
                    issuer: configuration["Authentication:Jwt:Issuer"],
                    audience: configuration["Authentication:Jwt:Audience"],
                    claims: user.Claims,
                    expires: DateTime.Now.AddHours(2),
                    signingCredentials: new SigningCredentials(issuerSigningKey, SecurityAlgorithms.HmacSha256)
                    );
                return Ok(new JwtSecurityTokenHandler().WriteToken(token));
            }
            return Unauthorized("User name or password is incorrect.");
        }
    }
}

```

### Step 5. Add the ApplicationUser and ApplicationUserLoginInfo Business Objects

XAF requires the  _ApplicationUser_  and  _ApplicationUserLoginInfo_  business objects to store user information. Add these business objects to the  _MySolution.Module_  project as described in  _Step 1_  of the following section:  [Use Active Directory and OAuth2 Authentication Providers in ASP.NET Core Blazor Applications: Common Steps](https://docs.devexpress.com/eXpressAppFramework/402197/data-security-and-safety/security-system/authentication/oauth-and-custom-authentication/active-directory-and-oauth2-authentication-providers-in-blazor-applications?v=22.1#common-steps).

## Use the Swagger UI to Test the JWT Authentication

1.If your solution includes a  **Web API**  project, right-click the project in the  **Solution Explorer**  and choose  **Debug | Start new instance**  to run the  **Web API**  project. A browser displays the page with the available endpoints.

If your solution includes a startup  **Blazor Server**  project with the  **Web API**, run the application. Add  _/swagger_  to the application address (for example,  _https://localhost:44318/swagger_  ) and press  _Enter_  to display a page with available endpoints.

Refer to the following link for more information on the page’s UI:  [Swagger UI](https://swagger.io/tools/swagger-ui/).

2.  Expand the  **Post Authentication**  endpoint and click the  **Try it out**  button.
    
3.  In the displayed form, enter the  **userName**  and  **password**  for an authorized user. In a template application, use  _Admin_  as the user name and an empty string as the password.
    
4.  Copy the public key from the  _Response body_, click the  **Authorize**  button  ![Authorize button](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-authorize-button.png?v=22.1)  to open the  **Available authorizations**  form, and paste the public key in the  **Value**  editor to enable the JWT authentication.
    
![](https://docs.devexpress.com/eXpressAppFramework/images/jwt-authentication.gif?v=22.1)

Refer to the following topic for information on how to create Web API endpoints:  [Create Endpoints and Test the Web API](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).



# Configure the OAuth2 Azure Authentication for the Web API


The  **Web API**  supports the OAuth2 Azure Authentication. To use it,  [set up](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-create-new-tenant)  an Azure Active Directory (Azure AD) tenant. After you obtain a tenant,  [register](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app)  the  **Web API**  with the Microsoft identity platform. When you configure platform settings for the  **Web API**, select  _Single-page application_  as the  **Web application**  type and set the following  **Redirect URI**:  _https://localhost:44318/swagger/oauth2-redirect.html_.

## Enable Authentication in a New Project

Use the  [Solution Wizard](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  to create a  **Web API**  project. Enable the OAuth2 Azure Authentication on the  **Choose Security**  page:

![Select authentication](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard-auth.png?v=22.1)

The wizard generates  [Azure AD](https://azure.microsoft.com/en-us/products/active-directory/)  authentication scaffolding code.

Update the generated code as follows:

1.  Specify your  [Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-create-new-tenant)  settings in the  _“Authentication”_  section of the  _appsettings.json_  file:
    
    **File:**  _MySolution.WebApi\appsettings.json_  (_MySolution.Blazor.Server\appsettings.json_)

    
    ```json
    // ...
    "Authentication": {
        // ...
        "AzureAd": {
            "Instance": "https://login.microsoftonline.com/",
            "Domain": "abcdabcd-abcd-abcd-abcd-abcdabcdabcd", // This value is an example - replace it with your tenant domain.
            "TenantId": "organizations", // Use 'common', 'organizations', or the tenant Id obtained from the Azure portal. 
            "ClientId": "11111111-1111-1111-1111-111111111111", // This value is an example - replace it with your client Id (application ID obtained from the Azure portal).
            "CallbackPath": "/ms_auth"
        }
    },    
    // ...
    
    ```
    
2.  Configure scopes according to your Azure settings. See the following topic for details:  [Quickstart: Configure an application to expose a web API](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-expose-web-apis).
    
    **File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)
    
  
    
    ```csharp
        AuthorizationCode = new OpenApiOAuthFlow() {
            // ...
            Scopes = new Dictionary<string, string> {
                { "api://11111111-1111-1111-1111-111111111111/WebApi", "Read WebApi"} 
            }
        }
    
    ```
    
3.  In the  **options.Events.OnAuthenticated**  delegate, implement the authentication logic. The auto-generated code maps an OAuth provider user to an application user. If this code suits your requirements, comment out  `return`.
    
    See the following topic for more information:  [How to: Use Active Directory and OAuth2 Authentication Providers in ASP.NET Core Blazor Applications](https://docs.devexpress.com/eXpressAppFramework/402197/data-security-and-safety/security-system/authentication/oauth-and-custom-authentication/active-directory-and-oauth2-authentication-providers-in-blazor-applications?v=22.1#google-azure-and-github-providers).
    
    **File:**  _MySolution.Blazor.Server\Startup.cs_  (_MySolution.Blazor.Server\Startup.json_)
    

    
    ```csharp
    options.Events.OnAuthenticated = (externalAuthenticationContext) => {
        // When a user successfully logs in with an OAuth provider, you can get their unique user key.
        //return;
        if (externalAuthenticationContext.AuthenticatedUser == null &&
        externalAuthenticationContext.Principal.Identity.AuthenticationType != SecurityDefaults.PasswordAuthentication &&
        externalAuthenticationContext.Principal.Identity.AuthenticationType != SecurityDefaults.WindowsAuthentication && !(externalAuthenticationContext.Principal is WindowsPrincipal)) {
            const bool autoCreateUser = true;
        // ...
        }
    
    ```
    

See the following section for information on how to test the OAuth2 Azure authentication:  [Use the Swagger UI to Test the OAuth2 Azure Authentication](https://docs.devexpress.com/eXpressAppFramework/403505/backend-web-api-service/authentication-in-web-api-applications/enable-oauth2-azure-authentication?v=22.1&p=netframework#use-the-swagger-ui-to-test-the-oauth2-azure-authentication).

## Enable Authentication in an Existing Project

Follow the steps below to add the OAuth2 Azure authentication to an existing  **Web API**  or  **Blazor Server**  project.

### Step 1. Install the Required NuGet Packages

Install the following NuGet Packages:

-   **DevExpress.ExpressApp.Security.Xpo**  - to the  _MySolution.WebApi_  and  _MySolution.Module_  projects;
-   **Microsoft.Identity.Web.UI**  - to  _MySolution.WebApi_.

See the following topic for details:  [Install DevExpress Controls Using NuGet Packages](https://docs.devexpress.com/GeneralInformation/115912/installation/install-devexpress-controls-using-nuget-packages?v=22.1).

### Step 2. Modify appsettings.json

Add the  **AzureAd**  option to the  **Authentication**  section in the  _appsettings.json_  file and specify your Azure AD credentials.

**File:**  _MySolution.WebApi\appsettings.json_  (_MySolution.Blazor.Server\appsettings.json_)


```json
// ...
"Authentication": {
    "AzureAd": {
        "Instance": "https://login.microsoftonline.com/",
        "Domain": "abcdabcd-abcd-abcd-abcd-abcdabcdabcd", // This value is an example, replace it with your tenant domain.
        "TenantId": "organizations", // Use 'common', 'organizations', or the tenant Id obtained from the Azure portal.
        "ClientId": "11111111-1111-1111-1111-111111111111", // This value is an example, replace it with your client Id (application ID obtained from the Azure portal).
        "CallbackPath": "/ms_auth"
    }
},    
// ...

```

### Step 3. Modify Startup.cs

Add the following code to the  **ConfigureServices**  method to enable authentication:

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
// ...
using DevExpress.ExpressApp.Security;
using DevExpress.Persistent.BaseImpl.PermissionPolicy;
using DevExpress.ExpressApp;
using System.Security.Claims;
using Microsoft.Identity.Web;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.Extensions.DependencyInjection;
using System.Security.Principal;
// ...
public void AddXafAspNetCoreSecurity(Configuration,IServiceCollection services) {
    // ...
    services.AddXafAspNetCoreSecurity(Configuration, options => {
        options.RoleType = typeof(PermissionPolicyRole);
        options.UserType = typeof(MySolution.Module.BusinessObjects.ApplicationUser);
        options.UserLoginInfoType = typeof(MySolution.Module.BusinessObjects.ApplicationUserLoginInfo);
        options.Events.OnSecurityStrategyCreated = securityStrategy => ((SecurityStrategy)securityStrategy).RegisterXPOAdapterProviders();
        options.SupportNavigationPermissionsForTypes = false;
    })
    .AddAuthenticationStandard(Configuration, options => {
        options.IsSupportChangePassword = true;
    })
    .AddExternalAuthentication(options => {
        options.Events.OnAuthenticated = (externalAuthenticationContext) => {
            // When a user successfully logs in with an OAuth provider, you can get their unique user key.
            //return;
            if(externalAuthenticationContext.AuthenticatedUser == null &&
            externalAuthenticationContext.Principal.Identity.AuthenticationType != SecurityDefaults.PasswordAuthentication &&
            externalAuthenticationContext.Principal.Identity.AuthenticationType != SecurityDefaults.WindowsAuthentication && !(externalAuthenticationContext.Principal is WindowsPrincipal)) {
                const bool autoCreateUser = true;

                IObjectSpace objectSpace = externalAuthenticationContext.LogonObjectSpace;
                ClaimsPrincipal externalUser = (ClaimsPrincipal)externalAuthenticationContext.Principal;

                var userIdClaim = externalUser.FindFirst("sub") ?? externalUser.FindFirst(ClaimTypes.NameIdentifier) ?? throw new InvalidOperationException("Unknown user id");
                string providerUserId = userIdClaim.Value;

                var userLoginInfo = FindUserLoginInfo(externalUser.Identity.AuthenticationType, providerUserId);
                if(userLoginInfo != null || autoCreateUser) {
                    externalAuthenticationContext.AuthenticatedUser = userLoginInfo?.User ?? CreateApplicationUser(externalUser.Identity.Name, providerUserId);
                }

                object CreateApplicationUser(string userName, string providerUserId) {
                    if(objectSpace.FirstOrDefault<MySolution.Module.BusinessObjects.ApplicationUser>(user => user.UserName == userName) != null) {
                        throw new ArgumentException($"The username ('{userName}') was already registered within the system");
                    }
                    var user = objectSpace.CreateObject<MySolution.Module.BusinessObjects.ApplicationUser>();
                    user.UserName = userName;
                    user.SetPassword(Guid.NewGuid().ToString());
                    user.Roles.Add(objectSpace.FirstOrDefault<PermissionPolicyRole>(role => role.Name == "Default"));
                    ((ISecurityUserWithLoginInfo)user).CreateUserLoginInfo(externalUser.Identity.AuthenticationType, providerUserId);
                    objectSpace.CommitChanges();
                    return user;
                }
                ISecurityUserLoginInfo FindUserLoginInfo(string loginProviderName, string providerUserId) {
                    return objectSpace.FirstOrDefault<MySolution.Module.BusinessObjects.ApplicationUserLoginInfo>(userLoginInfo =>
                                        userLoginInfo.LoginProviderName == loginProviderName &&
                                        userLoginInfo.ProviderUserKey == providerUserId);
                }
            }
        };
    });
    const string customBearerSchemeName = "CustomBearer";
    var authentication = services.AddAuthentication(customBearerSchemeName);
    authentication
    .AddJwtBearer(customBearerSchemeName, options => {
    options.TokenValidationParameters = new TokenValidationParameters() {
    ValidIssuer = Configuration["Authentication:Jwt:Issuer"],
    ValidAudience = Configuration["Authentication:Jwt:Audience"],
    IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes(Configuration["Authentication:Jwt:IssuerSigningKey"]))
    };
    });
    authentication.AddMicrosoftIdentityWebApi(Configuration, configSectionName: "Authentication:AzureAd");

    services.AddAuthorization(options => {
        options.DefaultPolicy = new AuthorizationPolicyBuilder(
            JwtBearerDefaults.AuthenticationScheme)
                .RequireAuthenticatedUser()
                .RequireXafAuthentication()
                .Build();
    });
// ...
}

```

Use the  **AddSecurityDefinition**  and  **AddSecurityRequirement**  methods to add the OAuth2 Azure authentication to the Swagger UI.

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
services.AddSwaggerGen(c => {
    //...
    var azureAdAuthorityUrl = $"{Configuration["Authentication:AzureAd:Instance"]}{Configuration["Authentication:AzureAd:TenantId"]}";
    c.AddSecurityDefinition("OAuth2", new OpenApiSecurityScheme
    {
        Type = SecuritySchemeType.OAuth2,
        Flows = new OpenApiOAuthFlows()
        {
            AuthorizationCode = new OpenApiOAuthFlow()
            {
                AuthorizationUrl = new Uri($"{azureAdAuthorityUrl}/oauth2/v2.0/authorize"),
                TokenUrl = new Uri($"{azureAdAuthorityUrl}/oauth2/v2.0/token"),
                Scopes = new Dictionary<string, string> {
                    // Configure scopes according to https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-expose-web-apis
                    {"api://11111111-1111-1111-1111-111111111111/WebApi", "Read WebApi"}
                }
            }
        }
    });
    c.AddSecurityRequirement(new OpenApiSecurityRequirement() {
        {
            new OpenApiSecurityScheme {
                Name = "OAuth2",
                Scheme = "OAuth2",
                Reference = new OpenApiReference {
                    Type = Microsoft.OpenApi.Models.ReferenceType.SecurityScheme,
                    Id = "OAuth2"
                },
                In = ParameterLocation.Header
            },
            new string[0]
        }
    });
});

```

Also, modify the  **UseSwaggerUI**  method as follows:

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env) {
    // ...
    app.UseSwaggerUI(c => {
        c.SwaggerEndpoint("/swagger/v1/swagger.json", "MySolution WebApi v1");
        c.OAuthClientId(Configuration["Authentication:AzureAd:ClientId"]);
        c.OAuthUsePkce();
    });
    // ...
}    

```

### Step 4. Add the ApplicationUser and ApplicationUserLoginInfo Business Objects

XAF requires the  _ApplicationUser_  and  _ApplicationUserLoginInfo_  business objects to store user information. Add these business objects to the  _MySolution.Module_  project as described in  _Step 1_  of the following section:  [Use Active Directory and OAuth2 Authentication Providers in ASP.NET Core Blazor Applications: Common Steps](https://docs.devexpress.com/eXpressAppFramework/402197/data-security-and-safety/security-system/authentication/oauth-and-custom-authentication/active-directory-and-oauth2-authentication-providers-in-blazor-applications?v=22.1#common-steps).

## Use the Swagger UI to Test the OAuth2 Azure Authentication

1.  If your solution includes a  **Web API**  project, right-click the project in the  **Solution Explorer**  and choose  **Debug | Start new instance**  to run the  **Web API**  project. A browser displays the page with the available endpoints.
    
    If your solution includes a startup  **Blazor Server**  project with the  **Web API**, run the application. Add  _/swagger_  to the application address (for example,  _https://localhost:44318/swagger_  ) and press  _Enter_  to display a page with available endpoints.
    
    Refer to the following link for more information on the page’s UI:  [Swagger UI](https://swagger.io/tools/swagger-ui/).
    
    ![Select authentication](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-swagger.png?v=22.1)
    
2.  Click the  **Authorize**  button:  ![Authorize button](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-authorize-button.png?v=22.1). In the  **Available authorizations**  window, select a scope and click the  **Authorize**  button:
    
    ![The Available authorizations form](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-authorization.png?v=22.1)
    
    Refer to the following topic for information on how to create Web API endpoints:  [Create Endpoints and Test the Web API](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).

    
# Create Custom Endpoints


You can create custom endpoints for the  [Web API service](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1).

1.  Right-click the project that contains a Web API service and select  **Add -> New Item**  in the context menu. Choose the  **API Controller – Empty**  template in the invoked window.
    
    ![Add API Controller](https://docs.devexpress.com/eXpressAppFramework/images/add-api-controller.jpg?v=22.1)
    
2.  Add custom endpoint methods to the new Controller (the Get, Post, Put, and Delete methods in the example below).
    
3.  If you wish to use the Web API authentication, decorate the new Controller with  [AuthorizeAttribute](https://learn.microsoft.com/dotnet/api/microsoft.aspnetcore.authorization.authorizeattribute). See the following topic for more information on how to configure the authentication:  [Web API Authentication](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    

The Controller’s code:



```csharp
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using System.Collections.Generic;

namespace MySolution.WebApi {
    [Route("api/[controller]")]
    [ApiController]
    [Authorize]
    public class CustomEndpoint1Controller : ControllerBase {
        [HttpGet]
        public IEnumerable<string> Get() {
            return new string[] { "value1", "value2" };
        }

        [HttpGet("{id}")]
        public string Get(int id) {
            return "value";
        }

        [HttpPost]
        public void Post([FromBody] string value) {
        }

        [HttpPut("{id}")]
        public void Put(int id, [FromBody] string value) {
        }

        [HttpDelete("{id}")]
        public void Delete(int id) {
        }
    }
}

```

The result in  [the Swagger UI](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1#use-the-swagger-ui-to-test-the-web-api):

![Web API Custom Endpoint](https://docs.devexpress.com/eXpressAppFramework/images/custom-endpoint-1.png?v=22.1)


# Access Object Space, Security System, and Caption Helper in Custom Endpoint Methods


This topic describes how to access an  [Object Space](https://docs.devexpress.com/eXpressAppFramework/113711/data-manipulation-and-business-logic/create-read-update-and-delete-data?v=22.1), the  [Security System](https://docs.devexpress.com/eXpressAppFramework/113366/data-security-and-safety/security-system?v=22.1), and the  [Caption Helper](https://docs.devexpress.com/eXpressAppFramework/113298/localization?v=22.1)  from custom endpoint methods.

## Useful APIs

Object to access

Injecting service

Methods and properties

[Object Space](https://docs.devexpress.com/eXpressAppFramework/113707/data-manipulation-and-business-logic/object-space?v=22.1)

[IObjectSpaceFactory](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.IObjectSpaceFactory?v=22.1)  
[INonSecuredObjectSpaceFactory](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.INonSecuredObjectSpaceFactory?v=22.1)

[IObjectSpaceFactory.CreateObjectSpace](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.IObjectSpaceFactory.CreateObjectSpace(System.Type)?v=22.1)  
[INonSecuredObjectSpaceFactory.CreateObjectSpace](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.INonSecuredObjectSpaceFactory.CreateNonSecuredObjectSpace(System.Type)?v=22.1)

[Security System](https://docs.devexpress.com/eXpressAppFramework/113366/data-security-and-safety/security-system?v=22.1)

[ISecurityProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityProvider?v=22.1)  
[ISecurityStrategyBase](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityStrategyBase?v=22.1)

[ISecurityProvider.GetSecurity](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityProvider.GetSecurity?v=22.1)  
[ISecurityStrategyBase.IsAuthenticated](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityStrategyBase.IsAuthenticated?v=22.1)  
[ISecurityStrategyBase.User](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityStrategyBase.User?v=22.1)

[Caption Helper](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Utils.CaptionHelper?v=22.1)

[ISharedCaptionHelperProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.AspNetCore.Services.Localization.ISharedCaptionHelperProvider?v=22.1)

[ISharedCaptionHelperProvider.GetCaptionHelper](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.AspNetCore.Services.Localization.ISharedCaptionHelperProvider.GetCaptionHelper?v=22.1)

## Prerequisites

If you created your application in v21.2 or earlier, you need to use the Application Builder’s  [ObjectSpaceProviders](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Blazor.ApplicationBuilder.IBlazorApplicationBuilder.ObjectSpaceProviders?v=22.1)  property to register Object Space Providers instead of the  `XafApplication.CreateDefaultObjectSpaceProvider`  method or  `XafApplication.CreateCustomObjectSpaceProvider`  event. Refer to the following help topic for more information on how to do this:  [Integrate Application Builders into Existing Applications](https://docs.devexpress.com/eXpressAppFramework/403980/application-shell-and-base-infrastructure/application-solution-components/integrate-application-builders-into-existing-applications?v=22.1).

We strongly recommend this because the use of the  `XafApplication.CreateDefaultObjectSpaceProvider`  method and  `XafApplication.CreateCustomObjectSpaceProvider`  event conflicts with  `IObjectSpaceFactory`  and  `IObjectSpaceProviderFactory`  service usage.

The use of  [IObjectSpaceFactory](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.IObjectSpaceFactory?v=22.1)  instead of  `XafApplication`‘s members also improves the performance of your application because the application instance is not created in this case.

## Examples

### Object Space

To create an Object Space in an ASP.NET Core application, inject the  [IObjectSpaceFactory](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.IObjectSpaceFactory?v=22.1)  service. Note that this service ensures if a user is logged on. If not, it throws an authorization exception. To avoid this exception, you can use the following techniques:

-   Use the  `INonSecuredObjectSpaceFactory`  service instead of  `IObjectSpaceFactory`.
-   Use another way to ensure if a user is logged on (for example, use  `AuthorizationPolicyBuilder.RequireXafAuthentication`  with  `AuthorizeAttribute`.


```csharp
using DevExpress.ExpressApp;
using DevExpress.ExpressApp.Core;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.OData.Routing.Controllers;

namespace MySolution.WebApi {
    [Route("api/[controller]")]
    [ApiController]
    [Authorize]
    public class CustomEndpointController : ControllerBase {
        IObjectSpaceFactory objectSpaceFactory;
        public CustomEndpointController(IObjectSpaceFactory objectSpaceFactory) {
            this.objectSpaceFactory = objectSpaceFactory;
        }
        [HttpGet]
        public IActionResult Get() {
            using IObjectSpace newObjectSpace = objectSpaceFactory.CreateObjectSpace<Contact>();
            // ...
            return Ok();
        }
        //...
    }
}

```

### Security System

To access the Security System in an ASP.NET Core application, inject the  [ISecurityProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityProvider?v=22.1)  service. Note that this service ensures if a user is logged on. If not, it throws an authorization exception. To avoid this exception, you can use the following techniques:

-   Use the  `ISecurityStrategyBase`  service instead of  `ISecurityProvider`  if you do not need to operate with an authenticated user object. This service does not ensure if a user is logged on or not, so the current user object might not be available here.
-   Use another way to ensure if a user is logged on (for example, use  `AuthorizationPolicyBuilder.RequireXafAuthentication`  with  `AuthorizeAttribute`.

These workarounds do not guarantee that you will not receive authentication exceptions, even if you specify the correct user credentials.



```csharp
using DevExpress.ExpressApp;
using DevExpress.ExpressApp.Security;
using Microsoft.AspNetCore.Authorization;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.OData.Routing.Controllers;
using MySolution.Module.BusinessObjects;

namespace MySolution.WebApi {
    [Route("api/[controller]")]
    [ApiController]
    [Authorize]
    public class CustomEndpointController : ControllerBase {
        ISecurityProvider securityProvider;
        public CustomEndpointController(ISecurityProvider securityProvider) {
            this.securityProvider = securityProvider;
        }
        [HttpGet]
        public IActionResult Get() {
            ISecurityStrategyBase security = securityProvider.GetSecurity();
            var userId = security.UserId; 
            // ...
            return Ok();
        }
        //...
    }
}

```

### Caption Helper

The  [Caption Helper](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Utils.CaptionHelper?v=22.1)  class allows you to get localized captions for XAF  [Controllers](https://docs.devexpress.com/eXpressAppFramework/112621/ui-construction/controllers-and-actions/controllers?v=22.1)  and  [Razor Components](https://docs.devexpress.com/eXpressAppFramework/113610/ui-construction/using-a-custom-control-that-is-not-integrated-by-default/using-a-custom-control-that-is-not-integrated-by-default?v=22.1)  that are shown in XAF  [Views](https://docs.devexpress.com/eXpressAppFramework/112611/ui-construction/views?v=22.1). XAF initializes the Application Model of this class on requests to standard XAF pages. To get captions with other requests (middleware, Web API method, and so on), use the  [ISharedCaptionHelperProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.AspNetCore.Services.Localization.ISharedCaptionHelperProvider?v=22.1)  service.

This service uses a shared Application Model and does not return user-specific localized strings from a user Model Differences Storage. If your application does not store different captions for different users in the Application Model, use the  [ISharedCaptionHelperProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.AspNetCore.Services.Localization.ISharedCaptionHelperProvider?v=22.1)  service as a unified way to get localized captions.

The  [Instance](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Utils.CaptionHelper.Instance?v=22.1)  returns a  `CaptionHelperImplementorBase`  instance to use on other platforms such as Win and Web.



```
using DevExpress.ExpressApp.AspNetCore.Services.Localization;
using DevExpress.ExpressApp.Utils;
using Microsoft.AspNetCore.Mvc;

namespace MySolutionName.Module.Blazor.Controllers {
    public class CustomLocalizationController : ControllerBase {
        internal ISharedCaptionHelperProvider sharedCaptionHelperProvider;

        public CustomLocalizationController(ISharedCaptionHelperProvider sharedCaptionHelperProvider) {
            this.sharedCaptionHelperProvider = sharedCaptionHelperProvider;
        }

        [HttpGet]
        public string GetActionCaption(string actionName) {
            CaptionHelperImplementorBase helper = sharedCaptionHelperProvider.GetCaptionHelper();
            return helper.GetActionCaption(actionName);
        }
    }
}
```


# Execute Custom Operations on Endpoint Requests


You can execute custom code when a Web API service processes HTTP requests.

Create a custom  **IDataService**  class. This class should contain a corresponding method for each endpoint.



```csharp
using DevExpress.Data.Filtering;
using DevExpress.ExpressApp.Core;
using DevExpress.ExpressApp.DC;
using DevExpress.ExpressApp.WebApi.Services;
// ...
public class CustomDataService : IDataService {
    private readonly DataService internalDataService;
    public CustomDataService(IObjectSpaceFactory objectSpaceFactory, ITypesInfo typesInfo) {
        internalDataService = new DataService(objectSpaceFactory, typesInfo);
    }
    // POST
    public T CreateObject<T>(IObjectDelta<T> delta) where T : class {
        return internalDataService.CreateObject<T>(delta);
    }
    // POST with /key and associated property
    public void CreateRef<T>(string key, string navigationProperty, string relatedKey) {
        internalDataService.CreateRef<T>(key, navigationProperty, relatedKey);
    }
    // DELETE
    public T DeleteObject<T>(string key) {
        return internalDataService.DeleteObject<T>(key);
    }
    // DELETE with /key and associated property
    public void DeleteRef<TEntity>(string key, string navigationProperty, string relatedKey = null) {
        internalDataService.DeleteRef<TEntity>(key, navigationProperty, relatedKey);
    }
    // For internal use.
    public IEnumerable<T> GetObjects<T>(CriteriaOperator criteriaOperator) {
        return internalDataService.GetObjects<T>(criteriaOperator);
    }
    // GET
    public IQueryable<T> GetObjectsQuery<T>() {
        return internalDataService.GetObjectsQuery<T>();
    }
    // GET with /key
    public T GetObjectByKey<T>(string key) {
        return internalDataService.GetObjectByKey<T>(key);
    }
    // GET with /key and associated property
    public object GetRef<T>(string key, string navigationProperty) {
        return internalDataService.GetRef<T>(key, navigationProperty);
    }
    // PATCH
    public T PatchObject<T>(string key, IObjectDelta<T> delta) where T : class {
        return internalDataService.PatchObject<T>(key, delta);
    }
    // PUT
    public T UpdateObject<T>(string key, IObjectDelta<T> delta) where T : class {
        return internalDataService.UpdateObject<T>(key, delta);
    }
}

```

Implement the required logic in the endpoint’s method that you wish to change.



```csharp
// GET
public IQueryable<T> GetObjectsQuery<T>() {
    if(typeof(T) == typeof(ApplicationUser)) {
        // Custom logic
    }
    return internalDataService.GetObjectsQuery<T>();
}

// PATCH
public T PatchObject<T>(string key, IObjectDelta<T> delta) where T : class {
    var original = GetObjectByKey<T>(key);
    // Custom logic before modifications
    delta.Patch(original);
    // Custom logic after modifications
    objectSpace.CommitChanges();
    return original;
}
// ...

```

Register  **CustomDataService**  in the  **ConfigureServices**  method after the  **services.AddXafWebApi**  method call.

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
namespace MySolution.WebApi {
    public class Startup {
        // ...
        public void ConfigureServices(IServiceCollection services) {
            // ...
            services.AddXafWebApi(Configuration, options => {
                // ...
            })
            // in XPO applications, uncomment the following line
            // .AddXpoServices(); 
            services.AddScoped<IDataService, CustomDataService>();
        }
        // ...    
    }
}
```


# Customize OData Options


You can customize  [OData](https://docs.microsoft.com/en-us/odata/overview)  options in the  _Startup.cs_  file. Use the  [services.AddControllers().AddOData](https://github.com/OData/AspNetCoreOData#2-basic-usage)  method for this purpose.

## Change the Expansion Depth for Related Business Objects

To specify the  [ODataValidationSettings.MaxExpansionDepth](https://learn.microsoft.com/dotnet/api/microsoft.aspnet.odata.query.odatavalidationsettings.maxexpansiondepth)  option, follow the steps below:

-   Implement a custom  _ODataQueryValidator_  service to set  [MaxExpansionDepth](https://learn.microsoft.com/dotnet/api/microsoft.aspnet.odata.query.odatavalidationsettings.maxexpansiondepth):
    

    
    ```csharp
    using Microsoft.AspNetCore.OData.Query.Validator;
    using Microsoft.AspNetCore.OData.Query;
    // ...
    public class MyODataQueryValidator : ODataQueryValidator {
        public override void Validate(ODataQueryOptions options, ODataValidationSettings validationSettings){
            validationSettings.MaxExpansionDepth = 3;
            base.Validate(options, validationSettings);
        }
    }
    
    ```
    
-   Replace the default  _ODataQueryValidator_  service with the custom service in the  _ConfigureServices_  method:
    
    **File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)
    

    
    ```csharp
    public void ConfigureServices(IServiceCollection services) {
    // ...
    services.AddControllers().AddOData((options, serviceProvider) => {
        options
            .EnableQueryFeatures(100)
            .AddRouteComponents("api/odata", new EdmModelBuilder(serviceProvider).GetEdmModel(), odataServices => {
                odataServices.AddSingleton<ODataQueryValidator, MyODataQueryValidator>();
            });
        });
        // ...
    }
    
    ```
    

## Change an EDM Model Structure using ODataModelBuilder

To customize the OData entity model structure at runtime (change types, properties, actions, etc.), implement the  **DevExpress.ExpressApp.WebApi.Services.IEdmModelCustomizer**  interface in a custom class and manipulate  [ODataModelBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnet.odata.builder.odatamodelbuilder?view=odata-aspnetcore-7.0)  in the CustomizeEdmModel method as needed.

You can register your custom IEdmModelCustomizer implementer after the  `services.AddXafWebApi`  call in the  `ConfigureServices`  method:

**File:**  _MySolution.WebApi\Startup.cs_  (_MySolution.Blazor.Server\Startup.cs_)



```csharp
services.AddXafWebApi(Configuration, options => { /* ... */  }); 
// Add a custom IEdmModelCustomizer.
services.TryAddEnumerable(ServiceDescriptor.Transient<IEdmModelCustomizer, CustomEdmModelCustomizer>());
// OR
// Remove a built-in IEdmModelCustomizer.
// var serviceDescriptor = services.Single(descriptor => descriptor.ImplementationType?.Name == "PersistentAliasEdmModelCustomizer");
// services.Remove(serviceDescriptor);

```

For more information, review the following:

-   [Model builders overview](https://learn.microsoft.com/en-us/odata/webapi/model-builder-abstract);
-   Code of the built-in IEdmModelCustomizer implementers (DateTimeNullableEdmModelCustomizer, PersistentAliasEdmModelCustomizer, etc.) within the DevExpress.ExpressApp.WebApi library sources;
-   Support articles:  [T1096425](https://supportcenter.devexpress.com/ticket/details/t1096425/web-api-the-400-bad-request-error-occurs-when-you-use-properties-with-notmappedattribute)  |  [T1041495](https://supportcenter.devexpress.com/ticket/details/t1041495/web-api-service-how-to-return-or-serialize-a-business-object-in-a-custom-method-endpoint)  |  [T1101266](https://supportcenter.devexpress.com/ticket/details/t1101266/web-api-how-to-create-a-custom-odatacontroller-for-each-business-object-type-to-create).
