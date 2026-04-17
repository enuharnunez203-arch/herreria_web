# Herrería López — Client & Order Management System (CRM)

A full-stack web application built for a local metalwork business to streamline client communication, project quoting, and order management. Replaces manual WhatsApp-based workflows with a centralized, secure platform.

---

##  Features

- **Contact & Quote Form** — Clients can submit project requests with file attachments directly from the website
- **Admin Dashboard** — Secure panel to view, manage, and track all incoming messages and orders
- **Session-based Authentication** — Protected admin area with login/logout functionality
- **File Upload System** — Validates file type (images only) and size (max 5MB) with unique naming to prevent conflicts
- **Email Notifications** — SMTP integration via PHPMailer to notify the business owner on new submissions

---

##  Security Implementation

Security was a core focus of this project:

- **SQL Injection Prevention** — All database interactions use prepared statements with `bind_param()`
- **XSS Prevention** — All output is sanitized with `htmlspecialchars()`
- **Server-side Validation** — Input validated with `filter_var()`, `trim()`, and type checks before any DB interaction
- **File Validation** — Upload handler verifies MIME type via `getimagesize()` and enforces size limits
- **Session Protection** — Admin routes check session state on every request before rendering any content

---

##  Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML, CSS, JavaScript |
| Backend | PHP |
| Database | MySQL |
| Email | PHPMailer (SMTP) |
| Server | Apache / Hostinger |

---

##  Database Schema

```sql
CREATE TABLE mensajes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    telefono VARCHAR(20),
    tipo_proyecto VARCHAR(100),
    mensaje TEXT,
    archivo_adjunto VARCHAR(255),
    fecha_envio DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

---

## 📁 Project Structure

```
herreria_web/
├── backend/
│   ├── config.php          # DB configuration (credentials excluded)
│   └── procesar_contacto.php  # Form handler, file upload, DB insert
├── dashboard/
│   ├── index.php           # Login page
│   ├── dashboard.php       # Admin panel - view all messages
│   └── logout.php          # Session destroy
├── uploads/                # Stored client attachments
└── [frontend files]        # Public-facing website
```

---

##  Local Setup

1. Clone the repository
```bash
git clone https://github.com/enuharnunez203-arch/herreria_web.git
```

2. Create a MySQL database and run the schema above

3. Configure your credentials in `backend/config.php`
```php
define('DB_HOST', 'localhost');
define('DB_NOMBRE', 'your_database');
define('DB_USUARIO', 'your_user');
define('DB_CONTRA', 'your_password');
```

4. Deploy on a local Apache server (XAMPP / Laragon) or any PHP hosting

---

##  Key Learnings

- Designed and implemented a relational database schema from scratch
- Applied data security principles across the full stack (SQL, PHP, file handling)
- Built a complete CRUD-based admin interface with session authentication
- Integrated third-party email service via SMTP for real-time notifications

---

## 👤 Author

**Enuhar Gutierrez**  
Computer Systems Engineering Student — Tecnológico Superior de Jalisco  
[LinkedIn](https://www.linkedin.com/in/enuhar-nunez) · [GitHub](https://github.com/enuharnunez203-arch)
