Object oriented programming is a widely used and heavily emphasized paradigm in software development, based on the idea of bundling data and code together into _objects_.

# Objects

In Java, values are either objects or primitives. An object bundles together a series of data values (its fields) and code (its methods) which together model some concept or object. A key concept of objects is that they represent and encapsulate _state_ and _behavior_. It's believed that object oriented design has a number of benefits for software design, including code reusability, separation of concerns, and modularity.

# Classes

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

# Inheritance

Inheritance provides a way to specialize a class to encapsulate more specific state or behavior. We do so by created a subclass of an existing class:

```
   class SubClass extends BaseClass {
     // additional fields, methods which specialize the base class
   }
```

Our subclass may implement any additional fields and methods that specialize its behavior against the base class. This lets us reuse the fields and methods from the base class without having to rewrite the shared code. There are a couple of intricacies to note when extending a class in Java.

A subclass does not inherit the constructor from its base class. The subclass needs its own constructor, although can run its base classes' subclass.

# Interfaces

Interfaces are a set of requirements on the behavior of an object. Interfaces do not actually implement anything (except for default parameters or constants), and they can't be instantiation. Interfaces have to be implemented by a class. They allow us to write methods that take an interface parameter, which gives us polymorphism, since the method can take any class that implements that interface.

To define an interface we declare any interface constants and then the method signatures of the methods an implementing class is required to have.

Conceptually interfaces are used to define a _contract_ on what's expected from a class. If a class implements an interface, then it fulfills that contract, which then allows it to be used in any method that takes that interface.

Interfaces can be extended to further specify its requirements. This creates a new interface that has all of the requirements of the original interface and possibly more.
