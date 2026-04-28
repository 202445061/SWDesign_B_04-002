```mermaid
classDiagram

class User {
    - id: String
    - pw: String
    - name: String
    - phone: String
    - address: String

    + registerUser(id: String, pw: String, name: String, phone: String, address: String) boolean
    + updateUser(id: String, pw: String, name: String, phone: String, address: String) boolean
    + deketeUser(id: String) boolean
    + searchUser(id: String) User
}

class Account {
    - number: String
    - balance: int

    + deposit(userId: String, number: String, amount: int) boolean
    + withdraw(userId: String, number: String, amount: int) boolean
    + trabsfer(userId: String, fromNumber: String, toNumber: String, amount: int) boolean
    + computeBalance(userId: String, number: String) int
    + searchUser(userId: String) User
}

class BankUI {
    + inputUserInfo() void
    + inputAccountInfo() void
    + requestDeposit(userId: String, number: String, amount: int) void
    + requestWithdraw(userId: String, number: String, amount: int) void
    + requestTrabsfer(userId: String, fromNumber: String, toNumber: String, amount: int) void
    + requestComputeBalance(userId: String, number: String) void
}

Account "1..*" --> "1" User : searchUser
BankUI ..> Account : uses