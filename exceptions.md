Exceptions are a way to represent exceptional events, and are used to handle the control flow of a program at runtime. Conceptually they are different from an error, which represents some irrecoverable or unforseen failure of the program. Conceptually exceptions are events that the developer anticipates and then handles in the normal flow of the program.

A typical example is checking the filesystem for a file and trying to open it if it exists. The developer would like the program to handle the scenario in which the file does not exist gracefully. The way we do this in Java is by throwing and catching exceptions.

# Throw

The throw statement throws an exception. The exception is just a Java object that inherits from the `Exception` class, which contains a message and possible other details about the exceptional event. The `Exception` class is subclassed to communicate something about the exceptional event that occurred and to give the developer more control over the control flow of the program.

```
throw new Exception("message");
```

# Try-catch blocks

The try-catch-finally pattern attempts to execute the block of code in the try block. If an exception is thrown in that block, program execution looks through teh catch blocks in order until it finds a catch block that matches the exception. Then it will run the code in the finally block regardless of whether an exception was thrown.

```
try {
  // Attempt to execute some code
} catch (TypeOfException e) {
  // This code is executed if an exception with type TypeOfException is thrown
} catch (SomeOtherException e) {
  // This code is executed if a SomeOtherException is thrown
} catch (Exception e) {
  // Since Exception is more general than the types above, this will catch
  // all other exceptions that haven't been caught already.
}finally {
  // This block is run after all catch blocks
  // Close files or release resources
}
```

# Method signatures

A method signatures need to declare which possible exceptions the method can throw, so that the method consumer knows which exceptions they potentially need to handle.

```
static public openFile(String fileName) throws IOException {
  // …
}
```
