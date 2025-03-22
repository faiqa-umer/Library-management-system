# 📚 Library Management System

Welcome to the **Library Management System**! This project is a simple yet efficient library management software designed using **Java** with **MySQL** for database management. The GUI is built using **NetBeans**.

---

## 🚀 Features
- 📖 **Book Management** *(Add, Update, Delete, Search)*
- 🧑 **Member Management**
- 🔎 **Book Search and Issue/Return**
- 🗃️ **Database Integration using JDBC**

---

## 🛠️ Prerequisites
Before running the project, ensure you have the following installed:

- ✅ **Java (JDK 8 or later)**
- ✅ **NetBeans IDE (8.2 or later)**
- ✅ **MySQL Server**
- ✅ **MySQL Connector/J** *(for JDBC)*

🔎 **[Download MySQL Connector/J Here](https://dev.mysql.com/downloads/connector/j/)**

---

## ⚙️ Setup Instructions

Follow these steps to get the project running on your system:

### Clone the Repository:
https://github.com/faiqa-umer/Library-management-system

### Open in NetBeans:
Launch NetBeans IDE.
Click on File → Open Project.
Select the project folder.

### Add MySQL Connector:
Download and install MySQL Connector/J.
Go to Project → Properties → Libraries → Add JAR/Folder.
Select the MySQL Connector .jar file.

---

### Set Up Database:
Open MySQL Workbench or any MySQL client.

### Create and configure your database using the following queries:

CREATE DATABASE library;

USE library;

 CREATE TABLE admin (
  username VARCHAR(50) PRIMARY KEY,
  full_name VARCHAR(100),
  email VARCHAR(100),
  password VARCHAR(255),
  security_question VARCHAR(100),
  security_answer VARCHAR(100)
);

 CREATE TABLE books (
  Book_id VARCHAR(50) PRIMARY KEY,
  Title VARCHAR(50),
  Author VARCHAR(50),
  Publisher VARCHAR(50),
  Edition VARCHAR(10),
  category VARCHAR(50),
  Shelf_no VARCHAR(5),
  available TINYINT(1) DEFAULT 1
);

 CREATE TABLE issuedbooks (
  id INT AUTO_INCREMENT PRIMARY KEY,
  book_id VARCHAR(50),
  book_name VARCHAR(255),
  author VARCHAR(255),
  username VARCHAR(50),
  issue_date DATE,
  FOREIGN KEY (book_id) REFERENCES books(Book_id)
);

 CREATE TABLE issuer (
  username VARCHAR(50) PRIMARY KEY,
  full_name VARCHAR(100),
  email VARCHAR(100),
  password VARCHAR(255),
  security_question VARCHAR(100),
  security_answer VARCHAR(100)
);

CREATE TABLE returnbooks (
  id INT AUTO_INCREMENT PRIMARY KEY,
  book_id VARCHAR(10),
  username VARCHAR(50),
  return_date DATE,
  FOREIGN KEY (book_id) REFERENCES books(Book_id),
  FOREIGN KEY (username) REFERENCES issuer(username)
);

### 📥 Insert Sample Data
You can insert sample data using the following SQL queries:

### Add Data to Admin Table
INSERT INTO admin (username, full_name, email, password, security_question, security_answer)
VALUES 
('admin1', 'John Doe', 'admin1@example.com', 'password123', 'What is your favorite color?', 'Blue'),
('admin2', 'Jane Smith', 'admin2@example.com', 'password456', 'What is your pet’s name?', 'Max');

### Add Data to Books Table
INSERT INTO books (Book_id, Title, Author, Publisher, Edition, category, Shelf_no, available)
VALUES 
('B001', 'Introduction to Java', 'Herbert Schildt', 'McGraw Hill', '10th', 'Programming', 'A1', 1),
('B002', 'Database Management Systems', 'Raghu Ramakrishnan', 'McGraw Hill', '3rd', 'Database', 'B2', 1),
('B003', 'Data Structures and Algorithms', 'Robert Lafore', 'Pearson', '2nd', 'Computer Science', 'C3', 1);

### Add Data to Issuer Table
INSERT INTO issuer (username, full_name, email, password, security_question, security_answer)
VALUES 
('user1', 'Alice Johnson', 'alice@example.com', 'userpass123', 'What is your mother’s maiden name?', 'Clark'),
('user2', 'Bob Williams', 'bob@example.com', 'userpass456', 'What city were you born in?', 'New York');

### Add Data to Issued Books Table

INSERT INTO issuedbooks (book_id, book_name, author, username, issue_date)
VALUES 
('B001', 'Introduction to Java', 'Herbert Schildt', 'user1', '2025-03-15'),
('B002', 'Database Management Systems', 'Raghu Ramakrishnan', 'user2', '2025-03-18');

### Add Data to Return Books Table
INSERT INTO returnbooks (book_id, username, return_date)
VALUES 
('B001', 'user1', '2025-03-22'),
('B002', 'user2', '2025-03-25');

---

### 🛠️ Update Database Connection
Open ConnectionClass.java.
Update your database credentials with the following:

String url = "jdbc:mysql://localhost:3306/library";
String user = "your_username";
String password = "your_password";

---

### 🚦 Running the Project
✅ Ensure MySQL server is running.

✅ In NetBeans, right-click on the project → Run.

✅ The login screen will appear. Enter admin credentials or register a new user.
---

### 🧑‍💻 Troubleshooting
❗ MySQL Connector Error: Ensure you’ve correctly added the .jar file in your NetBeans Libraries.

❗ Database Connection Failed: Verify that MySQL is running and your database credentials are correct.

❗ Compilation Errors: Ensure JDK and NetBeans are correctly installed.

