---
title: "MVC Pattern and Layered Model"
description: "Model-View-Controller (MVC) and Layered Architecture. This resource breaks down both concepts to reveal how they function, their key differences, and their importance"
pubDate: "Oct 02 2023"
heroImage: "/blogImages/mvc-ing.png"
---
The Model-View-Controller (MVC) pattern and the Layered Architecture are both design patterns in software engineering, but they serve different purposes and operate at different levels of abstraction in application design. Although they are distinct concepts, they can be related and used together in the development of complex applications. Here's how:

### Model-View-Controller (MVC)

- **Purpose**: MVC is a design pattern primarily used for developing **user interfaces**. It divides the application into three interconnected components, allowing the separation of internal application logic from presentation logic and user input. This facilitates the management of development, testing, and maintenance of the application.

  - **Model**: Represents the data and business logic. Handles data access, queries, and updates. It is responsible for accessing the data persistence layer, defining business rules, handling queries, and storing the application's state.
  - **View**: The visual representation of data, i.e., everything the user can see on the screen. It receives information from the model and displays it to the user in a comprehensible way, generating the user interface.
  - **Controller**: Acts as an intermediary between the model and the view. The controller's main responsibility is to process user inputs (through the view), process them (possibly updating the model), and then return an appropriate response to the user, which can be an update of the current view or the presentation of a new view.
  
    ![](/blogImages/mvc-ing.png)

  #### Do controllers always operate through APIs?

  Not necessarily. The operation of controllers in the Model-View-Controller (MVC) pattern is not limited exclusively to the use of APIs, although in modern web and mobile application development, the use of APIs is very common and often fundamental. The interaction of controllers can vary widely depending on the type of application, its architecture, and the specific requirements of the project.

  ##### <i> In Modern Web and Mobile Applications </i>

  In the context of modern web and mobile applications, especially those built as single-page applications (SPAs) or mobile apps that consume data from a server, controllers often interact with the model and view through APIs. These APIs, typically RESTful or GraphQL, serve as a bridge between the frontend (the view and part of the controller on the client) and the backend (the model and, potentially, part of the controller on the server).

  In these cases, the controller on the client side may send HTTP requests to an API endpoint, which are then handled by the controller on the server side. The server-side controller processes the request, interacts with the model to perform database operations or business logic, and returns a response, generally in JSON or XML format, which the client-side controller can use to update the view.

  ##### <i>In Traditional Server-Based Applications</i>

  In more traditional web applications, where the application logic resides mainly on the server, controllers primarily operate by receiving direct HTTP requests, processing them (interacting with the model as necessary), and returning a response that can be a complete web page (HTML) rendered on the server. In this case, the operation of controllers is not conducted through APIs in the modern sense of web services, though technically it is communicating through the HTTP protocol.

  ##### <i>Other Contexts</i>

  In desktop applications or certain embedded systems where MVC is used as a design pattern to organize code, controllers can operate without communicating through external APIs. In these scenarios, the controller interacts directly with the model and view within the same system or application.

  The relationship between controllers and APIs depends on the design and requirements of the application. While in many modern developments, controllers interact with APIs to facilitate communication between the client and server, in other contexts, they can function more autonomously, directly handling interactions between the view and the model without the need for an external API. The choice to use APIs and how controllers are implemented depends on the specific architecture of the application and the goals of the project.

### Layered Architecture

- **Purpose**: The Layered Architecture is an architectural pattern used to organize applications into separate groups of services, or "layers," where each layer has a specific responsibility. Its primary goal is to separate the concerns of an application to promote independence between parts, thereby facilitating maintenance and scalability. This pattern is more general than MVC and applies to the entire application architecture, not just the user interface.

  - **Presentation Layer (IGU)**: This is the layer closest to the end user. It handles user interaction, displaying information, and gathering user inputs. Its function is to present data and delegate user actions to the business logic layer.
  - **Business Logic Layer**: This is where the application's specific logic is processed, decisions are made, and business rules are executed. This layer acts as an intermediary between the presentation layer and the data layer, processing user requests, executing corresponding logic, and passing data to and from the data layer.
  - **Persistence or Data Access Layer**: This layer manages data persistence and retrieval, interacting with databases, file systems, or other data sources. It is responsible for storing, retrieving, and updating information as requested by the business logic layer.
  - **Service Layer**: In some cases, additional layers such as the Service Layer or Integration Layer are included. This optional layer is positioned between the business logic layer and the presentation layer, or between the business logic and the data layer, depending on the design. Its purpose is to provide a set of common services (such as authentication, authorization, logging, etc.) or to integrate external systems and services. This helps to centralize integration logic and to provide a consistent interface for consumers of these services.

    ![](/blogImages/layered.png)

### Application

- **Layered Architecture**: Applies to the entire structure of the application, from frontend to backend, and is useful in large and complex applications to keep the code organized and facilitate the integration of different technologies or components.
- **MVC**: Primarily used in designing the user interface, whether in web, desktop, or mobile applications. It is especially popular in web application development, where it facilitates the separation of server and client code.

### Relationship between MVC and Layered Architecture

Although MVC focuses on the separation of the user interface, and Layered Architecture focuses on the general architecture of the application, they can be related in the following ways:

- **MVC within the Layered Architecture**: MVC can be considered as part of the presentation layer in the Layered Architecture. That is, MVC handles user interaction with the application, which is just a portion of the presentation layer.
- **Complementarity**: In complex applications, the use of MVC for the user interface can be complemented with the Layered Architecture to structure the rest of the application, allowing a clear separation between presentation logic, business logic, and data access logic.
- **Flexibility and Maintainability**: Combining both patterns allows for developing applications with a more organized structure, facilitating scalability, maintenance, and independent testing of different components.

While both patterns seek to improve the structure and organization of code, the Layered Architecture is a more general architectural pattern that focuses on the entire structure of the application, whereas MVC is a design pattern aimed at separating the user interface logic from the business logic. In large projects, both patterns can coexist: MVC can be used within the presentation layer of the Layered Architecture to organize user interaction with the application.

---

Español

---
El patrón Modelo-Vista-Controlador (MVC) y el Modelo de Capas son ambos patrones de diseño en ingeniería de software, pero sirven a propósitos diferentes y operan a distintos niveles de abstracción en el diseño de aplicaciones. Aunque son conceptos diferentes, pueden estar relacionados y usarse juntos en el desarrollo de aplicaciones complejas. Aquí te explico cómo:

### Modelo-Vista-Controlador (MVC)

- **Propósito**: MVC es un patrón de diseño utilizado principalmente para desarrollar **interfaces de usuario**. Divide la aplicación en tres componentes interconectados, lo que permite separar la lógica interna de la aplicación de la lógica de presentación y la entrada del usuario. Esto facilita la gestión del desarrollo, la prueba y el mantenimiento de la aplicación.
  
  - **Modelo**: Representa los datos y la lógica de negocio. Maneja el acceso a los datos, las consultas, y las actualizaciones. Es responsable de acceder a la capa de persistencia de datos, definir las reglas de negocio, manejar las consultas y almacenar el estado de la aplicación.
  - **Vista**: Es la representación visual de los datos, es decir, todo lo que el usuario puede ver en pantalla. Recibe información del modelo y la muestra al usuario de una manera comprensible, generando la interfaz de usuario.
  - **Controlador**: Actúa como intermediario entre el modelo y la vista. 
  La principal responsabilidad del controlador es procesar las entradas del usuario (a través de la vista), procesarlas (posiblemente actualizando el modelo), y luego devolver una respuesta adecuada al usuario, que puede ser una actualización de la vista actual o la presentación de una nueva vista.

    ![](/blogImages/mvc-esp.png)

  #### ¿El controlador opera siempre a trevés de APIS's?

  No necesariamente. La operación de los controladores en el patrón Modelo-Vista-Controlador (MVC) no está limitada exclusivamente al uso de APIs, aunque en el desarrollo moderno de aplicaciones web y móviles, el uso de APIs es muy común y a menudo fundamental. La interacción de los controladores puede variar ampliamente dependiendo del tipo de aplicación, su arquitectura y los requisitos específicos del proyecto.
  
  ##### <i> En Aplicaciones Web y Móviles Modernas </i>
  
  En el contexto de aplicaciones web y móviles modernas, especialmente aquellas construidas como aplicaciones de una sola página (SPA) o aplicaciones móviles que consumen datos de un servidor, los controladores frecuentemente interactúan con el modelo y la vista a través de APIs. Estas APIs, típicamente RESTful o GraphQL, sirven como un puente entre el frontend (la vista y parte del controlador en el cliente) y el backend (el modelo y, potencialmente, parte del controlador en el servidor).
  
  En estos casos, el controlador en el lado del cliente puede enviar solicitudes HTTP a un endpoint de la API, que luego son manejadas por el controlador en el lado del servidor. El controlador del servidor procesa la solicitud, interactúa con el modelo para realizar operaciones de base de datos o lógica de negocio, y devuelve una respuesta, generalmente en formato JSON o XML, que el controlador del cliente puede utilizar para actualizar la vista.
  
  ##### <i>En Aplicaciones Tradicionales basadas en Servidor</i>
  
  En aplicaciones web más tradicionales, donde la lógica de la aplicación reside principalmente en el servidor, los controladores operan principalmente al recibir solicitudes HTTP directas, procesarlas (interactuando con el modelo según sea necesario), y devolver una respuesta que puede ser una página web completa (HTML) renderizada en el servidor. En este caso, la operación de los controladores no se realiza a través de APIs en el sentido moderno de servicios web, aunque técnicamente se está comunicando a través del protocolo HTTP.
  
  ##### <i>Otros Contextos</i>
  
  En aplicaciones de escritorio o ciertos sistemas embebidos donde MVC se utiliza como patrón de diseño para organizar el código, los controladores pueden operar sin comunicarse a través de APIs externas. En estos casos, el controlador interactúa directamente con el modelo y la vista dentro del mismo sistema o aplicación.
  
  La relación entre controladores y APIs depende del diseño y los requisitos de la aplicación. Mientras que en muchos desarrollos modernos los controladores interactúan con las APIs para facilitar la comunicación entre el cliente y el servidor, en otros contextos, pueden funcionar de manera más autónoma, manejando directamente las interacciones entre la vista y el modelo sin la necesidad de una API externa. La elección de utilizar APIs y cómo se implementan los controladores depende de la arquitectura específica de la aplicación y de los objetivos del proyecto.

### Modelo de Capas

- **Propósito**: El Modelo de Capas es un patrón arquitectónico que se utiliza para organizar las aplicaciones en grupos de servicios separados, o "capas", donde cada capa tiene una responsabilidad específica. Su objetivo principal es separar las preocupaciones de una aplicación para promover la independencia entre las partes, facilitando así el mantenimiento y la escalabilidad. Este patrón es más general que MVC y se aplica a toda la arquitectura de la aplicación, no solo a la interfaz de usuario.

  - **Capa de Presentación (IGU)**: Es la capa más cercana al usuario final. Se encarga de la interacción con el usuario, mostrando la información y recogiendo las entradas del usuario. Su función es presentar los datos y delegar las acciones del usuario a la capa de lógica de negocio.
  - **Capa de Lógica de negocio**: Aquí es donde se procesa la lógica específica de la aplicación, se toman decisiones y se ejecutan las reglas de negocio. Esta capa actúa como un intermediario entre la capa de presentación y la capa de datos, procesando las solicitudes del usuario, ejecutando la lógica correspondiente y pasando los datos a y desde la capa de datos.
  - **Capa de Persisencia o acceso a datos**: Esta capa gestiona la persistencia y la recuperación de los datos, interactuando con bases de datos, sistemas de archivos u otras fuentes de datos. Se encarga de almacenar, recuperar y actualizar la información según lo solicite la capa de lógica de negocio.
  - **Capa de Servicios**: En algunos casos, se incluyen capas adicionales como la Capa de Servicios o la Capa de Integración. Esta capa opcional se sitúa entre la capa de lógica de negocio y la capa de presentación o entre la lógica de negocio y la capa de datos, dependiendo del diseño. Su propósito es proporcionar un conjunto de servicios comunes (como autenticación, autorización, logging, etc.) o para integrar sistemas y servicios externos. Esto ayuda a centralizar la lógica de integración y a proporcionar una interfaz coherente para los consumidores de estos servicios.

    ![](/blogImages/capas.png)

### Aplicación

- **Modelo de Capas**: Se aplica a toda la estructura de la aplicación, desde el frontend hasta el backend, y es útil en aplicaciones grandes y complejas para mantener organizado el código y facilitar la integración de diferentes tecnologías o componentes.
- **MVC**: Se utiliza principalmente en el diseño de la interfaz de usuario, ya sea en aplicaciones web, de escritorio o móviles. Es especialmente popular en el desarrollo de aplicaciones web, donde facilita la separación del código del servidor y del cliente.

### Relación entre MVC y Modelo de Capas

Aunque MVC se centra en la separación de la interfaz de usuario, y el Modelo de Capas se enfoca en la arquitectura general de la aplicación, pueden estar relacionados de la siguiente manera:

- **MVC dentro del Modelo de Capas**: El MVC se puede considerar como parte de la capa de presentación en el Modelo de Capas. Es decir, el MVC se encarga de la interacción del usuario con la aplicación, que es solo una parte de la capa de presentación.
- **Complementariedad**: En aplicaciones complejas, el uso de MVC para la interfaz de usuario puede complementarse con el Modelo de Capas para estructurar el resto de la aplicación, permitiendo una separación clara entre la lógica de presentación, la lógica de negocio, y la lógica de acceso a datos.
- **Flexibilidad y Mantenibilidad**: La combinación de ambos patrones permite desarrollar aplicaciones con una estructura más organizada, facilitando la escalabilidad, el mantenimiento, y la prueba de diferentes componentes de manera independiente.

Aunque ambos patrones buscan mejorar la estructura y organización del código, el Modelo de Capas es un patrón arquitectónico más general que se enfoca en la estructura completa de la aplicación, mientras que MVC es un patrón de diseño orientado a separar la lógica de la interfaz de usuario de la lógica de negocio. En proyectos grandes, ambos patrones pueden coexistir: MVC se puede usar dentro de la capa de presentación del Modelo de Capas para organizar la interacción del usuario con la aplicación.
