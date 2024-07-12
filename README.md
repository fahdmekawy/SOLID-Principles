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
