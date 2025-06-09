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

2. **Database Setup**:
   ```sql
   CREATE DATABASE atm_system;
   USE atm_system;
   
   CREATE TABLE users (
       user_id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       pin VARCHAR(255) NOT NULL,
       balance DECIMAL(15, 2) DEFAULT 0.00
   );
   
   CREATE TABLE transactions (
       transaction_id INT AUTO_INCREMENT PRIMARY KEY,
       user_id INT NOT NULL,
       type ENUM('WITHDRAWAL', 'DEPOSIT', 'TRANSFER') NOT NULL,
       amount DECIMAL(15, 2) NOT NULL,
       timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
       description VARCHAR(255),
       FOREIGN KEY (user_id) REFERENCES users(user_id)
   );
   
   -- Test user (PIN: 1234)
   INSERT INTO users (name, pin, balance) 
   VALUES ('John Doe', SHA2('1234', 256), 1000.00);

   
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
