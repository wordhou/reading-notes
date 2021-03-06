Spring MVC is a Java framework for serving web applications with a Model-View-Controller design architecture.

# MVC architecture

MVC refers to a Model-View-Controller design pattern for separating responsibilities in an application. The Model refers to the actual application data and encapsulates that data and its behavior. The View is responsible for rendering that data and serving it (in this application) as HTML. The Controller is responsible for handling user input and processing the input to manipulate the models and generate views.

# Developing with Spring MVC

In Spring MVC all of the HTTP requests and responses are handled by a `DispatcherServlet`, which receives HTTP requests, calls the Controller methods, which then return a string with the name of the view that will render the response. Along the way the Controller method may attach data or manipulate the underlying Model that the view will render.

What's interesting about this approach is that everything goes back to the DispatcherServlet. Instead of calling the renderer from the Controller, the view name is passed back to the DispatcherServlet which then calls the renderer. This allows all of the components (classes and methods) to be built separately from each other, each with their own concerns.

# Annotations

Spring MVC does a lot behind the scenes. It scans the code for annotations, instantiates classes, and performs dependency injection (inversion of control). A lot of this is controlled by meta-data in the form of annotations, labels in our code that begin with the `@` symbol. This configuration can also be controlled by XML files in the project.

## Component

A Spring application is built out of Components, which are classes that Spring will autodetect and instantiate for dependency injection. Components are annotated with the `@Component` annotation. However the annotation may not be used very much, since there are three specialized types of components that are used in more specific situations.

## Controllers

Controller classes are components are annotated with the `@Controller` annotation. This indicates to SpringMVC that it should scan the class for annotated methods that handle HTTP requests and responses. The individual methods in the controller can be annotated with `@RequestMapping` or `@GetMapping` to indicate to Spring that it should call these methods when receiving HTTP requests at various endpoints.

### HTTP Request handling

HTTP requests are handled by methods with the `@RequestMapping` annotation. This annotation indicates the HTTP method and path (or paths) that the method should respond to, what kind of data it expects, and also what kind of data it returns. This allows us to build APIs that accept and return JSON, for example.

## Services

These classes are also subtypes of `@Component` and they provide a utility or encapsulates a layer of business logic.

## Repository

These classes deal with storage of objects and typically give us some way to perform Create-Read-Update-Delete (CRUD) operations.
These are also a subtype of `@Component`.

# Data Repositories and CRUD

We can use Spring Data JPA to create repository implementations at runtime based on a repository interface. These repositories act as in-memory databases that store plain Java objects. To indicate to Spring Data JPA that an object should be stored in a repository, we annotate that object with the `@Entity` annotation and also give one of its methods the `@Id` method to indicate that it's a primary key.

## Interfaces

Spring Data gives us three repository interfaces: `CrudRepository`, `PagingAndSortingRepository`, and `JpaRepository`, each of which extends the previous. The `CrudRepository` provides us with the typical operations on a database object model:

- `save(...)`
- `findOne(...)`
- `findAll(...)`
- `count()`
- `delete(...)`
- `exists(...)

## Relationships

Spring Data models our data using Java classes labeled with the `@Entity` annotation. It also models the relationships between entities based on relationship annotations: `@OneToMany, @ManyToMany, @ManyToOne`. We also need to specify join columns or mappedBy values to create the relationship. Behind the scenes, Spring Data is creating the table schemas and tables with the primary keys and foreign keys necessary to perform the SQL join operations.

# Integration testing

Integration testing allows us to verify the behavior of our application from end to end and be an important part of a testing strategy for a web application. We can perform integration testing in Spring MVC using JUnit 5. When properly configured, the testing framework will load all of the application beans into a `WebApplicationContext` object that gives us access to all of our controllers and services.

## WebApplicationContext object

```java
@Autowired
private WebApplicationContext webApplicationContext;

// gets the instance of the HelloWorldController
webApplicationContext.getBean("HelloWorldController")
```

## MockMVC object

The MockMVC object lets us test all of our controller endpoints as well as any Spring MVC infrastructure components. I believe it simulates what Spring does when it runs a web application, loading and connecting all of the autowired components and allowing us to test any part of the system.

More to come here.

# Spring Security

The Spring security architecture consists of authentication and authorization. Authentication determines who a user is, and authorization determines what a user is allowed to do.

## Authentication

Authentication is provided by an `AuthenticationManager` interface. It exposes an `authenticate()` method that has one job. It takes an Authentication object and returns an Authentication object with `authenticated=true` if the input was successful, and it throws an `AuthenticationException` if it was invalid.

The default implementation of `AuthenticationManager` is `ProviderManager`. This consults a series of `AuthenticationProvider` objects. There is a lot of configuration that can be done to set up these objects and implementations.

## Authorization

Authorization checks whether a user is allowed to perform an action on a resource. In Spring authorization is provided by a `AccessDecisionManager` interface. There are three different implementations provided by the framework. The interface exposes a `vote` method which takes an `Authentication` object, a generic object representing some resource the user wishes to access, and a `Collection<ConfigAttribute>`, a collection of attributes that represents the set of users or roles that are able to perform certain actions on it. These `ConfigAttributes` are often written in Spring Expression Language, which is a domain-specific language for expressing security expressions.

# WebSockets

Websockets is alternative protocol to HTTP that transfers data in both directions in real time. We can set up Websockets in a Spring MVC app using STOMP, a prototol that sits above websockets.

The messages needs a representation as a Java class. The message data will actually be transmitted as a JSON object but needs to be represented as a Java object for us to work with it using STOMP. We need classes that represent both the message that the server sends to the client, and the message that the client sends to the server.

Then you set up the controller much like a plain HTTP controller.

On the browser end we can use various libraries for websockets, including `SockJS` with `STOMP`.
