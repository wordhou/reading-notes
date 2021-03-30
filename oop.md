Object oriented programming is a widely used and heavily emphasized paradigm in software development, based on the idea of bundling data and code together into _objects_.

# Basic concepts

## Objects

In Java, values are either objects or primitives. An object bundles together a series of data values (its fields) and code (its methods) which together model some concept or object. A key concept of objects is that they represent and encapsulate _state_ and _behavior_. It's believed that object oriented design has a number of benefits for software design, including code reusability, separation of concerns, and modularity.

## Classes

In Java, all objects are an _instance_ of a class. The class essentially provides a blueprint for the objects of that class. The class defines the fields that each object contains, and also provides them with methods that interacts with their state in some way.

```java
public class Widget {
  // The fields of an object bundle together data that model some concept and
  // represents state.
  int size;
  int weight;
  int quantity;

  public void increaseQuantity() {
    // The methods of an object provide a way to interact with their internal
    // state in some way
  }

  // … constructor, more methods, etc.
}
```

Finally, the class itself can hold its own data and methods. These are called static fields and static methods. These methods and fields don't have access to the internal state of any of the classes' instances, but instead bundle together data and code that is relevant to the whole class.

## Inheritance

Inheritance provides a way to specialize a class to encapsulate more specific state or behavior. We do so by created a subclass of an existing class:

```
   class SubClass extends BaseClass {
     // additional fields, methods which specialize the base class
   }
```

Our subclass may implement any additional fields and methods that specialize its behavior against the base class. This lets us reuse the fields and methods from the base class without having to rewrite the shared code. There are a couple of intricacies to note when extending a class in Java.

A subclass does not inherit the constructor from its base class. The subclass needs its own constructor, although can run its base classes' subclass.

## Interfaces

Interfaces are a set of requirements on the behavior of an object. Interfaces do not actually implement anything (except for default parameters or constants), and they can't be instantiation. Interfaces have to be implemented by a class. They allow us to write methods that take an interface parameter, which gives us polymorphism, since the method can take any class that implements that interface.

To define an interface we declare any interface constants and then the method signatures of the methods an implementing class is required to have.

Conceptually interfaces are used to define a _contract_ on what's expected from a class. If a class implements an interface, then it fulfills that contract, which then allows it to be used in any method that takes that interface.

Interfaces can be extended to further specify its requirements. This creates a new interface that has all of the requirements of the original interface and possibly more.

# SOLID principles

The SOLID principles are a set of five principles that represent "good practice" in object oriented design.

## Single responsibility principle

A class or module should focus on doing one "thing". A class or module with a single responsibility is easier to substitute out or reuse in other settings, and requires less rewriting when changes are made to the code base.

## Open/closed principle

Code should be easy to extend without internal modification. In OOP this is usually accomplished with inheritance and interfaces. When we want to extend the functionality of a class we can extend it, or substitute in more specialized dependencies that satisfy the same interfaces. This makes it easier to incrementally improve or specialize code while minimizing the amount of code that has to be rewritten.

## Liskov substitution principle

This principle means that any subtype S of a type T should be substitutable in any situation where T would be acceptable. In object oriented programming this means that subclasses should still work in any situation where the parent would work and a class that satisfies an extended interface should work in any situation where a class that satisfies the base interface would as well. This principle enables type polymorphism, which lets us write code that handles a number of different types which specialize some base type.

## Interface segregation principle

Interfaces should be as "small" as possible while still allowing whatever logic to be performed to be performed. Multiple smaller interfaces should be favored over fewer larger more restrictive interfaces. When we say "small" we mean the number of restrictions the interface places on an implementing class. If you're consuming a library that requires your code to satisfy one large interface with many requirements that you don't actually need, then you're writing wasted code to satisfy an interface that's too large. If instead that interface was broken up into smaller interfaces that each allowed you to consume some subset of the library, you could choose to implement only the interfaces that you need.

This is a principle that applies beyond object oriented programming. It also is closely related to another principle called "composition over inheritance", which means that we should prefer _composing_ multiple interfaces to define the behavior of our class over multiple inheritance. By using multiple smaller interfaces, we ensure that our class works where we need it to work while not having to subclass or specialize functionality that we don't need. While this concept is debated, the principle is reflected in the language design of Golang and Rust, which both favor interfaces and traits respectively and eschew the traditional object oriented principle of inheritance.

## Dependency inversion

Code should depend on abstractions rather than implementations. This gives our code generality and allows us to change implementation details of dependencies without having to rewrite upstream. This is a general programming principle that extends well beyond object oriented programming. Common examples of this include iterators and streams. When we write functions that depends on an iterator versus an array, for example, we can then substitute out that array for a linked list or a hash set or any data structure that implements the Iterator interface. This principle is usually enabled by requiring that dependencies satisfy an interface and then consuming that interface.
