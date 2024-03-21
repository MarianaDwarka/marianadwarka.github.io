---
title: "Java API Project"
description: "The current project is based on the design and implementation of an API using the Spring Boot framework for a growing store. Through a layered software architecture, the API provides a modular structure that separates the system's responsibilities into different logical layers."
pubDate: "Oct 16 2023"
heroImage: "/blogImages/rest-api.png"
---

The project focuses on the development of an API for a store, with the aim of managing products, sales, and customers. This system will allow the store to efficiently manage its sales operations and product inventory, facilitating the registration and handling of these processes through a web interface and a mobile application in the future.

<a class="btn btn-outline ml-5" href="https://github.com/MarianaDwarka/API-Tienda" target="_blank">Check out the project repository</a> 


The proposed solution is structured following the multi-layer model (also known as layered architecture), a design pattern widely used in enterprise applications, especially with the Spring Boot framework in the Java ecosystem.

<a class="btn btn-outline ml-5" href="https://marianadwarka.github.io/blog/multi-layer-architecture/" target="_blank">Check out -> MVC Pattern and Layered Model</a>

Below is a detailed explanation of how this model applies to the project:

### 1. **Presentation Layer (Controller)**

In the context of this API, the presentation layer is responsible for interacting with the end-users (the store owner and her employees) through two types of HTTP clients: a web application and, potentially, a mobile application. Using Spring Boot, this layer is composed mainly of controllers (annotated with `@RestController`), which listen to HTTP requests (GET, POST, DELETE, PUT) and respond with the requested data or the result of an operation. The controllers make calls to the service layer to execute the business logic.

### 2. **Service Layer (Service)**

The service layer, implemented with classes annotated with `@Service`, contains the application's business logic. Here, methods are defined for operations such as CRUD of products, clients, and sales; querying products with low availability; obtaining details of specific sales; and the aggregation of sales data. This layer acts as an intermediary between the presentation layer and the data access layer, ensuring that the requested operations are executed according to established business rules.

### 3. **Data Access Layer (Repository)**

This layer interacts directly with the data source (for example, a relational database) to perform CRUD operations on the application entities: Product, Client, and Sale. In Spring Boot, this is achieved through the use of repositories (annotated with `@Repository`), which extend interfaces like `JpaRepository` to provide ready-to-use data access methods, as well as the ability to define custom queries. This layer abstracts the complexity of direct database management from the other layers of the application.

### 4. **Model Layer (Model)**

Finally, the model layer defines the business entities (Product, Sale, Client) with their respective properties and relationships. Using JPA (Java Persistence API) and annotations such as `@Entity`, Spring Boot maps these classes to database tables, facilitating the management of data persistence and relationships between entities.

The project applies the multi-layer model, separating responsibilities into different layers that interact with each other to facilitate the development, maintenance, and scalability of the application. Spring Boot significantly simplifies the implementation of each layer through the use of annotations and dependency injection, allowing developers to focus on business logic and providing value to end-users. This approach ensures that the API can be consumed by both web and mobile applications, meeting the requirements of the store owner and adapting to future expansions or modifications.

![](/blogImages/tienda-paquetes.png)

The provided image showcases the package structure for the aforementioned store. This structure mirrors the layered architecture and the organization of responsibilities within the code.

The application is divided into several packages that group together classes and interfaces with similar responsibilities:

### Packages and Their Role in the Multi-Layer Architecture

1. **com.marianadwarka.tienda.controller**
   - Contains controller classes (`ClienteController`, `ProductoController`, `VentaController`) which act as part of the presentation layer. These classes handle incoming HTTP requests, invoke operations from the service layer, and return the appropriate responses to the client.

2. **com.marianadwarka.tienda.dto**
   - Defines the data transfer objects (DTOs), such as `MayorVentaDTO` and `ProductosPorVentaDTO`. DTOs are used to transfer specific information between sublayers, particularly from the business logic to the presentation layer, facilitating data exchange and reducing direct exposure of the model entities.

3. **com.marianadwarka.tienda.model**
   - Contains the domain entities (`Cliente`, `Producto`, `Venta`) that represent the model layer. These classes are typically annotated with `@Entity` and reflect the structure of the database in the code.

4. **com.marianadwarka.tienda.repository**
   - Houses interfaces for the data access layer, like `IClienteRepository`, `IProductoRepository`, `IVentaRepository`. These interfaces extend frameworks such as JPA, enabling an abstraction of the database access.

5. **com.marianadwarka.tienda.service**
   - Includes interfaces (`IClienteService`, `IProductoService`, `IVentaService`) and their implementations (`ClienteService`, `ProductoService`, `VentaService`). The interfaces define the business logic and the operations that can be carried out, while the implementations concrete these definitions.

### Use of Interfaces for Service and Repository Layers

As observed, the implementation of layers through interfaces is a recommended practice with multiple advantages. For example, interfaces help to decouple the application's layers. The presentation layer does not need to know how operations are implemented in the service layer; it only needs to know the interface. This facilitates changes and the maintainability of the code.

Additionally, interfaces allow for multiple implementations. This is useful if the business logic needs to vary according to different contexts, without changing how the clients of the service layer interact with it.

Another important aspect is that interfaces act as contracts that define what operations are available, which aids in the clarity of the design and the expectation of what each part of the system does.



The developed API represents a technical solution for the operational needs of an expanding store. Leveraging the strengths of Spring Boot and the multi-layer architecture, a decoupled system that is easy to test, maintain, and expand has been achieved. The organization of the code into well-defined packages, along with the implementation of interfaces for the service and data access layers, ensures the ability to adapt the application to future requirements with minimal effort.


---

Español

---

El proyecto se enfoca en el desarrollo de una API para una tienda, con el objetivo de gestionar productos, ventas y clientes. Este sistema permitirá a la tienda administrar de manera eficiente sus operaciones de venta y el stock de sus productos, facilitando el registro y manejo de estos procesos a través de una interfaz web y una aplicación móvil en el futuro.

<a class="btn btn-outline ml-5" href="https://github.com/MarianaDwarka/API-Tienda" target="_blank">Revisar repositorio del proyecto</a>


La solución propuesta se estructura siguiendo el modelo multicapas (también conocido como arquitectura en capas), un patrón de diseño ampliamente utilizado en aplicaciones empresariales, especialmente con el framework Spring Boot en el ecosistema de Java. 

<a class="btn btn-outline ml-5" href="https://marianadwarka.github.io/blog/multi-layer-architecture/" target="_blank">Revisar -> MVC Pattern and Layered Model</a>

A continuación, se detalla cómo se aplica este modelo al proyecto:

### 1. **Capa de presentación (Controller)**

En el contexto de esta API, la capa de presentación se encarga de interactuar con los usuarios finales (la dueña de la tienda y sus empleados) a través de dos tipos de clientes HTTP: una aplicación web y, potencialmente, una aplicación móvil. Utilizando Spring Boot, esta capa está compuesta principalmente por controladores (anotados con `@RestController`), que escuchan las solicitudes HTTP (GET, POST, DELETE, PUT) y responden con los datos solicitados o el resultado de una operación. Los controladores hacen llamadas a la capa de servicio para ejecutar la lógica de negocio.

### 2. **Capa de Servicio (Service)**

La capa de servicio, implementada con clases anotadas con `@Service`, contiene la lógica de negocio de la aplicación. Aquí se definen métodos para operaciones como el CRUD de productos, clientes, y ventas; la consulta de productos con baja disponibilidad; la obtención de detalles de ventas específicas; y la agregación de datos de ventas. Esta capa actúa como un intermediario entre la capa de presentación y la capa de acceso a datos, asegurando que las operaciones solicitadas se ejecuten de acuerdo con las reglas de negocio establecidas.

### 3. **Capa de Acceso a Datos (Repository)**

Esta capa interactúa directamente con la fuente de datos (por ejemplo, una base de datos relacional) para realizar operaciones CRUD sobre las entidades de la aplicación: Producto, Cliente, y Venta. En Spring Boot, esto se logra mediante el uso de repositorios (anotados con `@Repository`), que extienden interfaces como `JpaRepository` para proporcionar métodos de acceso a datos listos para usar, así como la capacidad de definir consultas personalizadas. Esta capa abstrae la complejidad del manejo directo de la base de datos de las otras capas de la aplicación.

### 4. **Capa de Modelo (Model)**

Finalmente, la capa de modelo define las entidades de negocio (Producto, Venta, Cliente) con sus respectivas propiedades y relaciones. Utilizando JPA (Java Persistence API) y anotaciones como `@Entity`, Spring Boot mapea estas clases a tablas en la base de datos, facilitando la gestión de la persistencia de datos y las relaciones entre entidades.


El proyecto aplica el modelo multicapas, separando las responsabilidades en distintas capas que interactúan entre sí para facilitar el desarrollo, mantenimiento y escalabilidad de la aplicación. Spring Boot simplifica significativamente la implementación de cada capa mediante el uso de anotaciones y la inyección de dependencias, permitiendo a los desarrolladores concentrarse en la lógica de negocio y en proporcionar valor a los usuarios finales. Este enfoque asegura que la API pueda ser consumida tanto por aplicaciones web como móviles, cumpliendo con los requisitos de la dueña de la tienda y adaptándose a futuras expansiones o modificaciones.

![](/blogImages/tienda-paquetes.png)


En particular, en la imagen anterior se muestra la estructura de paquetes para la tienda descrita anteriormente. Esta estructura es un reflejo de la arquitectura en capas y la organización de responsabilidades dentro del código.

La aplicación se divide en varios paquetes que agrupan clases e interfaces con responsabilidades similares:

### Paquetes y su Rol en la Arquitectura Multicapas

1. **com.marianadwarka.tienda.controller**
   - Contiene clases controladoras (`ClienteController`, `ProductoController`, `VentaController`) que actúan como parte de la capa de presentación. Estas clases manejan las solicitudes HTTP entrantes, invocan operaciones de la capa de servicio y devuelven las respuestas adecuadas al cliente.

2. **com.marianadwarka.tienda.dto**
   - Define los objetos de transferencia de datos (DTOs, por sus siglas en inglés `Data Transfer Objects`), como `MayorVentaDTO` y `ProductosPorVentaDTO`. Los DTOs se utilizan para transferir información específica entre subcapas, especialmente de la lógica de negocio hacia la capa de presentación, facilitando el intercambio de datos y reduciendo la exposición directa de las entidades del modelo.

3. **com.marianadwarka.tienda.model**
   - Contiene las entidades del dominio (`Cliente`, `Producto`, `Venta`) que representan la capa de modelo. Estas clases están típicamente anotadas con `@Entity` y son el reflejo de la estructura de la base de datos en código.

4. **com.marianadwarka.tienda.repository**
   - Alberga las interfaces para la capa de acceso a datos, como `IClienteRepository`, `IProductoRepository`, `IVentaRepository`. Estas interfaces extienden frameworks como JPA, permitiendo una abstracción del acceso a la base de datos.

5. **com.marianadwarka.tienda.service**
   - Incluye interfaces (`IClienteService`, `IProductoService`, `IVentaService`) y sus implementaciones (`ClienteService`, `ProductoService`, `VentaService`). Las interfaces definen la lógica de negocio y las operaciones que pueden realizarse, mientras que las implementaciones concretan estas definiciones.

### Uso de Interfaces para las Capas de Servicio y Repositorio

Como se puede observar, se hizo la implementación de capas mediante interfaces, eesta es una práctica recomendada que tiene múltiples ventajas, por ejemplo, las interfaces ayudan a desacoplar las capas de la aplicación. Por ejemplo, la capa de presentación no necesita saber cómo se implementan las operaciones en la capa de servicio, solo necesita conocer la interfaz. Esto facilita los cambios y la mantenibilidad del código.

Además, las interfaces permiten tener múltiples implementaciones. Esto es útil si la lógica de negocio necesita variar según diferentes contextos, sin cambiar la forma en que los clientes de la capa de servicio interactúan con ella.

Otro aspecto importante es que las interfaces actúan como contratos que definen qué operaciones están disponibles, lo que ayuda a la claridad del diseño y a la expectativa de qué hace cada parte del sistema.

La API desarrollada representa una solución técnica para las necesidades operativas de una tienda en expansión. Aprovechando las fortalezas de Spring Boot y la arquitectura multicapa, se ha logrado un sistema desacoplado que es fácil de probar, mantener y ampliar. La organización del código en paquetes bien definidos, junto con la implementación de interfaces para las capas de servicio y acceso a datos, garantiza la capacidad de adaptar la aplicación a requisitos futuros con mínimo esfuerzo.
