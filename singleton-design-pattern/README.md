<h1>
  <span class="headline">Singleton Design Pattern in Java</span>
  <span class="subhead">Singleton Design Pattern</span>
</h1>

**Learning objective:** By the end of this lesson, you'll be able to identify the problem contexts, during your programming tasks, in which the singleton design pattern is the best solution.

## Problem: An application logger

To illustrate the singleton pattern in action, let's consider the classic example: a logger to print events throughout an application to the console. A logger typically needs to be a singleton because it often accesses a shared resource, such as a console, file or a network connection.

## The singleton design pattern

### Singleton design pattern components

- **One private static instance** to hold the single instance of the class.
- **One private constructor** that restricts instantiation from outside the class.
- **One public static method** that provides global access to the single instance 

### Most suitable problem contexts to use singleton design pattern
In some applications, there might be scenarios where we need:
- **Shared resources**: To manage global application states such as configuration, database connections, or logging.
- **Single-point access to objects**: To control resources such as printer queue.
- **A consistent object used throughout the program**: In order to prevent multiple instances that could create inconsistency. For example: A single 'Settings' object in a mobile operating system.
- **Heavy Object Initialization:** Memory expensive objects that should be created only once to avoid performance overhead.

The Singleton design pattern guarantees that there's only one instance with a unique identifier, which helps prevent naming issues. Restricting the instantiation of a class to a single object ensures consistent behavior and control shared resources. Without restriction, multiple objects of the class can be created, leading to problems like:
- **Resource overuse**: Duplicate objects increase memory usage.
- **Inconsistant States**: Multiple instances can modify shared resources and cause inconsistency in the state of the objects.

This is the best design pattern for our application logger problem.

### When NOT to use singleton design pattern
- **When Single Responsibility Principle (SRP) can't be violated**: Singleton combines object creation logic with its functional behavior, potentially breaking SRP.
- **When the class needs to be thoroughly unit tested**: Singletons make unit testing difficult since they introduce global state (which is generally discouraged in software design principles).
- **When a class needs to allow inheritance in order to evolve a lot in the future**: Singleton tightly couples the code, which makes it harder to refactor or replace with another implementation.