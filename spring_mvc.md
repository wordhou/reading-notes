Spring MVC is a Java framework for serving web applications with a Model-View-Controller design architecture.

# MVC architecture

MVC refers to a Model-View-Controller design pattern for separating responsibilities in an application. The Model refers to the actual application data and encapsulates that data and its behavior. The View is responsible for rendering that data and serving it (in this application) as HTML. The Controller is responsible for handling user input and processing the input to manipulate the models and generate views.

# Developing with Spring MVC

In Spring MVC all of the HTTP requests and responses are handled by a `DispatcherServlet`, which receives HTTP requests, calls the Controller methods, which then return a string with the name of the view that will render the response. Along the way the Controller method may attach data or manipulate the underlying Model that the view will render.

What's interesting about this approach is that everything goes back to the DispatcherServlet. Instead of calling the renderer from the Controller, the view name is passed back to the DispatcherServlet which then calls the renderer. This allows all of the components (classes and methods) to be built separately from each other, each with their own concerns.

# Annotations

A Spring MVC application is structured around Annotations, which tell the DispatcherServlet how everything is hooked up.
