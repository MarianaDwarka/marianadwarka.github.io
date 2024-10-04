---
title: "A standard multi-layer structure commonly used in Spring Boot"
description: "Algorithmic trading system that automates the entire process, from extracting real-time market data (EUR/USD) via the OANDA API to executing trades based on a simple moving average strategy. Data is processed in an Azure VM and stored in a MySQL database, enabling continuous strategy optimization."
pubDate: "Oct 09 2023"
heroImage: "/blogImages/spring.png"
---

Spring Boot, a project within the broader Spring ecosystem, simplifies the creation of microservices and web applications with minimal configuration, leveraging Inversion of Control (IoC) and dependency injection to efficiently organize and manage application components.

There are various multi-layer models or architectures that can be implemented or used depending on the project at hand, however, there are some standardizations to follow that adapt to most developments made in Java. Review the article about the MVC pattern and layered model:


<a class="btn btn-outline ml-5" href="https://marianadwarka.github.io/blog/mvc-layered/" target="_blank">MVC Pattern and Layered Model</a>

Moreover, although Spring Boot is quite flexible and can adapt to various architectures, a standard multi-layer structure commonly used in Spring Boot projects includes the following layers:

![](/blogImages/architecture.png)

### 1. **Presentation Layer (or Web Layer)**

- **Responsibility**: Handles all interactions with the user through the graphical interface or API requests. That is, it is the layer responsible for attending incoming HTTP requests, deriving them to the corresponding layer, waiting for a response, generating it, and transmitting it back to the client. Generally, this layer works closely with the "Service" layer, where from a request it calls the functions it needs from the service layer to generate a response.
- **Spring Components**: Controllers (`@Controller` or `@RestController`), where `@RestController` combines `@Controller` and `@ResponseBody`, eliminating the need to annotate each handling method with `@ResponseBody`.

### 2. **Service Layer (or Business Logic Layer)**

- **Responsibility**: Contains the business logic of the application. Acts as a bridge between the web layer and the data access layer, orchestrating the flow of data and business operations. It is the layer where all necessary functions or operations are specified and can offer, as its name suggests, a service to the controller layer.
- **Spring Components**: Services (`@Service`), which represent the business logic. Spring manages these classes as Spring beans, allowing dependency injection wherever necessary.

### 3. **Data Access Layer (or Repository Layer)**

- **Responsibility**: Responsible for communication with the database or any other data source, such as file systems, web services, etc. This layer abstracts the data access logic from the rest of the application. It is the layer in charge of data persistence, that is, the result of the modeling interaction between the developed classes and the database tables.
- **Spring Components**: Repositories (`@Repository`), which abstract storage, retrieval, and search operations, facilitating integration with databases through JPA (Java Persistence API). Spring Data JPA can further simplify the implementation of this layer by providing ready-to-use CRUD repositories and support for derived queries. Also, it allows data access using different technologies, for example, JDBC or an ORM like JPA through Hibernate.

### 4. **Model Layer (or Domain Layer)**

- **Responsibility**: This layer works closely with the Repository layer. It defines the business entities (models) and their relationships. Each of the classes models a real-life object. These entities are mapped to the database through ORM (Object-Relational Mapping).
- **Spring Components**: Entities (`@Entity`), used by Hibernate or any other JPA provider to map classes to database tables.

### Common Multi-Layer Architecture in Spring Boot

In a typical Spring Boot application, these layers interact as follows:

- **HTTP requests** arrive at the **presentation layer**, where controllers process the request and delegate the execution of business logic to the **service layer**.
- The **service layer** executes the necessary business logic and, if needed, interacts with the **data access layer** to persist or retrieve data.
- The **data access layer** uses repositories to interact with the database and returns data to the service layer, which in turn may transform this data into DTOs (Data Transfer Objects) or view models before sending them back to the presentation layer for the client's response.

This structure not only promotes the separation of responsibilities, facilitating the maintenance and scalability of the application, but also leverages the features of Spring and Spring Boot to reduce the amount of repetitive and boilerplate code necessary, especially in configuration and defining the application's infrastructure.

## Inversion of Control and Dependency Injection

Inversion of Control (IoC) and Dependency Injection (DI) are fundamental concepts in modern software development, especially when it comes to creating highly modular and easy-to-maintain applications. These concepts play a crucial role in frameworks like Spring Boot, facilitating the efficient organization and management of application components. Below, both concepts are explained and how they relate to the Layered Model, particularly in the context of Spring Boot.

### Inversion of Control (IoC)

Inversion of Control is a software design principle by which the control of the program's execution flow is inverted. Instead of the application code controlling the execution flow, this control is delegated to an external container or framework.
- **How It Works in Spring Boot**: In Spring and Spring Boot, IoC is implemented through the Spring container. This container manages the creation and configuration of all objects (known as beans in Spring), controlling their lifecycle. Developers only need to define dependencies among components, and the container takes care of instantiating and assembling them when necessary.

### Dependency Injection (DI)

Dependency Injection is a design pattern that implements IoC to resolve dependencies between objects. Instead of objects creating or finding their dependencies, these are "injected" by an external agent (like the Spring container in the case of Spring Boot).
- **How It Works in Spring Boot**: DI allows Spring Boot components to be externally configured and in a decoupled manner. For example, if a service needs access to a data repository, the instance of the repository is injected into the service by the Spring container, rather than the service directly instantiating the repository. This is done using annotations like `@Autowired`.

IoC and DI are fundamental in Spring Boot for implementing the Layered Model efficiently, providing a flexible, maintainable, and easily testable application architecture. These principles help to better organize the code, promoting a clean design and a clear separation of responsibilities among the different parts of the application.

---

Español

---
Spring Boot, un proyecto dentro del ecosistema más amplio de Spring, facilita la creación de aplicaciones de microservicios y web con mínima configuración, aprovechando la inversión de control (IoC) y la inyección de dependencias para organizar y gestionar los componentes de la aplicación de manera eficiente. 

Existen diversis modelos o arquitecturas multicapa que pueden ser implementados o utilizados según el proyecto sobre el cual se esté trabajando, sin embargo, hay algunas estandarizaciones a seguir que se adaptan a la mayoría de los desarrollos realizados en Java. Revisar el artículo sobre el patrón MVC y el modelo de capas:

<a class="btn btn-outline ml-5" href="https://marianadwarka.github.io/blog/mvc-layered/" target="_blank">MVC Pattern and Layered Model</a>


Además, aunque Spring Boot es bastante flexible y puede adaptarse a diversas arquitecturas, una estructura multicapa estándar comúnmente utilizada en proyectos Spring Boot incluye las siguientes capas:

![](/blogImages/architecture.png)

### 1. **Capa de Presentación (o Capa Web)**

- **Responsabilidad**: Maneja todas las interacciones con el usuario a través de la interfaz gráfica o solicitudes API. Es decir, es la capa encargada de atender las solicitudes http entrantes, derivarlas a la capa que corresponda, esperar por una respuesta, generarla y transmitirla nuevamente al cliente. Generalmente, esta capa trabaja estrechamente con la capa "Service", donde a partir de una request llama a las funciones que necesite de la capa service para generar una response.
- **Componentes de Spring**: Controladores (`@Controller` o `@RestController`), donde `@RestController` combina `@Controller` y `@ResponseBody`, eliminando la necesidad de anotar cada método de manejo con `@ResponseBody`.

### 2. **Capa de Servicio (o Capa de Lógica de Negocio)**

- **Responsabilidad**: Contiene la lógica de negocio de la aplicación. Actúa como un puente entre la capa web y la capa de acceso a datos, orquestando el flujo de datos y las operaciones de negocio. Es la capa donde se especifican todas las funciones u operaciones que sean necesarias y que puedan ofrecer, como dice su nombre, un servicio a la capa controller.
- **Componentes de Spring**: Servicios (`@Service`), que representan la lógica de negocio. Spring gestiona estas clases como beans de Spring, permitiendo la inyección de dependencias donde sea necesario.

### 3. **Capa de Acceso a Datos (o Capa de Repositorio)**

- **Responsabilidad**: Encargada de la comunicación con la base de datos o cualquier otra fuente de datos, como sistemas de archivos, servicios web, etc. Esta capa abstrae la lógica de acceso a datos del resto de la aplicación. Es la capa encargada de la persistencia de los datos, es decir, del resultado de la interacción de modelado entre las clases desarrolladas y las tablas de una base de datos.
- **Componentes de Spring**: Repositorios (`@Repository`), que abstractizan el almacenamiento, recuperación y búsqueda de operaciones, facilitando la integración con bases de datos a través de JPA (Java Persistence API). Spring Data JPA puede simplificar aún más la implementación de esta capa al proporcionar repositorios CRUD listos para usar y soporte para consultas derivadas. También, permite el acceso a los datos mediante diferentes tecnologías, por ejemplo, JDBC o algún ORM como JPA a través de Hibernate.

### 4. **Capa de Modelo (o Capa de Dominio)**

- **Responsabilidad**: Esta capa trabaja estrechamente con la capa Repository. Define las entidades de negocio (modelos) y las relaciones entre ellas. Cada una de las clases modela un objeto de la vida real. Estas entidades son mapeadas a la base de datos a través de ORM (Object-Relational Mapping). 
- **Componentes de Spring**: Entidades (`@Entity`), utilizadas por Hibernate o cualquier otro proveedor JPA para mapear clases a tablas de base de datos.

### Arquitectura Multicapa Común en Spring Boot

En una aplicación típica de Spring Boot, estas capas interactúan de la siguiente manera:

- Las **solicitudes HTTP** llegan a la **capa de presentación**, donde los controladores procesan la solicitud y delegan la ejecución de la lógica de negocio a la **capa de servicio**.
- La **capa de servicio** ejecuta la lógica de negocio necesaria y, si es necesario, interactúa con la **capa de acceso a datos** para persistir o recuperar datos.
- La **capa de acceso a datos** utiliza repositorios para interactuar con la base de datos y devuelve los datos a la capa de servicio, que a su vez puede transformar estos datos en DTOs (Data Transfer Objects) o modelos de vista antes de enviarlos de vuelta a la capa de presentación para la respuesta al cliente.

Esta estructura no solo promueve la separación de responsabilidades, facilitando el mantenimiento y la escalabilidad de la aplicación, sino que también aprovecha las características de Spring y Spring Boot para reducir la cantidad de código repetitivo y boilerplate necesario, especialmente en la configuración y la definición de la infraestructura de la aplicación.

## Inversión de control e Inyección de dependencias

La Inversión de Control (IoC) y la Inyección de Dependencias (DI) son conceptos fundamentales en el desarrollo de software moderno, especialmente en lo que respecta a la creación de aplicaciones altamente modulares y fáciles de mantener. Estos conceptos juegan un papel crucial en frameworks como Spring Boot, facilitando la organización y gestión eficiente de los componentes de la aplicación. A continuación, se explican ambos conceptos y cómo se relacionan con el Modelo de Capas, particularmente en el contexto de Spring Boot.

### Inversión de Control (IoC)

La Inversión de Control es un principio de diseño de software por el cual el control del flujo de ejecución del programa se invierte. En lugar de que el código de la aplicación controle el flujo de ejecución, este control se delega a un contenedor o framework externo.
- **Cómo Funciona en Spring Boot**: En Spring y Spring Boot, IoC se implementa a través del contenedor Spring. Este contenedor gestiona la creación y la configuración de todos los objetos (conocidos como beans en Spring), controlando su ciclo de vida. Los desarrolladores solo necesitan definir las dependencias entre los componentes, y el contenedor se encarga de instanciarlos y ensamblarlos cuando sea necesario.

### Inyección de Dependencias (DI)

La Inyección de Dependencias es un patrón de diseño que implementa IoC para resolver dependencias entre objetos. En lugar de que los objetos creen o busquen sus dependencias, estas les son "inyectadas" por un agente externo (como el contenedor Spring en el caso de Spring Boot).
- **Cómo Funciona en Spring Boot**: DI permite que los componentes de Spring Boot sean configurados externamente y de una manera desacoplada. Por ejemplo, si un servicio necesita acceder a un repositorio de datos, la instancia del repositorio se inyecta en el servicio por el contenedor Spring, en lugar de que el servicio instancie directamente el repositorio. Esto se realiza mediante anotaciones como `@Autowired`.

IoC y DI son fundamentales en Spring Boot para implementar el Modelo de Capas de manera eficiente, proporcionando una arquitectura de aplicación flexible, mantenible y fácilmente testeable. Estos principios ayudan a organizar mejor el código, promoviendo un diseño limpio y una separación clara de responsabilidades entre las diferentes partes de la aplicación.