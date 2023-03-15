# 1.what is the advantages of using 'spring boot' rather than 'spring' ?

Spring Boot is a framework built on top of the Spring framework that provides additional functionality and features that can make it easier and faster to develop applications.

Here are some advantages of using Spring Boot over Spring:

### Easy Configuration:
Spring Boot provides auto-configuration which makes it easier to configure the application. It also reduces the amount of boilerplate code that needs to be written.

### Faster Development: 
Spring Boot provides a range of pre-built components and modules which can be easily integrated into the application. This helps in faster development and deployment of the application.

### Embedded Server: 
Spring Boot provides an embedded server, which means that developers do not need to deploy the application on an external server. This makes it easier to develop and test the application.

### Dependency Management: 
Spring Boot provides dependency management, which makes it easier to manage dependencies in the application. It also helps in reducing conflicts between different versions of the same library.

### Integration with Other Tools: 
Spring Boot integrates with a range of tools such as Maven, Gradle, and Jenkins. This makes it easier to build, test, and deploy the application.

### Modular Architecture: 
Spring Boot provides a modular architecture which makes it easier to separate concerns and develop the application in a more organized manner.

Overall, Spring Boot can help in reducing development time, increasing productivity, and improving the quality of the application.

# 2.what is the base annotation of spring boot application?
The base annotation for a Spring Boot application is typically @SpringBootApplication. This annotation is a combination of three other annotations: @Configuration, @EnableAutoConfiguration, and @ComponentScan.

### @Configuration: 
This annotation is used to indicate that a class is a configuration class and can contain bean definitions and configuration methods.

### @EnableAutoConfiguration:
This annotation is used to enable Spring Boot's auto-configuration feature, which automatically configures beans and other components based on the dependencies on the classpath.

### @ComponentScan: 
This annotation is used to scan for Spring-managed beans within a specific package and its sub-packages.

By combining these three annotations into a single @SpringBootApplication annotation, you can create a Spring Boot application with minimal configuration and have Spring Boot automatically configure and manage many aspects of the application's runtime environment.

# 3.what are the annotations you know in spring boot?

There are many annotations available in Spring Boot, but here are some of the most commonly used ones:

### @SpringBootApplication: 
As mentioned earlier, this annotation combines @Configuration, @EnableAutoConfiguration, and @ComponentScan annotations into a single annotation.

### @RestController: 
This annotation is used to indicate that a class is a RESTful controller that is responsible for handling HTTP requests.

### @RequestMapping: 
This annotation is used to map an HTTP request to a specific method or controller.

### @GetMapping, @PostMapping, @PutMapping, @PatchMapping, @DeleteMapping: 
These annotations are used to map HTTP GET, POST, PUT, PATCH, and DELETE requests to specific methods in a controller.

### @RequestBody: 
This annotation is used to indicate that a method parameter should be bound to the body of the HTTP request.

### @PathVariable: 
This annotation is used to indicate that a method parameter should be bound to a variable in the URL path.

### @RequestParam: 
This annotation is used to indicate that a method parameter should be bound to a query parameter in the URL.

### @Autowired: 
This annotation is used to indicate that a bean should be automatically injected into a class.

### @Component: 
This annotation is used to indicate that a class is a Spring-managed component.

### @Service: 
This annotation is used to indicate that a class is a Spring-managed service.

### @RestController: 
This annotation is used to mark a class as a REST controller, which automatically maps HTTP requests to methods in the class.

### @Repository: 
This annotation is used to mark a class as a repository component.

### @Value: 
This annotation is used to inject values from external configuration files or system properties.

### @Transactional: 
This annotation is used to mark a method as transactional.

### @EnableAsync: 
This annotation is used to enable asynchronous processing in a Spring Boot application.

### @ConditionalOnProperty: 
This annotation is used to conditionally enable or disable a component based on the value of a property.

### @EnableCaching: 
This annotation is used to enable caching in a Spring Boot application.

These are just a few examples of the annotations available in Spring Boot. There are many more annotations that can be used for various purposes such as security, logging, and testing.

# 3.what is @Qualifier ?

In Spring, @Qualifier is an annotation that is used to resolve ambiguity when there are multiple beans of the same type. When there are multiple beans of the same type, Spring cannot determine which bean to inject into a dependency, and an error is thrown.

To resolve this ambiguity, you can use the @Qualifier annotation along with the @Autowired annotation. The @Qualifier annotation allows you to specify a unique name or value for the bean that you want to inject.

### Here's an example:

        @Component
        public class Foo {
           // ...
        }

        @Component
        public class Bar {
           // ...
        }

        @Component
        public class MyComponent {
            private final Foo foo;
            private final Bar bar;

            public MyComponent(@Qualifier("foo") Foo foo, @Qualifier("bar") Bar bar) {
                this.foo = foo;
                this.bar = bar;
            }

            // ...
        }

In the example above, there are two beans of type Foo and Bar. When injecting the beans into the MyComponent class constructor, we use the @Qualifier annotation to specify which bean to inject. By providing a unique name or value, Spring knows which bean to inject and the ambiguity is resolved.

# 4.what is the difference between @Controller and @RestController?
In Spring, both @Controller and @RestController are used to handle HTTP requests and map them to methods in your application. However, there is a key difference between these two annotations.

The @Controller annotation is used to mark a class as a Spring MVC controller. It is typically used to create web pages that generate HTML responses. Methods in a @Controller class typically return a String representing the name of the view that should be rendered.

The @RestController annotation, on the other hand, is used to mark a class as a controller that is designed specifically to handle RESTful web services. It is typically used to create APIs that return data in formats such as JSON or XML. Methods in a @RestController class typically return the actual data that should be sent as the response body.

In summary, @Controller is used for traditional web applications that generate HTML responses, while @RestController is used for creating RESTful web services that return data in different formats.
# 5.what is @Entity

In Spring, @Entity is an annotation that is used to mark a class as a JPA (Java Persistence API) entity. A JPA entity is a lightweight, POJO (Plain Old Java Object) class that represents a table in a database.

The @Entity annotation is typically used in combination with other annotations such as @Id, @GeneratedValue, @Column, and @OneToMany to define the mapping between the entity class and the corresponding database table.

### Here's an example:
          @Entity
          public class User {
             @Id
             @GeneratedValue(strategy = GenerationType.IDENTITY)
             private Long id;

             @Column(name = "username")
             private String username;

             @Column(name = "password")
             private String password;

             // getters and setters
          }
