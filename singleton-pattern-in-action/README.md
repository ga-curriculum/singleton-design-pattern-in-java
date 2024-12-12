<h1>
  <span class="headline">Singleton Design Pattern in Java</span>
  <span class="subhead">Singleton Pattern in Action</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to apply the Singleton design pattern to add functionality to an application.

### Build a logger in an application

To illustrate the Singleton pattern in action, let's consider a classic example: a logger to print events throughout an application to the console. A logger typically needs to be a singleton because it often accesses a shared resource, such as a file or a network connection.

We'll implement the Singleton pattern in the `Logger` class that includes these items:

- A private constructor is used to prevent instantiation from outside the class.
- A private static member to hold a single instance of the class.
- A public static method provides global access to the instance.

`src/main/java/org/example/Logger.java`

```java
public class Logger {
    // Static member to hold a single instance
    private static Logger instance;

    // Private constructor to prevent instantiation from outside the class
    private Logger() {
    }

    // Public method to provide global access to the instance
    public static Logger getInstance() {
        if (instance == null) {
            instance = new Logger();
        }
        return instance;
    }

    // Method to log messages
    public void log(String message) {
        System.out.println("Log: " + message);
    }
}
```

Once the `Logger` class is implemented as a Singleton, we can use it to log messages in our `Main` class.

`src/main/java/org/example/Main.java`

```java
public class Main {
    public static void main(String[] args) {
        Logger logger = Logger.getInstance();
        logger.log("Application has started.");

        // Further down in your application
        Logger anotherLoggerInstance = Logger.getInstance();
        anotherLoggerInstance.log("An action has been performed.");
    }
}
```

The `Logger` class is implemented as a Singleton in the code above. The `getInstance()` method ensures that only one instance of the `Logger` class is created and shared across the application. All parts of the application that need to log messages can access the same instance of the `Logger` class.
