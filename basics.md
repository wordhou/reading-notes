# Java classes

Files can define a class (or multiple classes). There must be a class with a name that exactly matches the file name. That classes `main` method is the method executed when the class is compiled and run with `javac` and `java`.

All functions are class methods in Java.

# Compiling and running

Java is a compiled language where code is compiled down to an intermediate bytecode. This intermediate bytecode is then run by the Java Virtual Machine. This feature makes compiled java bytecode more portable, as bytecode can be run on any machine with a JVM installed.

Compliling a file is done with `javac ClassName.java`. This creates a complied `.class` file that can then be run by running `java ClassName`.

# Variables

In Java there are four kinds of variables: non-static (or instance) fields, static fields, local variables, and method parameters. Static and instance fields will be covered in more depth later. Local variables are variables declared within the scope of a method.

# Primitives

Java has only the following primitives:

| Type    |    Size |                Values                 |
| :------ | ------: | :-----------------------------------: |
| boolean |   1 bit |           `true` or `false`           |
| byte    |  8 bits |              -128 to 127              |
| short   | 16 bits | -2<sup>15</sup> to 2<sup>15</sup> - 1 |
| int     | 32 bits | -2<sup>31</sup> to 2<sup>31</sup> - 1 |
| long    | 64 bits | -2<sup>63</sup> to 2<sup>63</sup> - 1 |
| float   | 32 bits |      Plus or minus around 10^100      |
| double  | 64 bits |      Plus or minus around 10^300      |
| char    | 16 bits |     Any UTF-16 encoded character      |

Interestingly the language makes a design choice to not have any primitive unsigned integer types. Reading into some of the [motivations](https://stackoverflow.com/questions/430346/why-doesnt-java-support-unsigned-ints#430357) of the language designers, I've found that the goal in not including unsigned integers seems to be summed as "We don't want our language to be complicated or confusing like C." I don't love this design decision, but it seems there are ways to work around this when unsigned arithmetic is needed.

# Documentation

The Oracle Java docs are an indispensable resource. They can be searched, and give all method signatures and explanations about the classes and methods in the java standard library.
