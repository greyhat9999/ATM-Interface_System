markdown
# ATM System - Java Application
![Screenshot 2025-05-27 233249](https://github.com/user-attachments/assets/0b27d359-30d4-42f0-a570-89cd29693040)

A fully functional ATM simulation system built with Java Swing and MySQL.

## Features
- 💳 User authentication with PIN verification
- 💰 Check balance, withdraw, and deposit funds
- 📊 Transaction history recording
- 🏦 MySQL database integration
- 🖥️ Clean GUI interface

## Technologies Used
- **Frontend**: Java Swing
- **Backend**: Java JDBC
- **Database**: MySQL
- **Version Control**: Git/GitHub

## How to Run
1. **Prerequisites**:
   - Java JDK 8+
   - MySQL Server 5.7+
   - MySQL Connector/J

2. ## 🗄️ Database Setup (MySQL)

This project uses MySQL for storing user and transaction data. The entire database setup is handled automatically when the application starts.

### ✅ What Gets Created Automatically

- A MySQL database named `atm_system`
- Two tables:
  - `users`
  - `transactions`

### 🧱 Table Structures

```sql
-- users table
CREATE TABLE IF NOT EXISTS users (
    user_id INT PRIMARY KEY,
    name VARCHAR(100),
    pin CHAR(64),
    balance DOUBLE
);

-- transactions table
CREATE TABLE IF NOT EXISTS transactions (
    transaction_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    type VARCHAR(20),
    amount DOUBLE,
    date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    description VARCHAR(255),
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

⚙️ Java Integration
The Java code uses a DBConnection utility that:

Connects to MySQL

Creates the atm_system database (if it doesn’t exist)

Creates the required tables automatically

No manual SQL execution is needed.

You only need to set your MySQL credentials in DBConnection.java:

java
Copy
Edit
private static final String USER = "your_mysql_username";
private static final String PASSWORD = "your_mysql_password";
Once you run the application, the database and its tables will be ready to use
   
Run the Application:

bash
git clone https://github.com/greyhat9999/ATM-Interface_System.git
cd ATMSystem
javac -cp "lib/*" src/main/java/main/App.java
java -cp "src/main/java;lib/*" main.App


Project Structure
ATMSystem/
├── src/
│   └── main/
│       ├── java/
│       │   ├── main/App.java
│       │   ├── dao/       # Database operations
│       │   ├── model/     # Data classes
│       │   └── view/      # GUI screens
│       └── resources/
├── lib/                   # MySQL Connector
├── .gitignore
└── README.md


Contributors
Vansh Chaudhary & Aryan Yadav

License
MIT License - Free for academic and personal use
