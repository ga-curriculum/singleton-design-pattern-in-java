# ![[tktk Module Name] - tktk Microlesson Name](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to practice applying the Singleton design pattern to create a robust database connection manager, ensuring a single instance manages a database connection. 

### Code along : Singleton design pattern in action (20 minutes)

To illustrate the Singleton pattern in action, let's consider a classic example: a database connection manager. In many
applications, maintaining a single database connection pool is crucial for resource management and performance
optimization. Using the Singleton pattern, we can ensure that only one connection pool instance is created and it's
accessible globally across the application.

```java
package org.example.codealong.singleton;

import java.sql.Connection;

import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseConnectionManager {
    private static DatabaseConnectionManager instance;
    private Connection connection;

    private DatabaseConnectionManager() {
        try {
            // Load the H2 database driver
            Class.forName("org.h2.Driver");

            // Establish a connection to an H2 in-memory database
            String url = "jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1";
            String user = "sa"; // Default username is 'sa'
            String password = ""; // Default password is empty
            this.connection = DriverManager.getConnection(url, user, password);
        } catch (ClassNotFoundException | SQLException e) {
            // Handle potential exceptions
            System.out.println("Database connection creation failed.");
            e.printStackTrace();
        }
    }

    public static synchronized DatabaseConnectionManager getInstance() {
        if (instance == null) {
            instance = new DatabaseConnectionManager();
        }
        return instance;
    }

    public Connection getConnection() {
        return this.connection;
    }

    public static void main(String[] args) {
        // Request a connection multiple times
        Connection conn1 = DatabaseConnectionManager.getInstance().getConnection();
        Connection conn2 = DatabaseConnectionManager.getInstance().getConnection();
        Connection conn3 = DatabaseConnectionManager.getInstance().getConnection();

        // Compare and print out the connection references
        System.out.println("Database connection 1 established: " + conn1);
        System.out.println("Database connection 2 established: " + conn2);
        System.out.println("Database connection 3 established: " + conn3);

        // Demonstrating that the DatabaseConnectionManager instance is the same
        System.out.println("Is DatabaseConnectionManager instance the same for conn1 and conn2? " +
                (DatabaseConnectionManager.getInstance() == DatabaseConnectionManager.getInstance()));

        // Comparing connection object references directly
        System.out.println("Do conn1, conn2, and conn3 refer to the same object? " +
                (conn1 == conn2 && conn2 == conn3));
    }
}


```

This setup instantiates a `DatabaseConnectionManager` Singleton that establishes a connection to an H2 in-memory
database. The Singleton ensures that only one database connection is made, and it can be accessed globally throughout
the application.