# ![[tktk Module Name] - tktk Microlesson Name](./assets/singleton-code-along.png)

**Learning objective:** By the end of this lesson, students will be able to practice applying the Singleton design pattern to create a robust database connection manager and ensure that a single instance manages a database connection. 

### Code along : Singleton design pattern in action (20 minutes)

To illustrate the Singleton pattern in action, let's consider a classic example: a logger class. A Logger class typically needs to be a singleton because it often accesses a shared resource, such as a file or a network connection. Steps to implement the Singleton pattern in the Logger class:

- A private constructor is used to prevent instantiation from outside the class.
- Private static member to hold a single instance of the class.
- A public static method provides global access to the instance.

```java
package org.example.codealong.singleton;

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

Once the Logger class is implemented as a Singleton, we can use it to log messages. 

```java
package org.example.codealong.singleton;

public class Application {
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
