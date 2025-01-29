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


### P --- The Liskov Substitution Principle (LSP)

```swift
enum YearState {
    case `init`
    case start
    case finished
}

protocol YearTask {
    var state: YearState { get set }
    func start()
    func finish()
}

class Year2024: YearTask {
    lazy var state: YearState = .start {
        didSet {
            let announcement = switch state {
            case .`init`: "2024 init"
            case .start: "2024 is started 🏁🏁🏁"
            case .finished: "2024 is finished 🎉🎉🎉"
            }
            print(announcement)
        }
    }

    func start() {
        state = .start
    }

    func finish() {
        state = .finished
    }
}

class Year2025: YearTask {
    lazy var state: YearState = { .start }() {
        didSet {
            let announcement = switch state {
            case .`init`: "2025 init"
            case .start: "2025 is started 🏁🏁🏁"
            case .finished: "2025 is finished 🎉🎉🎉"
            }
            print(announcement)
        }
    }

    func start() {
        state = .start
        tryMyBest()
    }

    func finish() {
        state = .finished
    }

    func tryMyBest() {
        // Do it in 2025
    }
}

final class YearFactory {
    static func createYearTask(_ current: Int) -> YearTask? {
        switch current {
        case 2024: Year2024()
        case 2025: Year2025()
        default: Year2024()
        }
    }
}

func main() {
    var year = 2024
    let oldYear = YearFactory.createYearTask(year)
    oldYear?.finish()
    year += 1
    let newYear = YearFactory.createYearTask(year)
    newYear?.start()
}
```
