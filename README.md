# SOLID Principles in Software Development

## Introduction
**SOLID** is an acronym for five principles of object-oriented design and programming. These principles, when followed, can lead to more understandable, flexible, and maintainable software. This project aims to provide an overview of each principle with examples and illustrations.

## Principles Overview
1. **S** - Single Responsibility Principle (SRP)
2. **O** - Open/Closed Principle (OCP)
3. **L** - Liskov Substitution Principle (LSP)
4. **I** - Interface Segregation Principle (ISP)
5. **D** - Dependency Inversion Principle (DIP)

---

## 1. Single Responsibility Principle (SRP)
A class should have one, and only one, reason to change. This means that a class should only have one job or responsibility.

### Example
```dart
// Before applying SRP
class Invoice {
  void calculateTotal() { /* ... */ }
  void printInvoice() { /* ... */ }
  void saveToDatabase() { /* ... */ }
}

// After applying SRP
class Invoice {
  void calculateTotal() { /* ... */ }
}

class InvoicePrinter {
  void printInvoice(Invoice invoice) { /* ... */ }
}

class InvoiceRepository {
  void saveToDatabase(Invoice invoice) { /* ... */ }
}


```
---

## 2. Open/Closed Principle (OCP)
Software entities should be open for extension but closed for modification. This means you should be able to add new functionality without changing existing code.

### Example
```dart
// Before applying OCP
class Rectangle {
  void draw() { /* ... */ }
}

class Circle {
  void draw() { /* ... */ }
}

// After applying OCP
abstract class Shape {
  void draw();
}

class Rectangle extends Shape {
  @override
  void draw() { /* ... */ }
}

class Circle extends Shape {
  @override
  void draw() { /* ... */ }
}
```
---

## 3. Liskov Substitution Principle (LSP)
Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

### Example
```dart
// Before applying LSP
class Bird {
  void fly() { /* ... */ }
}

class Ostrich extends Bird {
  @override
  void fly() {
    // Ostrich can't fly, so this would be a problem
  }
}

// After applying LSP
abstract class Bird {
  void move();
}

class Sparrow extends Bird {
  @override
  void move() {
    fly();
  }
  
  void fly() { /* ... */ }
}

class Ostrich extends Bird {
  @override
  void move() {
    run();
  }
  
  void run() { /* ... */ }
}

```
---

## 4. Interface Segregation Principle (ISP)
A client should not be forced to implement interfaces they do not use. Instead of one fat interface, many small interfaces are preferred based on groups of methods with specific behaviors.

### Example
```dart
// Before applying ISP
abstract class Worker {
  void work();
  void eat();
}

// After applying ISP
abstract class Workable {
  void work();
}

abstract class Eatable {
  void eat();
}

class Robot implements Workable {
  @override
  void work() { /* ... */ }
}

class Human implements Workable, Eatable {
  @override
  void work() { /* ... */ }
  
  @override
  void eat() { /* ... */ }
}
```
---

## 5. Dependency Inversion Principle (DIP)
High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

### Example
```dart
// Before applying DIP
class MySQLConnection {
  void connect() { /* ... */ }
}

class PasswordReminder {
  final MySQLConnection dbConnection;

  PasswordReminder(this.dbConnection);
}

// After applying DIP
abstract class DatabaseConnection {
  void connect();
}

class MySQLConnection implements DatabaseConnection {
  @override
  void connect() { /* ... */ }
}

class PasswordReminder {
  final DatabaseConnection dbConnection;

  PasswordReminder(this.dbConnection);
}
