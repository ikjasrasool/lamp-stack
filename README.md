# LAMP Stack CRUD Application

A comprehensive web application built using the LAMP (Linux, Apache, MySQL, PHP) stack to perform CRUD (Create, Read, Update, Delete) operations. This application allows users to manage records with a clean, responsive interface.

## Features

- **Create**: Add new user records with name, email, and role
- **Read**: View all existing records in a table format
- **Update**: Edit user information through a modal interface
- **Delete**: Remove records with confirmation dialog

## Technology Stack

- **Linux**: Operating system environment
- **Apache**: Web server for hosting the application
- **MySQL**: Database management system for data storage
- **PHP**: Server-side scripting language
- **Bootstrap 5**: Front-end framework for responsive design
- **JavaScript**: Client-side interactivity

## Installation Guide

### 1. Setting Up the LAMP Stack

#### Installing Apache Web Server
```bash
sudo apt update
sudo apt install apache2
sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl status apache2
```

#### Installing MySQL
```bash
sudo apt install mysql-server
sudo systemctl start mysql
sudo systemctl enable mysql
sudo mysql_secure_installation
```

#### Installing PHP
```bash
sudo apt install php libapache2-mod-php php-mysql
sudo systemctl restart apache2
php -v
```

### 2. Creating the Database

```sql
CREATE DATABASE crud_app;
USE crud_app;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  role VARCHAR(50) DEFAULT 'User',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO users (name, email, role) VALUES
('John Doe', 'john@example.com', 'Admin'),
('Jane Smith', 'jane@example.com', 'Editor'),
('Bob Johnson', 'bob@example.com', 'User');

CREATE USER 'crud_user'@'localhost' IDENTIFIED BY 'YourSecurePassword';
GRANT ALL PRIVILEGES ON crud_app.* TO 'crud_user'@'localhost';
FLUSH PRIVILEGES;
```

### 3. Setting Up the Web Application Files

```bash
cd /var/www/html
sudo mkdir crud_app
sudo chown -R $USER:$USER crud_app
cd crud_app
```

### 4. Setting Proper Permissions

```bash
sudo chown -R www-data:www-data /var/www/html/crud_app
sudo chmod -R 755 /var/www/html/crud_app
```

## Application Structure

The application consists of a single file (`index.php`) that includes:
- Database connection configuration
- CRUD operation logic
- HTML interface with Bootstrap styling
- JavaScript for handling interactive elements

## Security Implementation

- Input validation and sanitization to prevent SQL injection
- Prepared statements for all database operations
- Error handling for database operations
- Form validation on both client and server side

## How to Use

1. Open your browser and navigate to `http://localhost/crud_app/`
2. Use the form at the top to add new records
3. View all records in the table below
4. Use the "Edit" button to modify records
5. Use the "Delete" button to remove records

## Database Schema

The application uses a simple `users` table with the following structure:

| Column | Type | Constraints |
|--------|------|-------------|
| id | INT | AUTO_INCREMENT, PRIMARY KEY |
| name | VARCHAR(100) | NOT NULL |
| email | VARCHAR(100) | NOT NULL, UNIQUE |
| role | VARCHAR(50) | DEFAULT 'User' |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP |



## Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature-name`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature-name`
5. Submit a pull request
