<h1>
  <span class="headline">Singleton Design Pattern in Java</span>
  <span class="subhead">Singleton Pattern in Action</span>
</h1>

**Learning objective:** By the end of this lesson, you'll be able to identify the problem contexts, during your programming tasks, in which the Singleton design pattern is the best solution.

## Application logger Implementation


### `logger` class definition:

```java
public class Logger {
    // Static member to hold a single instance
    private static Logger instance;

    // Private constructor to prevent instantiation from outside the class
    private Logger() {
    }

    // Public method to provide global access to the instance
    public static Logger getInstance() {
        //A check for existence of a logger object before instantiating to ensure no new instances are created
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

### `logger` object usage in a `Main` class:

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
