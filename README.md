📚 Library Management System
Project Overview
The Library Management System is a comprehensive database solution designed to streamline the management of a library's operations. This project includes tables for handling user logins, book details, authors, publishers, staff, readers, book issuance, and library settings. The database schema is implemented in PostgreSQL.

Features
User Management: Track and manage user login credentials.
Book Catalog: Store and manage detailed information about books, including authors and publishers.
Staff Management: Maintain records of library staff, their roles, and work shifts.
Reader Management: Keep track of library members, their book issues, and fines.
Book Issuance: Record and manage the issuance and return of books, including fines for late returns.
Library Settings: Configure global library settings, including book issue limits and fine rates.
Database Schema
The database schema consists of the following tables:

1. user_login
Stores information about users who can access the library system.

Primary Key: user_id
Columns: user_password, first_name, last_name, sign_up_on, email_id
2. publisher
Holds details of book publishers and their distribution history.

Primary Key: publisher_id
Columns: publisher, distributor, releases_count, last_release
3. author
Contains information about authors who have published books in the library.

Primary Key: author_id
Columns: first_name, last_name, publications_count
4. books
Manages details of all books in the library.

Primary Key: book_id
Foreign Keys: author_id (References author), publisher_id (References publisher)
Columns: book_code, book_name, book_version, release_date, available_from, is_available
5. staff
Records information about the library staff, including their work schedules.

Primary Key: staff_id
Columns: first_name, last_name, staff_role, start_date, last_date, is_active, work_shift_start, work_shift_end
6. readers
Tracks the library’s members and their borrowing history.

Primary Key: reader_id
Columns: first_name, last_name, registered_on, books_issued_total, books_issued_current, is_issued, last_issue_date, total_fine, current_fine
7. books_issue
Logs the details of books issued to readers and associated fines.

Primary Key: issue_id
Foreign Keys: book_id (References books), issued_to (References readers)
Columns: issued_on, return_on, current_fine, fine_paid, payment_transaction_id
8. settings
Contains configuration settings for the library, such as the number of books a reader can issue and fine rates.

Columns: book_issue_count_per_reader, fine_per_day, book_return_in_days
Getting Started
Prerequisites
Ensure you have PostgreSQL installed on your machine.

Installation
Clone the Repository:

bash
Copy code
git clone https://github.com/your-username/library-management-system.git
cd library-management-system
Set Up the Database:

Connect to your PostgreSQL instance.
Execute the SQL script to create the library_management schema and all associated tables:
sql
Copy code
psql -U your_username -d your_database -f create_schema.sql
Insert Sample Data (Optional):

You can populate the tables with initial data by executing an additional SQL script if available.
Usage
Managing Users: Add, update, or delete user information in the user_login table.
Handling Books: Add new books, authors, and publishers, and manage their details.
Issuing Books: Track book issues, returns, and manage fines through the books_issue table.
Library Configuration: Adjust library-wide settings such as book issue limits and fine amounts via the settings table.
