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
