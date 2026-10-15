student-app-Valian-Athalla-Syahputra

# Student Management App

A web-based student data management app with **relational CRUD**, **login**, and **role-based access** (admin / staff).
Built for the Web Programming practicum (Session 6).

## Features

- CRUD for student records (NIM, name, major)
- Majors stored in a separate table (one-to-many relationship using `FOREIGN KEY` and `JOIN`)
- Login with hashed passwords (`password_hash` / `password_verify`) and `$_SESSION`
- `admin` and `staff` roles:

  | Action | admin | staff |
  |--------|:-----:|:-----:|
  | View dashboard | ✅ | ✅ |
  | Add / edit students | ✅ | ✅ |
  | Delete students | ✅ | ❌ |
  | Manage users (`users.php`) | ✅ | ❌ |

- Basic security: prepared statements (SQL injection protection), `htmlspecialchars()` (XSS protection), server-side role checks

## Tech Stack

HTML, CSS, Vanilla JS, PHP (procedural MySQLi), MariaDB/MySQL (XAMPP), Bootstrap 5

## Getting Started

1. Install [XAMPP](https://www.apachefriends.org/) and start **Apache** and **MySQL** in the XAMPP Control Panel.
2. Copy this project folder to `C:\xampp\htdocs\student-app`.
3. Open `http://localhost/phpmyadmin` and create the base database and table:
   ```sql
   CREATE DATABASE IF NOT EXISTS db_school;
   USE db_school;
   CREATE TABLE IF NOT EXISTS students (
     id INT AUTO_INCREMENT PRIMARY KEY,
     nim VARCHAR(20) NOT NULL,
     name VARCHAR(100) NOT NULL,
     major VARCHAR(50) NOT NULL
   );
   ```
4. Still in phpMyAdmin (database `db_school`), run the contents of **`database_sesi6.sql`**.
5. Open `http://localhost/student-app/seed_admin.php` **once** to create the first admin account, then **delete `seed_admin.php`**.
6. Open `http://localhost/student-app/` and log in.

## Default Account

| Username | Password | Role |
|----------|----------|------|
| admin | admin123 | admin |

Staff accounts can be created from the **Users** page after logging in as admin.

## Database Configuration

Edit `config.php` (XAMPP defaults: user `root`, empty password, database `db_school`).

## Project Structure

```
student-app/
├── config.php          # database connection
├── database_sesi6.sql  # schema: majors, students, users
├── seed_admin.php      # creates the first admin (run once)
├── auth.php            # login guard + role helpers
├── navbar.php          # shared navbar
├── login.php / logout.php
├── index.php           # dashboard (JOIN)
├── create.php / edit.php / delete.php
└── users.php           # user management (admin only)
```

## Author

Name: Valian Athalla Syahputra · Student ID: 5025251156
