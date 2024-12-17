<h1>
  <span class="headline">Singleton Design Pattern in Java</span>
  <span class="subhead">What Is a Design Pattern</span>
</h1>

**Learning objective:** By the end of this lesson, you will be able to describe what design patterns are in the domain of software engineering.

## What is a design pattern?

A design pattern is an existing, time-tested, re-usable and most elegant solution to a frequently encountered design problem. It is not as abstract a programming paradigm and not as concrete as an algorithm. It is a set of guidlines on the decisions the need to be taken, in terms of the components and behaviour that should exist (or, in some cases, should not exist).

OOP design patterns are grouped into three main categories:

- **Creational patterns** focus on solving design problems related to object creation.
- **Structural patterns** focus on solving design problems related to organising classes and objects to form a larger structure with specific goals. 
- **Behavioral patterns** focus on solving design problems related to interaction and communication between objects and classes.

The approach of identifying the most appropriate design pattern for problem-solving not only enhances code efficiency and readability but also facilitates the development process by providing tested and proven approaches to solve problems.

## Solving a design problem

### Step 1: Problem definition
To solve a design problem, we need to be able to clearly articulate our problem in the right context. This is done using "How might we" questions?
- For example: How might we create a class that can be instantiated to only only object even when multiple developers try to instantiate it multiple times. (so that we can use that object as our application log.)

### Step 2: Design pattern selection
This step involves looking at our collection of design patterns and choosing the most appropriate pattern. 
- For example: For the application log problem, we will need to create a class from which only one object can be instantiated. This is related to creation of classes and objects. So we narrow down our search to the collection of Creational design patterns.  

### Step 3: Programmatic implementation
The final step is realising the design pattern in form of Java code.
