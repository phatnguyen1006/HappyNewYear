# HappyNewYear_2025

Chúc một năm Sức Khỏe dồi dào, Tài Lộc đầy nhà, và Thành Công nối dài như 🐍🐍🐍

Hy vọng năm nay, mọi người sẽ vượt qua mọi thử thách, sáng tạo không ngừng và gặt hái thêm nhiều thành tựu mới.

Vui như Tết, việc suôn sẻ, mọi ước mơ đều sớm thành hiện thực 🚀 🚀 🚀

✨ Chúc mừng năm mới Ất Tỵ 2025! ✨

## Topic Ất Tỵ

Choose a principle from the SOLID principles and provide a sample code example to illustrate it clearly.

### Single Responsibility Principle (Leong)

A class should have only one reason to change.

This principle emphasizes that a class should have a single, well-defined responsibility. If a class has multiple responsibilities, it becomes harder to maintain and test as changes in one responsibility can inadvertently affect others.

Sample code: 

```kotlin
data class Customer(val name: String, val email: String, var address: String) {
    fun updateAddress(newAddress: String) {
        address = newAddress
    }
}

class EmailSender {
    fun sendWelcomeEmail(customer: Customer) {
        // Logic to send a welcome email to the customer
        println("Sending welcome email to ${customer.name}") 
    }
}

class PurchaseCalculator {
    fun calculateTotalPurchases(customer: Customer): Double {
        // Logic to calculate the total amount spent by the customer
        // (This would typically involve accessing a database or external service)
        return 0.0 // Placeholder
    }
}
```

Advantages:
 - Improved Maintainability: If the email sending logic changes, only the `EmailSender` class needs modification. Similarly, changes to purchase calculation logic only affect the `PurchaseCalculator`.
 - Increased Testability: Each class can be tested independently, making it easier to identify and isolate bugs.
 - Enhanced Reusability: The `EmailSender` and `PurchaseCalculator` classes can be potentially reused in other parts of the application or even in other projects.
