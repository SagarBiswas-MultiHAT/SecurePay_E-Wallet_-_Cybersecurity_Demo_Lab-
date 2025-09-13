# SecurePay E-Wallet & Cybersecurity Demo Lab

<p align="center">
  <img src="./imgs/SecurePAY.png" alt="SecurePay Logo" width="180"/>
</p>

## 🚀 Project Overview

**SecurePay** is a beginner-friendly, full-stack PHP web app that simulates a secure E-Wallet system and a Cybersecurity Attack Demo Lab. It is designed for learning secure coding practices and understanding common web vulnerabilities. The project is modular, with clear separation between authentication, wallet, admin, and cybersecurity demo features. **No frameworks required.**

---

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Demo & Screenshots](#-demo--screenshots)
- [Folder Structure](#-folder-structure)
- [Features](#features)
- [Setup](#setup)
- [Usage](#usage)
- [Admin Panel](#admin-panel)
- [Cybersecurity Lab](#cybersecurity-lab)
- [Troubleshooting](#troubleshooting)
- [Conventions & Security](#conventions--security)
- [Developer Notes](#developer-notes)
- [License](#license)

---

## 🎬 Demo & Screenshots

> _Add your screenshots or a demo GIF here!_

---

## 🗂️ Folder Structure

```
SecurePay_E-Wallet_&_Cybersecurity_Demo_Lab/
├── add_funds.php
├── history.php
├── index.php
├── make_sagar_admin.sql
├── readMe.md
├── SecurePay_E-Wallet_&_Cybersecurity_Demo_Lab.zip
├── send_money.php
├── users_table.sql
├── wallets_transactions_tables.sql
├── withdraw.php
├── admin/
│   ├── index.php
│   ├── login.php
│   ├── logout.php
│   └── users.php
├── assets/
│   ├── css/
│   │   ├── adminStyle.css
│   │   └── style.css
│   └── js/
│       └── validate.js
├── auth/
│   ├── login.php
│   ├── logout.php
│   └── register.php
├── cyberlab/
│   ├── index.php
│   ├── secure_toggle.php
│   ├── xss_demo.php
│   └── for_stole_data/
│       ├── attack.html
│       ├── server.js
│       ├── session_hijacking.md
│       ├── session_hijacking.php
│       └── XSS_Payloads.md
├── dashboard/
│   └── index.php
├── imgs/
│   ├── SecurePAY.png
│   └── send-money.png
├── includes/
│   ├── db_connect.php
│   └── functions.php
├── test/
│   ├── passTOhash.php
│   └── sessionUserName.php
```

---

## ✨ Features

- **User Authentication:** Registration, login, logout (session-based, password hashing)
- **E-Wallet:** Add funds, send money, view transaction history (secure, server-side validation)
- **Dashboard:** Balance, recent transactions, frequent recipients
- **Cybersecurity Lab:**
  - [XSS Demo](./cyberlab/xss_demo.php)
  - [SQLi Demo](./cyberlab/sqli_demo.php) _(add if available)_
  - Toggle secure/vulnerable mode via [secure_toggle.php](./cyberlab/secure_toggle.php)
- **Admin Panel:** Dashboard, user management, transaction logs (with prepared statements)
- **Responsive UI:** Minimalist, fintech-inspired (HTML/CSS)
- **MySQL Database:** Users, wallets, transactions

---

## 🛠️ Setup

1. **Import SQL Tables:**
   - Import [`users_table.sql`](./users_table.sql) and [`wallets_transactions_tables.sql`](./wallets_transactions_tables.sql) into your MySQL database.
2. **Configure Database:**
   - Update DB credentials in [`includes/db_connect.php`](./includes/db_connect.php).
3. **Run the App:**
   - With PHP built-in server:
     ```sh
     php -S localhost:8000
     ```
   - Or use XAMPP and visit: [http://localhost/Web_Tech_Project/](http://localhost/Web_Tech_Project/)

---

## 🧑‍💻 Usage

- **Main App:** [http://localhost/Web_Tech_Project/](http://localhost/Web_Tech_Project/)
- **Admin Panel:** [http://localhost/Web_Tech_Project/admin/index.php](http://localhost/Web_Tech_Project/admin/index.php) _(admin login required)_
- **User Management:** [http://localhost/Web_Tech_Project/admin/users.php](http://localhost/Web_Tech_Project/admin/users.php)
<!-- Transaction Logs page removed -->
- **Cyber Lab:** [http://localhost/Web_Tech_Project/cyberlab/](http://localhost/Web_Tech_Project/cyberlab/) _(toggle secure/vulnerable mode)_

> _Default admin credentials (for demo):_
>
> - **Username:** `admin`
> - **Password:** `admin123`  
>   _(Change after first login!)_

---

## 🛡️ Admin Panel

- [`/admin/index.php`](./admin/index.php): Dashboard with user, wallet, and transaction stats
- [`/admin/users.php`](./admin/users.php): Manage users (reset password, block/unblock, delete)
<!-- /admin/transactions.php removed -->
- All admin features use prepared statements and check for column existence to avoid errors

---

## 🧪 Cybersecurity Lab

- [`/cyberlab/xss_demo.php`](./cyberlab/xss_demo.php): XSS Demo
- [`/cyberlab/sqli_demo.php`](./cyberlab/sqli_demo.php): SQL Injection Demo _(if available)_
- Toggle secure/vulnerable mode using [`secure_toggle.php`](./cyberlab/secure_toggle.php) and `isSecureMode()`
- Demos are self-contained, with clear UI and educational comments

---

## 🛠️ Troubleshooting

- **"Not Found" errors:** Check your URL and project folder location. Ensure XAMPP/Apache is running and the project is in the correct directory.
- **Database errors:**
  - "Unknown column ... in field list": Update your table or code to match column names.
  - "Access denied": Check your DB credentials in `db_connect.php`.
- **PHP errors:**
  - Undefined array key warnings: The code will show "-" for missing fields.
  - Session issues: Make sure PHP sessions are enabled in your `php.ini`.
- **Static files not loading:** Check resource paths and that `assets/` and `imgs/` folders are present.

---

## 🔒 Conventions & Security

- All user input is sanitized server-side ([`includes/functions.php`](./includes/functions.php))
- All DB operations use prepared statements
- Use `$_SESSION['user_id']` for user context
- Success/error messages shown in styled alert boxes (`.alert.success`, `.alert.error`)
- All forms use POST and basic HTML validation; some have additional JS validation ([`assets/js/validate.js`](./assets/js/validate.js))
- Minimalist, fintech-inspired UI ([`assets/css/style.css`](./assets/css/style.css))
- All protected pages call `require_login()` and implement session timeout (5 min inactivity)
- `require_login()` ensures correct login redirect for both user and admin
- UI consistency: transaction sign formatting, column alignment, card background color, CSS variable usage, image/logo display, and error handling
- All resource paths (images, CSS, JS) are checked and corrected for each module
- All code is commented for beginners; educational notes in Cyber Lab demos and admin panel

---

## 🧑‍💻 Developer Notes

- To add a new secure/vulnerable demo, follow the pattern in [`cyberlab/xss_demo.php`](./cyberlab/xss_demo.php) and use `isSecureMode()`
- For new wallet actions, use prepared statements and update both `wallets` and `transactions` tables
- For new admin features, check for column existence before querying, and handle missing columns gracefully in the UI

---

## 📄 License

MIT

---

For more details, see the code in each module directory. All features are implemented with security best practices and clear comments for learning.
