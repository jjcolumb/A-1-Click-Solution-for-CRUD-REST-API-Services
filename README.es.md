[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services#readme)
# Crear una nueva aplicación con la API web

Este tema contiene instrucciones paso a paso sobre cómo crear una aplicación con la  **API web**. Para obtener más información sobre  la API web, consulte el tema siguiente:  [Servicio de API web back-end](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1).

1.  Cree una nueva solución en Visual Studio. Seleccione la plantilla de proyecto  **DevExpress v22.1  XAF Template Gallery**  y haga clic en  **Siguiente**.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/9c3e13ae-6f59-4de7-91d9-2747d268eb82)

    
2.  Especifique el nombre y la ubicación del nuevo proyecto (solución) y haga clic en  **Crear**.
    
3.  Asegúrese de que la plataforma .**NET Core**  está seleccionada y ejecute el  **Asistente para soluciones XAF**.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/92194933-7937-401f-8a70-0bc3cb991f8c)

    
4.  En el Asistente para soluciones, seleccione  **Servicio (ASP.NET API web principal)**  y otras plataformas que desee agregar a la solución.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/b8d686a6-e27a-476b-8e70-4ee001f02842)

    
5.  Seleccione  **eXpress Persistent Objects**  o  **Entity Framework Core**  ORM para su aplicación y haga clic en  **Siguiente**.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/bf5d9ad5-05c7-4a72-b3e1-c7f8cd244b9f)

    
6.  Elija las opciones de seguridad para su aplicación.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/078339ad-6491-40eb-bd30-08a1decdecf4)

    
    Consulte el tema siguiente para obtener más información:  [Autenticación en proyectos de API web](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    
    Si seleccionó ASP.NET Core Blazor en la página  **Elegir plataformas de destino**, también puede especificar si el servicio API web debe agregarse como un proyecto independiente o integrarse en el proyecto de aplicación Blazor:
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/2bc7f829-6aff-4ed8-ba83-d307a475e061)

    
7.  [Cree puntos de enlace y pruebe la API web](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).


# Agregar un proyecto de API web a una solución existente


Este tema contiene instrucciones paso a paso sobre cómo agregar un proyecto de  [API web](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  a una aplicación .NET Core.

1.  Use el  [Asistente para soluciones](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  para agregar un proyecto de API web a la aplicación. Haga clic con el botón secundario en la solución en el  **Explorador de soluciones**  y elija  **Agregar elemento DevExpress | Nuevo proyecto...**.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/dc5f054f-b67a-4d8d-a995-b3c4e8beefa8)

    
2.  Seleccione la plataforma .**NET Core**  y ejecute el  **Asistente para soluciones XAF**.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/a41c3f52-14a0-48a8-84cd-69bf5e97e9d7)

3.  Elija la opción  **ASP.NET Core Web API Service**  y especifique el nombre del proyecto.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/e218d61d-197f-41df-8e59-b09902f78ce8)

    
4.  Seleccione  **eXpress Persistent Objects**  o  **Entity Framework Core**  ORM para su aplicación y haga clic en  **Siguiente**.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/8c7505cd-aeb8-4f2a-96e6-0c7692589475)

    
5.  _Opcional._  Elija las opciones de seguridad de la aplicación y haga clic en  **Finalizar**. Consulte el tema siguiente para obtener más información:  [Autenticación en proyectos de API web](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/a7d22fdd-3919-46e0-a1b0-ffacad6c4627)

    
    El asistente agrega el proyecto de API web a la aplicación.
    
    Si usa el algoritmo Sha512 para cifrar contraseñas en la aplicación, establezca la propiedad  **PasswordCryptographer.SupportLegacySha512**  en el archivo  _Startup.cs_  del proyecto de API web para compatibilidad con versiones anteriores:`true`
    
    **Archivo:**  _MySolution.WebApi\Startup.cs_
    

    
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
    
6.  [Cree puntos de enlace y pruebe la API web](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).


# Agregar el servicio API web a un proyecto de Blazor Server


En este tema se describe cómo agregar el servicio  [API web](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  a un proyecto de Blazor Server.

1.  Instale los siguientes paquetes NuGet en el proyecto Blazor Server (_MySolution.Blazor.Server_):
    
    -   **DevExpress.ExpressApp.WebApi**
    -   **Swashbuckle.AspNetCore**
    -   **DevExpress.ExpressApp.WebApi.Xpo**: solo en aplicaciones XPO
    
    Consulte el tema siguiente para obtener más información sobre cómo instalar paquetes NuGet de DevExpress:  [Instalar controles de DevExpress mediante paquetes NuGet.](https://docs.devexpress.com/GeneralInformation/115912/installation/install-devexpress-controls-using-nuget-packages?v=22.1)
    
2.  Use el código siguiente para configurar servicios para la  **API web**:
    
    **Archivo:**  _MySolution.Blazor.Server\Startup.cs_
    

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
    
3.  _Opcional._  Configure las opciones de autenticación. La  **API web**  admite todas las técnicas de  [autenticación](https://docs.microsoft.com/en-us/aspnet/core/security/authentication) estándar ASP.NET Core. Consulte el tema siguiente para obtener más información:  [Autenticación en proyectos de API web](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    
4.  [Cree puntos de enlace y pruebe la API web](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).


# Agregar extremos CRUD y consumir la API web

En este tema se describe cómo crear extremos y probar el servicio  [API web](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1). Consulte los siguientes temas para obtener información sobre cómo crear un proyecto con la  **API web**:

-   [Cree una nueva aplicación con la API web](https://docs.devexpress.com/eXpressAppFramework/403401/backend-web-api-service/create-new-application-with-web-api-service?v=22.1).
-   [Agregue un proyecto de API web a una solución existente](https://docs.devexpress.com/eXpressAppFramework/403561/backend-web-api-service/add-web-api-to-blazor-server?v=22.1).
-   [Agregue el servicio API web a un proyecto de servidor Blazor](https://docs.devexpress.com/eXpressAppFramework/403561/backend-web-api-service/add-web-api-to-blazor-server?v=22.1).

## Crear extremos para objetos de negocio

En el archivo  _Inicio.cs_, agregue o busque los  [servicios. Llamada al método AddXafWebApi](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.WebApi.Services.WebApiStartupExtensions.AddXafWebApi(IServiceCollection--IConfiguration--Action-WebApiOptions-)?v=22.1)  y utilice el método  **BusinessObject**  para crear extremos para objetos de negocio. El código siguiente crea extremos para los objetos de negocio  **ApplicationUser**  y  **Contact**:

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



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

## Exponer u ocultar propiedades de objeto de negocio

ASP.NET API web  [principal/OData](https://learn.microsoft.com/en-us/odata/webapi/getting-started) expone propiedades de clase empresarial pública de tipos simples/de valor con un configurador (grabable) en una respuesta de API web. Nuestro servicio de API web expone adicionalmente propiedades XPO calculadas de solo lectura de tipos simples/de valor sin un configurador (solo lectura) marcado con  [PersistentAliasAttribute](https://docs.devexpress.com/XPO/DevExpress.Xpo.PersistentAliasAttribute?v=22.1).

Para ocultar las propiedades de clase empresarial de una respuesta de la API web en tiempo de diseño, decórelas con  [IgnoreDataMemberAttribute](https://learn.microsoft.com/en-us/dotnet/api/system.runtime.serialization.ignoredatamemberattribute?view=net-6.0) , si es necesario.

ASP.NET API web principal/OData incluye propiedades complejas de clase, referencia y colección en una respuesta de API web de forma predeterminada. Para incluir propiedades complejas de clase, referencia y clase empresarial de colección en una respuesta de API web, use las opciones de  [consulta de  OData](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-overview):

-   [Obtener un objeto de referencia](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1#get-a-reference-object)
-   [Obtener una colección asociada](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1#get-an-associated-collection)
-   [Cambiar la profundidad de expansión de los objetos de negocio relacionados](https://docs.devexpress.com/eXpressAppFramework/403719/backend-web-api-service/use-odata-to-send-requests/customize-odata-options?v=22.1)

Para obtener personalizaciones avanzadas de la estructura del modelo de entidad de OData, consulte  [Cambiar una estructura de modelo EDM mediante ODataModelBuilder](https://docs.devexpress.com/eXpressAppFramework/403719/backend-web-api-service/use-odata-to-send-requests/customize-odata-options?v=22.1).

## Usar la interfaz de usuario de Swagger para probar la API web

Si la solución incluye un proyecto de  **API web**, haga clic con el botón secundario en el proyecto en el  **Explorador de soluciones**  y elija  **Depurar | Inicie una nueva instancia**  para ejecutar el proyecto de  **API web**. Un navegador muestra la página con los puntos finales disponibles.

Si la solución incluye un proyecto de inicio  **de Blazor Server**  que contiene la  **API web**, ejecute la aplicación. Agregue  _/swagger_  a la dirección de la aplicación (por ejemplo,  _https://localhost:44318/swagger_  ) y presione  _Entrar_  para mostrar una página con extremos disponibles.

Consulte el siguiente vínculo para obtener más información sobre la interfaz de usuario de la página:  [Swagger UI](https://swagger.io/tools/swagger-ui/) .

La configuración predeterminada inicia el servicio API web en diferentes puertos según el proyecto:


**Proyecto de API web**

Puerto predeterminado: 44319

Ejemplo: https://localhost:44319/swagger

----
**Proyecto Blazor Server**

Puerto predeterminado: 44318

Ejemplo: https://localhost:44318/swagger

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/063b6fa9-6317-468d-ab9f-d7b50a4a3822)


Pruebe la API web. Expanda el extremo  **GET ApplicationUser**  y haga clic en el botón  **Pruébelo**. Se muestra el botón  **Ejecutar**. Haga clic en este botón para ver el resultado.

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/8b16b0ae-e382-4d6a-b51b-de8b1ff78aea)


## Usar la herramienta Postman para probar la API web

También puede usar la herramienta  [Postman](https://learning.postman.com/docs/getting-started/installation-and-updates/) para probar la API web. La herramienta Postman es más flexible y permite enviar solicitudes complejas con  [parámetros](https://learning.postman.com/docs/sending-requests/requests/#sending-parameters) al servicio  **API web**. Consulte el siguiente enlace para obtener más información sobre cómo utilizar esta herramienta:  [Enviando su primera solicitud](https://learning.postman.com/docs/getting-started/sending-the-first-request/).

>PROPINA
Para probar el servicio  **API web** hospedado en  _localhost_, instale el agente de escritorio de Postman  como se describe en el tema siguiente: Instalación del agente [de escritorio de Postman](https://learning.postman.com/docs/getting-started/installation-and-updates/#installing-the-postman-desktop-agent).

La imagen siguiente muestra una solicitud al objeto de negocio  _Contact_  filtrado por  _FirstName_  en la interfaz de usuario web de Postman ():`https://web.postman.co/home`

![Usar Postman para crear una solicitud de API web](https://docs.devexpress.com/eXpressAppFramework/images/web-api-postman.png?v=22.1)

Consulte los siguientes temas para obtener más información sobre las opciones de consulta  [de OData](https://docs.microsoft.com/en-us/odata/overview):

-   [Información general sobre  las opciones de consulta](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-overview)
-   [Uso de opciones de  consulta](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-usage)

Si habilita la autenticación para el servicio  **API web**, especifique la configuración de autorización para la herramienta Postman. Consulte el tema siguiente para obtener más información:  [Especificación de detalles  de autorización](https://learning.postman.com/docs/sending-requests/authorization/#specifying-authorization-details)  . Si el servicio  **API web**  usa el token JWT XAF del extremo "Autenticar", cópielo desde la página de la interfaz de usuario de Swagger como se describe en la siguiente sección:  [Use la interfaz de usuario de Swagger para probar la autenticación JWT](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1#use-the-swagger-ui-to-test-the-jwt-authentication).

## Consumir la API web desde aplicaciones .NET

Consulte el siguiente artículo de ayuda para encontrar el ejemplo:  [Realizar solicitudes HTTP a la API web desde aplicaciones .NET.](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1)


# Realizar solicitudes HTTP a la API web desde aplicaciones .NET


Puede enviar solicitudes a un servicio  [API web](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1)  desde cualquier  [aplicación .NET con la biblioteca HttpClient.](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/console-webapiclient)  Use la sintaxis de  [OData](https://docs.microsoft.com/en-us/odata/overview) para generar solicitudes. Consulte los siguientes temas para obtener más información sobre las opciones de consulta  [de OData](https://docs.microsoft.com/en-us/odata/overview):

-   [Información general sobre  las opciones de consulta](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-overview)
-   [Uso de opciones de  consulta](https://docs.microsoft.com/en-us/odata/concepts/queryoptions-usage)

Los ejemplos siguientes envían solicitudes al servicio API web disponible en la siguiente dirección: . `https://localhost:44319/`

## Obtener un token de autenticación JWT

Para obtener el token de  [autenticación JWT](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1)  para otras solicitudes de datos, envíe una solicitud al siguiente extremo: . En el ejemplo siguiente se utiliza "Sam" como nombre de usuario y una contraseña vacía:`api/Authentication/Authenticate`


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

## Operar con Business Objects

### [#](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#get-business-objects)Obtener objetos de negocio

El código siguiente recupera los campos  _LastName_  y  _Email_  del objeto de negocio  _Employee_  donde  _FirstName_  es igual a "Mary":



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

Resultado

### Crear un objeto de negocio

El código siguiente agrega una nueva instancia de  _Employee_  con el campo  _FirstName_  establecido en "Mary" y el campo  _LastName_  establecido en "Gordon":


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

**Resultado**  (el valor  _dataResponse.StatusCode_): 201 Creado

### Obtener un objeto de referencia

Puede utilizar una de las siguientes técnicas:

[Técnica 1 (expandir parámetro de consulta)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-1-expand-query-parameter)

El parámetro de consulta OData  [$expand](https://docs.microsoft.com/en-us/odata/webapi/odata-expand) permite obtener un objeto de negocio de referencia  **junto con**  el objeto principal.

[Técnica 2 (Ref Endpoint)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-2-ref-endpoint)

El extremo  [$ref](https://docs.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/odata-v4/entity-relations-in-odata-v4#getting-related-entities) permite obtener un objeto de negocio de referencia  **sin**  su objeto principal.

#### Técnica 1 (expandir parámetro de consulta)

En el ejemplo siguiente se utiliza  **$expand**  para obtener un objeto  _Employee_  con su objeto  _Department_  relacionado:



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

Resultado


```json
{"@odata.context":"https://localhost:44319/api/odata/$metadata#Employee(LastName,Email,Department())",
 "value":[{"LastName":"Tellitson",
           "Email":"Mary_Tellitson@example.com",
           "Department":{
                "Oid":"6eff292f-f871-4237-a22c-8a50aa747ea3",
                "Title":"Development Department",
                "Description":"The Information Technology Department manages the company's information infrastructure and online assets.",
                "Location":"Building 2",
                "Office":"205"}
        }]
}

```

El parámetro  **$expand**  se puede aplicar a más de un nivel de objetos de negocio relacionados. En el ejemplo siguiente se recupera una cadena de datos que consta de dos objetos de negocio relacionados:

```csharp
// ...
string requestAddress = "https://localhost:44319/api/odata/Department";
var departments = await httpClient.GetStringAsync($"{requestAddress}?$select=Title&$expand=Employees($select=FirstName,LastName;$expand=Tasks($select=Subject))");
// ...

```

Resultado



```json
{"@odata.context": "https://localhost:44319/api/odata/$metadata#Department(Title,Employees(FirstName,LastName,Tasks(Subject)))",
 "value": [{ "Title": "Human Resources",
             "Employees": [{ "FirstName": "Angela",
                             "LastName": "Gross",
                             "Tasks": [{ "Subject": "Create 2022 R&D Plans"},
                                       { "Subject": "Submit D&B Number to ISP for Credit Approval"},
                                       { "Subject": "Deliver R&D Plans for 2022"}]
                           },
                           { "FirstName": "Barbara",
                             "LastName": "Faircloth",
                             "Tasks": [{ "Subject": "Subject": "Deliver R&D Plans for 2022"},
                                       { "Subject": "Submit D&B Number to ISP for Credit Approval"},
                                       { "Subject": "Create 2022 R&D Plans"}]
                            }]
           },
          { "Title": "Purchasing",
            "Employees": [{ "FirstName": "Ernest",
                            "LastName": "Webb",
                            "Tasks": [{ "Subject": "Submit D&B Number to ISP for Credit Approval"},
                                       { "Subject": "Deliver R&D Plans for 2022"}]
                           },
                           ... 
                         ]
          }]
}

```

La  [profundidad  de expansión máxima](https://docs.microsoft.com/en-us/odata/webapi/odata-expand#expand-depth)  predeterminada es igual a dos. Puede cambiar este parámetro como se describe en el tema siguiente:  [Cambiar la profundidad de expansión de los objetos de negocio relacionados](https://docs.devexpress.com/eXpressAppFramework/403719/backend-web-api-service/use-odata-to-send-requests/customize-odata-options?v=22.1#change-the-expansion-depth-for-related-business-objects).

#### Técnica 2 (Ref Endpoint)

En el ejemplo siguiente se obtiene el objeto  _de referencia Departamento_  del  _empleado_:

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

Resultado



```json
{"@odata.context":"https://localhost:44319/api/odata/$metadata#Department/$entity",
"ID":1,
"Title":"Development Department",
"Office":"205","Location":"Building 2",
"Description":"The Information Technology Department manages the company's information infrastructure and online assets."}

```

### Obtener una colección asociada

Puede utilizar una de las siguientes técnicas:

[Técnica 1 (expandir parámetro de consulta)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-1-expand-query-parameter-1)

El parámetro de consulta OData  [$expand](https://docs.microsoft.com/en-us/odata/webapi/odata-expand) permite obtener objetos de una colección asociada  **junto con**  el objeto principal.

[Técnica 2 (Ref Endpoint)](https://docs.devexpress.com/eXpressAppFramework/403715/backend-web-api-service/use-odata-to-send-requests/use-http-client-to-access-web-api?v=22.1&p=netframework#technique-2-ref-endpoint-1)

El extremo  [$ref](https://docs.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/odata-v4/entity-relations-in-odata-v4#getting-related-entities) permite obtener objetos de una colección asociada  **sin**  su objeto principal.

#### Técnica 1 (expandir parámetro de consulta)

En el ejemplo siguiente se obtiene  _LastName_,  _Email_  y la colección  _Tasks_  relacionada del objeto de negocio  _Employee_  donde  _FirstName_  es igual a "Mary":


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

Resultado



```json
{"@odata.context":"https://localhost:44319/api/odata/$metadata#Employee(LastName,Email,Tasks())",
 "value":[{"LastName":"Tellitson",
           "Email":"Mary_Tellitson@example.com",
           "Tasks":[{"Oid":"b958f20a-118d-4af0-b249-94445608549d",
                     "Subject":"2022 Brochure Designs",
                     "DueDate":"2022-01-15T00:00:00+04:00",
                     "StartDate":"0001-01-01T00:00:00Z",
                     "Status":"Deferred",
                     "PercentCompleted":0,
                     "Priority":"Normal"},
                    {"Oid":"7de87fc8-4dc0-4b76-82b3-18dffdc61ba4",
                     "Subject":"Review Benefits",
                     "DueDate":"2021-10-02T00:00:00+04:00",
                     "StartDate":"2021-09-12T00:00:00+04:00",
                     "Status":"Completed",
                     "PercentCompleted":100,
                     "Priority":"Normal"},
                    {"Oid":"67d36cda-a261-489f-afa9-c8ac43e1c2ea",
                     "Subject":"Lunch Potluck",
                     "DueDate":"2021-10-03T00:00:00+04:00",
                     "StartDate":"0001-01-01T00:00:00Z",
                     "Status":"Deferred",
                     "PercentCompleted":0,
                     "Priority":"Low"}
                    ]
        }]
}

```

#### Técnica 2 (Ref Endpoint)

En  _el ejemplo_  siguiente se obtiene la colección  _Employee's Tasks_:



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

Resultado


```json
{"@odata.context":"https://localhost:44319/api/odata/$metadata#DemoTask",
"value":[
    {
        "ID":8,
        "Subject":"Approve Overtime Pay",
        "Description":"Brett, the overtime I submitted was not paid and I'm being told it was not approved. I thought you approved this. What is the problem?\r\nBrett Wade: I did approve it. It was error in payroll. Trying to figure it out.",
        "DueDate":"2022-04-22T00:00:00+04:00",
        "StartDate":"2022-03-28T00:00:00+04:00",
        "PercentCompleted":0,
        "Status":"Completed",
        "Priority":"Normal",
        "ActualWorkHours":15,
        "EstimatedWorkHours":19
    },
    {
        "ID":9,
        "Subject":"Move Inventory to New Warehouse",
        "Description":"Robin, you are point person to get all inventory moved to the new warehouse location. You can hire temp workers if needed.",
        "DueDate":"2022-04-24T00:00:00+04:00",
        "StartDate":null,
        "PercentCompleted":0,
        "Status":"NotStarted",
        "Priority":"Low",
        "ActualWorkHours":0,
        "EstimatedWorkHours":10
    },
    {
        "ID":10,
        "Subject":"Shipping Label Artwork",
        "Description":"Kevin wants new shipping labels and I cannot print them without the artwork from your team. Can you please hurry and send it to me.\r\nMorgan Kennedy: Send me the specs and I will work on it when I can.",
        "DueDate":"2022-04-24T00:00:00+04:00",
        "StartDate":"2022-04-19T00:00:00+04:00",
        "PercentCompleted":0,
        "Status":"InProgress",
        "Priority":"High",
        "ActualWorkHours":19,
        "EstimatedWorkHours":12
    }
]}

```

### Asignar un objeto a una propiedad de referencia

En el ejemplo siguiente se establece la propiedad de referencia  _Employee's_  Department  en el objeto  _Department_:

#### Técnica 1 (En el cuerpo)



```csharp
string requestAddress = "https://localhost:44318/api/odata/Employee/1";
string jsonBody = @"{ ""Department"": ""1""}";
// or
// string jsonBody = @"{ ""Department"": { ""Oid"": ""1"" }}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido

#### Técnica 2 (Ref Endpoint)



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1/Department/$ref";
string jsonBody = "{\"@odata.id\":\"https://localhost:44319/api/odata/Department/1\"}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido

### Agregar un objeto a una colección

En  _el ejemplo_  siguiente se agrega el objeto  _DemoTask_  a la colección  _Employee's Tasks_:



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1/Tasks/$ref";
string jsonBody = "{\"@odata.id\":\"https://localhost:44319/api/odata/DemoTask(1)\"}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PostAsync(requestAddress, content);
Console.WriteLine(response);

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido

### Desvincular un objeto de una propiedad de referencia

En el ejemplo siguiente se quita el valor de la propiedad de referencia del  _departamento_  del  _empleado_:



```csharp
string requestAddress = @"https://localhost:44319/api/odata/Employee/1/Department/$ref?
                          $id=https://localhost:44319/api/odata/Department/1";
// or 
// string requestAddress = @"https://localhost:44319/api/odata/Employee(1)/Department/$ref?
//                           $id=https://localhost:44319/api/odata/Department(1)";
var response = await httpClient.DeleteAsync(requestAddress);
Console.WriteLine(response)

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido

### Quitar un objeto de una colección

En el ejemplo siguiente se quita el objeto  _DemoTask_  _de la colección_  _Employee's Tasks_:



```csharp
string requestAddress = @"https://localhost:44319/api/odata/Employee/1/Tasks/$ref?
                          $id=https://localhost:44319/api/odata/DemoTask/1";
// or 
// string requestAddress = @"https://localhost:44319/api/odata/Employee(1)/Tasks/$ref?
//                           $id=https://localhost:44319/api/odata/DemoTask(1)";
var response = await httpClient.DeleteAsync(requestAddress);
Console.WriteLine(response)

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido

### Modificar un objeto asignado a una propiedad de referencia

En el ejemplo siguiente se modifica el objeto Department asignado a la propiedad de referencia  _Employee's_  _Department_:


```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1";
string jsonBody = @"{ ""Department"": { ""Office"":""504""} }";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido

### Modificar objetos agregados a una colección asociada

En el ejemplo siguiente se modifica el objeto  _DemoTask_  con =1 de la colección  _Employee's Tasks_.  Si la colección no contiene el objeto  _DemoTask_  con esto, se agregará este objeto:`Oid``Oid`



```csharp
string requestAddress = "https://localhost:44319/api/odata/Employee/1";
string jsonBody = @"{ ""Tasks"": [{ ""Oid"": ""1"", ""Subject"":""New subject""} ]}";
StringContent content = new StringContent(jsonBody, Encoding.UTF8, "application/json");
var response = await httpClient.PatchAsync(requestAddress, content);
Console.WriteLine(response);

```

**Resultado**  (el valor  _dataResponse.StatusCode_): 204 Sin contenido


# Autenticación de API web

La  **API web**  admite todas las técnicas de autenticación estándar de  [ASP.NET](https://docs.microsoft.com/en-us/aspnet/core/security/authentication) Core que puede especificar en el archivo MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_).  Consulte el tema siguiente para obtener más información:  [Autenticación](https://docs.devexpress.com/eXpressAppFramework/119064/data-security-and-safety/security-system/authentication?v=22.1).

Si usa el  [Asistente para soluciones](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  para crear un proyecto de  **API web**, habilite la autenticación en la página  **Elegir seguridad**:

![Seleccione la autenticación](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-wizard-auth.png?v=22.1)

Autenticación estándar

El asistente genera código de scaffolding de autenticación  [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token) para la  **API web**.

Autenticación OAuth2

El asistente agrega el código de scaffolding de  [JWT y Azure AD](https://azure.microsoft.com/en-us/products/active-directory/) al archivo  _MySolution.WebApi\appsettings.json._

Windows Active Directory

El asistente agrega el código de scaffolding JWT al archivo MySolution.WebApi\appsettings.json y el código de scaffolding para Windows Active Directory al archivo  _MySolution.WebApi_\_Properties\launchSettings.json._

Consulte los siguientes temas para obtener información sobre cómo configurar el código de scaffolding de autenticación y habilitar manualmente la autenticación:

-   [Configurar la autenticación JWT](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1)
-   [Configuración de la autenticación de Azure de OAuth2](https://docs.devexpress.com/eXpressAppFramework/403505/backend-web-api-service/authentication-in-web-api-applications/enable-oauth2-azure-authentication?v=22.1)


# Configurar la autenticación JWT para la API web


## Habilitar la autenticación en un nuevo proyecto

Use el  [Asistente para soluciones](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  para crear un proyecto de  **API web**  con la autenticación JWT. Si elige Autenticación  **estándar**  en la página  **Elegir seguridad**, el asistente genera código de scaffolding de autenticación  [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token).

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/e63be011-2156-440c-9239-afeacfe44aaa)


Puede reemplazar el valor  **IssuerSigningKey**  generado automáticamente con su clave de firma JWT y cambiar otras configuraciones de JWT en el archivo  _appsettings.json._  Le recomendamos que utilice la herramienta  [Administrador  secreto](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets)  para almacenar la clave de firma. Puede almacenarlo en el archivo  _appsettings.json_  solo con fines de prueba.

**Archivo:**  MySolution.WebApi\appsettings.json (_MySolution.Blazor.Server\__appsettings.json_)



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

Consulte la siguiente sección para obtener información sobre cómo probar la autenticación JWT:  [Use la interfaz de usuario de Swagger para probar la autenticación JWT](https://docs.devexpress.com/eXpressAppFramework/403504/backend-web-api-service/authentication-in-web-api-applications/enable-jwt-authentication?v=22.1&p=netframework#use-the-swagger-ui-to-test-the-jwt-authentication).

## Habilitar la autenticación en un proyecto existente

Para agregar la autenticación JWT a un proyecto existente de  **API web**  o  **Blazor Server**, siga los pasos a continuación.

### Paso 1. Instalar los paquetes NuGet necesarios

Instale los siguientes paquetes NuGet en los proyectos MySolution.WebApi (_MySolution.Blazor.Server) y MySolution.Module_:

-   **DevExpress.ExpressApp.Security.AspNetCore**
-   **Microsoft.AspNetCore.Authentication.JwtBearer**
-   **DevExpress.ExpressApp.Security.Xpo**  - en aplicaciones XPO
-   **DevExpress.EntityFrameworkCore.Security**: en aplicaciones EF Core

Consulte el tema siguiente para obtener más información:  [Instalar controles DevExpress mediante paquetes NuGet.](https://docs.devexpress.com/GeneralInformation/115912/installation/install-devexpress-controls-using-nuget-packages?v=22.1)

### Paso 2. Modificar la configuración de la aplicación.  JSON

Agregue la opción  **Jwt**  a la sección  **Autenticación**  en el archivo  _appsettings.json._

**Archivo:**  MySolution.WebApi\appsettings.json (_MySolution.Blazor.Server\__appsettings.json_)



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

El valor  **IssuerSigningKey**  es una clave generada automáticamente. Puede reemplazarlo con su clave de firma JWT. Puede almacenarlo en el archivo  _appsettings.json_  solo con fines de prueba. Le recomendamos que utilice la herramienta  [Administrador  secreto](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets)  para almacenar la clave de firma.

### Paso 3. Modificar inicio.  .cs

Agregue el código siguiente al método  **ConfigureServices**  para habilitar la autenticación:

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



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

### Paso 4. Agregar un servicio de autenticación JWT

Puede implementar su propio servicio JWT o usar el servicio JWT que genera el  [Asistente para soluciones](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1). Puede encontrar el código de servicio generado automáticamente a continuación. Para usar este servicio JWT, cree la carpeta  _JWT_  en el proyecto MySolution.WebApi (_MySolution.Blazor.Server_) y agregue el archivo  _AuthenticationController.cs_  a esta carpeta_._

**Archivo:**  MySolution.WebApi\JWT\AuthenticationController.cs (_MySolution.Blazor.Server\JWT\AuthenticationController__.cs_)



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

### Paso 5. Agregar el usuario de la aplicación y la información de inicio de sesión del usuariode la aplicaciónObjetos de negocio

XAF requiere los objetos de negocio  _ApplicationUser_  y  _ApplicationUserLoginInfo_  para almacenar información de usuario. Agregue estos objetos de negocio al proyecto  _MySolution.Module_  como se describe en el  _paso 1_  de la siguiente sección:  [Usar proveedores de autenticación de Active Directory y OAuth2 en aplicaciones de ASP.NET Core Blazor: pasos comunes](https://docs.devexpress.com/eXpressAppFramework/402197/data-security-and-safety/security-system/authentication/oauth-and-custom-authentication/active-directory-and-oauth2-authentication-providers-in-blazor-applications?v=22.1#common-steps).

## Usar la interfaz de usuario de Swagger para probar la autenticación JWT

1. Si la solución incluye un proyecto de  **API web**, haga clic con el botón secundario en el proyecto en el  **Explorador de soluciones**  y elija  **Depurar | Inicie una nueva instancia**  para ejecutar el proyecto de  **API web**. Un navegador muestra la página con los puntos finales disponibles.

Si la solución incluye un proyecto de inicio  **de Blazor Server**  con la  **API web**, ejecute la aplicación. Agregue  _/swagger_  a la dirección de la aplicación (por ejemplo,  _https://localhost:44318/swagger_  ) y presione  _Entrar_  para mostrar una página con extremos disponibles.

Consulte el siguiente vínculo para obtener más información sobre la interfaz de usuario de la página:  [Swagger UI](https://swagger.io/tools/swagger-ui/) .

2.  Expanda el extremo  **Post Authentication**  y haga clic en el botón  **Pruébelo**.
    
3.  En el formulario que se muestra, introduzca el nombre de usuario y la  **contraseña**  de un  **usuario**  autorizado. En una aplicación de plantilla, utilice  _Admin_  como nombre de usuario y una cadena vacía como contraseña.
    
4.  Copie la clave pública del  _cuerpo de la respuesta_, haga clic en el botón  ![Authorize button](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-authorize-button.png?v=22.1)  **Autorizar**  para abrir el formulario  **Autorizaciones disponibles**  y pegue la clave pública en el editor de  **valores**  para habilitar la autenticación JWT.
    

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/fb6a3db3-9888-44dc-b64a-c92c1ad6c173)


Consulte el tema siguiente para obtener información sobre cómo crear extremos de API web:  [Crear extremos y probar la API web](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).


# Configuración de la autenticación de Azure OAuth2 para la API web


La  **API web**  admite la autenticación de Azure OAuth2. Para usarlo,  [configure](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-create-new-tenant) un inquilino de Azure Active Directory (Azure AD). Después de obtener un inquilino,  [registre](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app) la  **API web**  con la plataforma de identidad de Microsoft. Cuando configure las opciones de plataforma para la  **API**  web, seleccione  _Aplicación de una sola página_  como tipo de  **aplicación web**  y establezca el siguiente  **URI de redireccionamiento**:  _https://localhost:44318/swagger/oauth2-redirect.html_.

## Habilitar la autenticación en un nuevo proyecto

Use el  [Asistente para soluciones](https://docs.devexpress.com/eXpressAppFramework/113624/installation-upgrade-version-history/visual-studio-integration/solution-wizard?v=22.1)  para crear un proyecto de  **API web**. Habilite la autenticación de Azure OAuth2 en la página  **Elegir seguridad**:

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/6acdb834-4962-460e-84ed-b672c0640ad9)


El asistente genera código de scaffolding de autenticación  [de Azure AD](https://azure.microsoft.com/en-us/products/active-directory/).

Actualice el código generado de la siguiente manera:

1.  Especifique la configuración de  [Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-create-new-tenant) en la sección "_Autenticación"_  del archivo  _appsettings.json_:
    
    **Archivo:**  MySolution.WebApi\appsettings.json (_MySolution.Blazor.Server\__appsettings.json_)
    

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
    
2.  Configure los ámbitos según la configuración de Azure. Consulte el siguiente tema para obtener más información:  [Inicio rápido: configurar una aplicación para exponer una API  web](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-configure-app-expose-web-apis).
    
    **Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )
    

    
    ```csharp
        AuthorizationCode = new OpenApiOAuthFlow() {
            // ...
            Scopes = new Dictionary<string, string> {
                { "api://11111111-1111-1111-1111-111111111111/WebApi", "Read WebApi"} 
            }
        }
    
    ```
    
3.  En las  **opciones. Events.OnAuthenticated**  delegate, implemente la lógica de autenticación. El código generado automáticamente asigna un usuario de proveedor de OAuth a un usuario de aplicación. Si este código se adapta a sus necesidades, comente . `return`
    
    Consulte el tema siguiente para obtener más información:  [Cómo: Usar proveedores de autenticación de Active Directory y OAuth2 en aplicaciones ASP.NET Core Blazor](https://docs.devexpress.com/eXpressAppFramework/402197/data-security-and-safety/security-system/authentication/oauth-and-custom-authentication/active-directory-and-oauth2-authentication-providers-in-blazor-applications?v=22.1#google-azure-and-github-providers).
    
    **Archivo:**  MySolution.Blazor.Server\Startup.cs (_MySolution.Blazor.Server\Startup.json_ )
    

    
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
    

Consulte la siguiente sección para obtener información sobre cómo probar la autenticación de Azure de OAuth2:  [Use la interfaz de usuario de Swagger para probar la autenticación de Azure de OAuth2](https://docs.devexpress.com/eXpressAppFramework/403505/backend-web-api-service/authentication-in-web-api-applications/enable-oauth2-azure-authentication?v=22.1&p=netframework#use-the-swagger-ui-to-test-the-oauth2-azure-authentication).

## Habilitar la autenticación en un proyecto existente

Siga los pasos que se indican a continuación para agregar la autenticación de Azure OAuth2 a un proyecto existente de  **API web**  o  **Blazor Server**.

### Paso 1. Instalar los paquetes NuGet necesarios

Instale los siguientes paquetes NuGet:

-   **DevExpress.ExpressApp.Security.Xpo**: a los proyectos  _MySolution.WebApi y MySolution.Module_;
-   **Microsoft.Identity.Web.UI**  - a  _MySolution.WebApi._

Consulte el tema siguiente para obtener más información:  [Instalar controles DevExpress mediante paquetes NuGet.](https://docs.devexpress.com/GeneralInformation/115912/installation/install-devexpress-controls-using-nuget-packages?v=22.1)

### Paso 2. Modificar la configuración de la aplicación.  JSON

Agregue la opción  **AzureAd**  a la sección  **Autenticación**  del archivo  _appsettings.json_  y especifique sus credenciales de Azure AD.

**Archivo:**  MySolution.WebApi\appsettings.json (_MySolution.Blazor.Server\__appsettings.json_)



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

### Paso 3. Modificar inicio.  .cs

Agregue el código siguiente al método  **ConfigureServices**  para habilitar la autenticación:

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



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

Use los métodos AddSecurityDefinition y  **AddSecurityRequirement**  para agregar la autenticación de Azure OAuth2 a la interfaz de usuario de Swagger.

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



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

Además, modifique el método  **UseSwaggerUI**  de la siguiente manera:

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



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

### Paso 4. Agregar el usuario de la aplicación y la información de inicio de sesión del usuariode la aplicaciónObjetos de negocio

XAF requiere los objetos de negocio  _ApplicationUser_  y  _ApplicationUserLoginInfo_  para almacenar información de usuario. Agregue estos objetos de negocio al proyecto  _MySolution.Module_  como se describe en el  _paso 1_  de la siguiente sección:  [Usar proveedores de autenticación de Active Directory y OAuth2 en aplicaciones de ASP.NET Core Blazor: pasos comunes](https://docs.devexpress.com/eXpressAppFramework/402197/data-security-and-safety/security-system/authentication/oauth-and-custom-authentication/active-directory-and-oauth2-authentication-providers-in-blazor-applications?v=22.1#common-steps).

## Usar la interfaz de usuario de Swagger para probar la autenticación de Azure OAuth2

1.  Si la solución incluye un proyecto de  **API web**, haga clic con el botón secundario en el proyecto en el  **Explorador de soluciones**  y elija  **Depurar | Inicie una nueva instancia**  para ejecutar el proyecto de  **API web**. Un navegador muestra la página con los puntos finales disponibles.
    
    Si la solución incluye un proyecto de inicio  **de Blazor Server**  con la  **API web**, ejecute la aplicación. Agregue  _/swagger_  a la dirección de la aplicación (por ejemplo,  _https://localhost:44318/swagger_  ) y presione  _Entrar_  para mostrar una página con extremos disponibles.
    
    Consulte el siguiente vínculo para obtener más información sobre la interfaz de usuario de la página:  [Swagger UI](https://swagger.io/tools/swagger-ui/) .
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/10cf1577-174f-4e44-b28d-a5f88885a1f9)

    
2.  Haga clic en el botón  **Autorizar**:  ![Botón Autorizar](https://docs.devexpress.com/eXpressAppFramework/images/create-web-api-authorize-button.png?v=22.1). En la ventana  **Autorizaciones disponibles**, seleccione un ámbito y haga clic en el botón  **Autorizar**:
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/deec1143-3d4b-4198-b2d7-ffa7aeeed77c)

    
    Consulte el tema siguiente para obtener información sobre cómo crear extremos de API web:  [Crear extremos y probar la API web](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1).


# Crear puntos de conexión personalizados


Puede crear extremos personalizados para el  [servicio API web](https://docs.devexpress.com/eXpressAppFramework/403394/backend-web-api-service?v=22.1).

1.  Haga clic con el botón secundario en el proyecto que contiene un servicio API web y seleccione  **Agregar > nuevo elemento**  en el menú contextual. Elija la plantilla  **API Controller – Empty**  en la ventana invocada.
    
    ![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/6755e566-9dbb-4614-a262-245d3d64ee62)

    
2.  Agregue métodos de extremo personalizados al nuevo Controller (los métodos Get, Post, Put y Delete del ejemplo siguiente).
    
3.  Si desea utilizar la autenticación de API web, decore el nuevo Controller con  [AuthorizeAttribute](https://learn.microsoft.com/dotnet/api/microsoft.aspnetcore.authorization.authorizeattribute) . Consulte el tema siguiente para obtener más información sobre cómo configurar la autenticación:  [Autenticación de API web](https://docs.devexpress.com/eXpressAppFramework/403413/backend-web-api-service/authentication-in-web-api-projects?v=22.1).
    

Código del Controlador:


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
El resultado en  [la interfaz de usuario de Swagger](https://docs.devexpress.com/eXpressAppFramework/403551/backend-web-api-service/test-web-api?v=22.1#use-the-swagger-ui-to-test-the-web-api):

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/0f485357-bbde-4986-a0ac-ff67f93340d7)


# Acceda al espacio de objetos, al sistema de seguridad y al asistente de subtítulos en métodos de extremo personalizados

En este tema se describe cómo obtener acceso a un espacio de objetos, al  [sistema de seguridad](https://docs.devexpress.com/eXpressAppFramework/113366/data-security-and-safety/security-system?v=22.1)  y al  [asistente de subtítulos](https://docs.devexpress.com/eXpressAppFramework/113298/localization?v=22.1)  desde métodos  [de](https://docs.devexpress.com/eXpressAppFramework/113711/data-manipulation-and-business-logic/create-read-update-and-delete-data?v=22.1)  extremo personalizados.

## API útiles

![image](https://github.com/jjcolumb/A-1-Click-Solution-for-CRUD-REST-API-Services/assets/126447472/03de5f6b-6ea4-4f02-89f0-4a209ca12301)


## Prerrequisitos

Si creó la aplicación en v21.2 o anterior, debe utilizar la propiedad  [ObjectSpaceProviders](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Blazor.ApplicationBuilder.IBlazorApplicationBuilder.ObjectSpaceProviders?v=22.1)  de Application Builder para registrar proveedores de espacio de objetos en lugar del método o evento. Consulte el siguiente tema de ayuda para obtener más información sobre cómo hacerlo:  [Integrar Application Builders en aplicaciones existentes](https://docs.devexpress.com/eXpressAppFramework/403980/application-shell-and-base-infrastructure/application-solution-components/integrate-application-builders-into-existing-applications?v=22.1).`XafApplication.CreateDefaultObjectSpaceProvider``XafApplication.CreateCustomObjectSpaceProvider`

Se recomienda encarecidamente esto porque el uso del método y el evento entran en conflicto con el uso del servicio. `XafApplication.CreateDefaultObjectSpaceProvider``XafApplication.CreateCustomObjectSpaceProvider``IObjectSpaceFactory``IObjectSpaceProviderFactory`

El uso de  [IObjectSpaceFactory](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.IObjectSpaceFactory?v=22.1)  en lugar de los miembros de también mejora el rendimiento de la aplicación porque la instancia de la aplicación no se crea en este caso.`XafApplication`

## Ejemplos

### Espacio de objetos

Para crear un espacio de objetos en una aplicación ASP.NET Core, inserte el servicio  [IObjectSpaceFactory](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Core.IObjectSpaceFactory?v=22.1). Tenga en cuenta que este servicio garantiza si un usuario ha iniciado sesión. De lo contrario, produce una excepción de autorización. Para evitar esta excepción, puede utilizar las siguientes técnicas:

-   Utilice el servicio en lugar de . `INonSecuredObjectSpaceFactory``IObjectSpaceFactory`
-   Utilice otra forma de asegurarse de si un usuario ha iniciado sesión (por ejemplo, utilice con .`AuthorizationPolicyBuilder.RequireXafAuthentication``AuthorizeAttribute`



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

### Sistema de seguridad

Para tener acceso al sistema de seguridad en una aplicación ASP.NET Core, inserte el servicio  [ISecurityProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Security.ISecurityProvider?v=22.1). Tenga en cuenta que este servicio garantiza si un usuario ha iniciado sesión. De lo contrario, produce una excepción de autorización. Para evitar esta excepción, puede utilizar las siguientes técnicas:

-   Utilice el servicio en lugar de si no necesita operar con un objeto de usuario autenticado. Este servicio no garantiza si un usuario ha iniciado sesión o no, por lo que es posible que el objeto de usuario actual no esté disponible aquí.`ISecurityStrategyBase``ISecurityProvider`
-   Utilice otra forma de asegurarse de si un usuario ha iniciado sesión (por ejemplo, utilice con .`AuthorizationPolicyBuilder.RequireXafAuthentication``AuthorizeAttribute`

Estas soluciones provisionales no garantizan que no recibirá excepciones de autenticación, incluso si especifica las credenciales de usuario correctas.



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

### Ayudante de subtítulos

La clase  [auxiliar de subtítulos permite obtener subtítulos](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Utils.CaptionHelper?v=22.1)  localizados para  [controladores](https://docs.devexpress.com/eXpressAppFramework/112621/ui-construction/controllers-and-actions/controllers?v=22.1)  XAF y  [componentes Razor que](https://docs.devexpress.com/eXpressAppFramework/113610/ui-construction/using-a-custom-control-that-is-not-integrated-by-default/using-a-custom-control-that-is-not-integrated-by-default?v=22.1)  se muestran en  [vistas](https://docs.devexpress.com/eXpressAppFramework/112611/ui-construction/views?v=22.1)  XAF. XAF inicializa el modelo de aplicación de esta clase en solicitudes a páginas XAF estándar. Para obtener subtítulos con otras solicitudes (middleware, método de API web, etc.), use el servicio  [ISharedCaptionHelperProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.AspNetCore.Services.Localization.ISharedCaptionHelperProvider?v=22.1).

Este servicio utiliza un modelo de aplicación compartido y no devuelve cadenas localizadas específicas del usuario desde un almacenamiento de diferencias de modelo de usuario. Si la aplicación no almacena subtítulos diferentes para diferentes usuarios en el modelo de aplicación, use el servicio  [ISharedCaptionHelperProvider](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.AspNetCore.Services.Localization.ISharedCaptionHelperProvider?v=22.1)  como una forma unificada de obtener subtítulos localizados.

La instancia devuelve una  [instancia](https://docs.devexpress.com/eXpressAppFramework/DevExpress.ExpressApp.Utils.CaptionHelper.Instance?v=22.1)  para usarla en otras plataformas, como Win y Web.`CaptionHelperImplementorBase`



```csharp
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


# Ejecutar operaciones personalizadas en solicitudes de endpoint


Puede ejecutar código personalizado cuando un servicio API web procesa solicitudes HTTP.

Cree una clase  **IDataService**  personalizada. Esta clase debe contener un método correspondiente para cada extremo.



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

Implemente la lógica requerida en el método del punto final que desea cambiar.



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

Registre  **CustomDataService**  en el método  **ConfigureServices**  después de los  **servicios. Llamada al método AddXafWebApi**.

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



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


# Personalizar las opciones de OData


Puede personalizar las opciones de  [OData](https://docs.microsoft.com/en-us/odata/overview) en el archivo  _Inicio.cs_. Utilice los  [servicios. AddControllers(). AddOData](https://github.com/OData/AspNetCoreOData#2-basic-usage) para este propósito.

## Cambiar la profundidad de expansión de los objetos de negocio relacionados

Para especificar la opción  [ODataValidationSettings.MaxExpansionDepth](https://learn.microsoft.com/dotnet/api/microsoft.aspnet.odata.query.odatavalidationsettings.maxexpansiondepth), siga estos pasos:

-   Implemente un servicio  _ODataQueryValidator_  personalizado para establecer  [MaxExpansionDepth](https://learn.microsoft.com/dotnet/api/microsoft.aspnet.odata.query.odatavalidationsettings.maxexpansiondepth):
    

    
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
    
-   Reemplace el servicio  _ODataQueryValidator_  predeterminado por el servicio personalizado en el método  _ConfigureServices_:
    
    **Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )
    

    
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
    

## Cambiar una estructura de modelo de EDM mediante el Generador de modelos deOData

Para personalizar la estructura del modelo de entidad OData en tiempo de ejecución (cambiar tipos, propiedades, acciones, etc.), implemente la interfaz  **DevExpress.ExpressApp.WebApi.Services.IEdmModelCustomizer**  en una clase personalizada y manipule  [ODataModelBuilder](https://learn.microsoft.com/en-us/dotnet/api/microsoft.aspnet.odata.builder.odatamodelbuilder?view=odata-aspnetcore-7.0) en el método CustomizeEdmModel según sea necesario.

Puede registrar el implementador personalizado de IEdmModelCustomizer después de la llamada en el método:`services.AddXafWebApi``ConfigureServices`

**Archivo:**  MySolution.WebApi\Startup.cs (_MySolution.Blazor.Server\Startup.cs_ )



```csharp
services.AddXafWebApi(Configuration, options => { /* ... */  }); 
// Add a custom IEdmModelCustomizer.
services.TryAddEnumerable(ServiceDescriptor.Transient<IEdmModelCustomizer, CustomEdmModelCustomizer>());
// OR
// Remove a built-in IEdmModelCustomizer.
// var serviceDescriptor = services.Single(descriptor => descriptor.ImplementationType?.Name == "PersistentAliasEdmModelCustomizer");
// services.Remove(serviceDescriptor);

```

Para obtener más información, revise lo siguiente:

-   [Información general  sobre los generadores de modelos](https://learn.microsoft.com/en-us/odata/webapi/model-builder-abstract);
-   Código de los implementadores integrados de IEdmModelCustomizer (DateTimeNullableEdmModelCustomizer, PersistentAliasEdmModelCustomizer, etc.) dentro de los orígenes de la biblioteca DevExpress.ExpressApp.WebApi;
-   Artículos de soporte:  [T1096425](https://supportcenter.devexpress.com/ticket/details/t1096425/web-api-the-400-bad-request-error-occurs-when-you-use-properties-with-notmappedattribute) |  [T1041495](https://supportcenter.devexpress.com/ticket/details/t1041495/web-api-service-how-to-return-or-serialize-a-business-object-in-a-custom-method-endpoint) |  [T1101266](https://supportcenter.devexpress.com/ticket/details/t1101266/web-api-how-to-create-a-custom-odatacontroller-for-each-business-object-type-to-create) .
