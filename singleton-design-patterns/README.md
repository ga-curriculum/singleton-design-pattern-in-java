# ![[tktk Module Name] - tktk Microlesson Name](./assets/singleton-design-pattern-mod.png)

**Learning objective:** By the end of this lesson, students will be able to examine the advantages and limitations of Singleton design patterns. 

### Singleton design pattern (10 minutes)

The Singleton design pattern is a sophisticated creational strategy aimed at solving a common issue in object-oriented
programming: ensuring a class generates a single instance, while also offering a universally accessible point to this
instance. It's particularly useful in scenarios where multiple objects need to coordinate actions across a system.

At the heart of the Singleton pattern is the principle of restricting object creation to one instance, thereby granting
controlled, global access to that instance. This singular control over resource instantiation is pivotal for a variety
of applications, including managing access to a shared resource, such as a file or a database connection, or when
implementing a centralized system for managing state or configurations across an application.

**Implementing the Singleton pattern involves several key steps**:

- **Private Constructor**: To prevent external instantiation, the class constructor is made `private`.
- **Private Static Instance**: The class maintains a `private`, `static` instance of itself.
- **Public Static Method**: This method, often named `getInstance()`, allows external access to the Singleton instance.
  On its first call, it creates the class instance and stores it in a static field. On subsequent calls, it returns the
  already created instance.

This design pattern ensures that the class is only instantiated once. The stored instance is returned on all future
calls to the `getInstance()` method, thus maintaining a single, global instance accessible throughout the application.

#### Advantages of Singleton Pattern (10 minutes):

- Controlled Access: It provides a controlled access point to a shared resource, ensuring that concurrent access does
  not create conflicting changes.
- Lazily Loaded, Memory Efficient: The instance is created only when it's needed for the first time, promoting efficient
  memory usage.
- Global State Management: Singleton offers a neat way to manage a global state or shared resources in an application.

#### Considerations and Criticisms (10 minutes):

While the Singleton pattern has its benefits, it's also subject to criticism, especially regarding its impact on
software testing, its promotion of global state (which is generally discouraged in software design principles), and
challenges in a multithreaded environment that requires careful handling to ensure the instance is created only once.

Moreover, the pattern's reliance on a global instance can introduce tight coupling between classes, making it harder to
test the classes that depend on the Singleton. This is because the pattern does not inherently provide a way to mock or
replace the Singleton instance during testing, although techniques such as dependency injection can mitigate this issue.

Despite these criticisms, the Singleton pattern remains a powerful tool in the software developer's toolkit,
particularly when its use is carefully weighed against the specific needs and constraints of the application being
designed.