Introduction

A system to streamline book management in a college library. Students can register, issue, and return books easily. The backend follows a Monolithic Architecture.

Technologies Used

Maven: Dependency management
Spring Boot: REST APIs and web app development
Spring Security: Authentication & Authorization
Spring Data JPA (Hibernate): Simplified database operations
MySQL: Database
Project Lombok: Reduces boilerplate code


IDE:

Resolve dependencies with Maven.
Run SpringBootApplication.
Backend Design
Entities & Attributes
Student: student_id, country, emailId, name, age, card_id
Card: card_id, createdOn, status (ACTIVE/DEACTIVATED)
Book: book_id, isAvailable, genre, author_id
Author: author_id, country, name, emailId
User: user_id, username, password, role (STUDENT/ADMIN)
Transaction Table (N
mapping for Card and Book):

transaction_id, card_id, book_id, isIssue, status, fine, date
Functionalities
Student Controller
CRUD APIs for student data.
Change Password API: Updates default password.
Book & Author Controller
CRUD APIs for books and authors.
Transaction Controller
Issue Book: Validates card and book availability, updates transaction.
Return Book: Updates book status, calculates fine, logs return transaction.
Security
APIs protected using Spring Security.
Roles determine access:
Admin: View all students and transactions.
Student: View/update their own details, issue/return books.
Example Endpoints:

/student/all - Admin only
/student/changePassword - Student only
/transaction/issueBook - Student
