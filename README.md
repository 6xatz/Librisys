# Librisys 📚

**Librisys** is a simple **ASP.NET Web Forms (ASPX)** application with a minimal dark theme. It manages **Books** and **Members** with full CRUD operations, includes a login screen, and a dashboard summary.

## Features

* **Login page** (Users table)
* **Dashboard summary**: Total Members, Total Books
* **Books CRUD**

  * List with async delete (no full page reload)
  * Add/Edit in-place (async) with status messages
* **Members CRUD**

  * List with async delete
  * Add/Edit in-place (async)
* **Master layout** with sidebar navigation
* **Minimal dark theme** (CSS embedded in `Site.master`)

## Tech Stack

* **ASP.NET Web Forms (C#)**, .NET Framework 4.x
* **SQL Server** (Local/Express)
* **ADO.NET** (`System.Data.SqlClient`)
* **ASP.NET UpdatePanel / ScriptManager** for partial postbacks (AJAX)

## Getting Started

### 1. Install & Enable IIS Features

Ensure the following features are installed on Windows:

```text
Internet Information Services
+- Web Management Tools
+- World Wide Web Services
   +- Application Development Features
      ¦ +- .NET Extensibility 4.8
      ¦ +- ASP
      ¦ +- ASP.NET 4.8
      ¦ +- ISAPI Extensions
      ¦ +- ISAPI Filters
   +- Common HTTP Features
      ¦ +- Static Content
```

### 2. Setup IIS Site

1. Open **IIS Manager**
2. Add a **New Site**

   * Physical path: `C:\inetpub\wwwroot\Librisys`
   * Port: `8080` (any available port)

### 3. Configure SQL Server

1. Enable TCP/IP:

   * Open **SQL Server Configuration Manager** → SQL Server Network Configuration → Protocols for SQLEXPRESS → **TCP/IP: Enabled**
   * Properties → IP Addresses tab → scroll to **IPAll** → set **TCP Port = 1433**
   * Restart SQL Server Service

2. Create a connection in **Navicat** (or other DB tool):

   * Connection Name: `LocalSQL` (any name)
   * Host/IP: `PC-XXXX`
   * Port: `1433`
   * Authentication: SQL Server Authentication
   * Restore database: `Librisys.sql`

### 4. Database Setup

* Execute `Librisys.sql` to create tables: `Users`, `Products` (legacy), `Books`, `Members`
* Default login in `Users`: Username `Librisys`, Password `0000` (change in DB)

### 5. Set Permissions & Restart IIS

```cmd
icacls "C:\inetpub\wwwroot\Librisys\books" /grant Everyone:(OI)(CI)F /T
iisreset
```

### 6. Run the Application

* Open browser → `http://localhost:8080/login.aspx`
* Login → redirected to `dashboard.aspx`

## Security & TODOs

* Passwords are stored in plain text for demo purposes. Use **hashed passwords** in production.
* Add **server-side authentication checks** per page if needed.
* Consider migrating to **MVC/Razor** or a **PHP stack** for future scalability.

## Documentation

All associated resources are licensed under the [Read-Only Source License](./LICENSE.md).
