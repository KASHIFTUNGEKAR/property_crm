# 🏠 Smart Property Portal

A full-featured **Property CRM & Ad Campaign Management System** built with pure PHP following the MVC architecture pattern. This platform enables property listing, admin moderation, and a built-in advertising engine with CPC/CPM campaign support.

---

## ✨ Features

### 🔐 Authentication & Authorization
- User registration with role-based access (User / Admin)
- Secure login with **bcrypt** password hashing
- Session-based authentication
- Role-based route protection

### 🏡 Property Management
- **Create** property listings with detailed info (title, description, price, city, type, bedrooms, bathrooms, sqft, amenities, etc.)
- **Multi-image upload** with gallery support
- **Edit & Update** existing listings
- **Admin approval workflow** — properties start as `pending` and require admin approval before going live
- **Featured & Sponsored** property highlighting
- Video URL & Virtual Tour links

### 📊 User Dashboard
- View approved & pending property listings
- Campaign performance stats (impressions, clicks, spend)
- Quick actions for managing listings and campaigns

### 📢 Ad Campaign System
- **CPC (Cost Per Click)** campaigns — charged per click
- **CPM (Cost Per Impression)** campaigns — charged per 1,000 impressions
- Budget management with **automatic pause** when budget is exhausted
- Click & impression tracking with database logging
- Campaign performance dashboard with real-time stats

### 🎨 Ad Creative Management
- Upload ad creatives (image, title, description, redirect URL)
- Link creatives to campaigns
- **Admin approval/rejection** workflow for ad creatives
- Click tracking on ad creatives

### 🛡️ Admin Panel
- **Property Moderation** — review and approve pending property listings
- **Ad Creative Moderation** — approve or reject submitted ad creatives
- **Revenue Dashboard** — view total revenue, active/paused campaigns, total clicks & impressions

---

## 🏗️ Tech Stack

| Layer        | Technology              |
|-------------|------------------------|
| Language     | PHP 7+                 |
| Architecture | Custom MVC Framework   |
| Database     | MySQL (via PDO)        |
| Auth         | bcrypt + PHP Sessions  |
| Server       | Apache (XAMPP/WAMP)    |
| Frontend     | HTML, CSS, JavaScript  |

---

## 📁 Project Structure

```
smart_property_portal/
├── config/
│   └── Database.php          # PDO database connection
├── controllers/
│   ├── AdminController.php   # Admin panel (properties, ads, revenue)
│   ├── AuthController.php    # Login, Register, Logout
│   ├── CampaignController.php # Campaign CRUD & click tracking
│   ├── DashboardController.php # User dashboard
│   ├── HomeController.php    # Landing page
│   ├── PropertyController.php # Property CRUD & image uploads
│   ├── AdController.php      # Ad click handler
│   └── WalletController.php  # Wallet management
├── core/
│   ├── Controller.php        # Base controller class
│   ├── Model.php             # Base model class
│   └── Router.php            # URL routing engine
├── models/
│   ├── AdCreative.php        # Ad creative model
│   ├── Campaign.php          # Campaign model (CPC/CPM logic)
│   ├── Property.php          # Property model (CRUD, approval)
│   ├── User.php              # User model (auth)
│   └── Wallet.php            # Wallet model
├── public/
│   ├── assets/               # CSS, JS, images
│   └── uploads/              # User-uploaded files
├── storage/                  # Application storage
├── views/
│   ├── admin/                # Admin panel views
│   ├── auth/                 # Login & register forms
│   ├── campaign/             # Campaign management views
│   ├── dashboard/            # User dashboard views
│   ├── layouts/              # Layout templates
│   ├── property/             # Property detail & forms
│   └── home.php              # Landing page
└── index.php                 # Application entry point
```

---

## ⚙️ Installation & Setup

### Prerequisites
- **PHP 7.0+**
- **MySQL 5.7+**
- **Apache** with `mod_rewrite` enabled (XAMPP / WAMP / MAMP recommended)

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/03musab/property_crm.git
   cd property_crm
   ```

2. **Import the database**
   ```bash
   mysql -u root -p < smart_property_portal.sql
   ```
   Or import `smart_property_portal.sql` via **phpMyAdmin**.

3. **Configure the database connection**

   Edit `config/Database.php`:
   ```php
   private $host = "localhost";
   private $db_name = "smart_property_portal";
   private $username = "root";
   private $password = "";
   ```

4. **Place the project in your web server's root**
   - **XAMPP**: `C:\xampp\htdocs\smart_property_portal\`
   - **WAMP**: `C:\wamp64\www\smart_property_portal\`

5. **Start Apache & MySQL**, then open:
   ```
   http://localhost/smart_property_portal/
   ```

---

## 🗄️ Database Schema

The application uses the following tables:

| Table              | Description                          |
|-------------------|--------------------------------------|
| `users`           | User accounts with roles             |
| `properties`      | Property listings with status        |
| `property_images` | Gallery images for properties        |
| `campaigns`       | Ad campaigns (CPC/CPM)              |
| `ad_clicks`       | Click event tracking                 |
| `ad_impressions`  | Impression event tracking            |
| `ad_creatives`    | Ad creatives with approval status    |

---

## 🔄 Application Routes

| Route                | Method | Description                    |
|---------------------|--------|--------------------------------|
| `/`                 | GET    | Home / Landing page            |
| `/register`         | GET/POST | User registration            |
| `/login`            | GET/POST | User login                   |
| `/logout`           | GET    | Logout & destroy session       |
| `/dashboard`        | GET    | User dashboard                 |
| `/property`         | GET    | View property details          |
| `/add-property`     | GET    | Add property form              |
| `/edit-property`    | GET    | Edit property form             |
| `/update-property`  | POST   | Update property                |
| `/create-campaign`  | GET    | Campaign creation form         |
| `/save-campaign`    | POST   | Store new campaign             |
| `/campaign-dashboard` | GET  | Campaign stats                 |
| `/upload-creative`  | GET    | Upload ad creative form        |
| `/save-creative`    | POST   | Store ad creative              |
| `/admin-dashboard`  | GET    | Admin overview                 |
| `/admin-properties` | GET    | Admin — pending properties     |
| `/approve-property` | GET    | Admin — approve a property     |
| `/admin-ad-creatives` | GET  | Admin — pending ad creatives   |
| `/approve-ad`       | GET    | Admin — approve an ad          |
| `/reject-ad`        | GET    | Admin — reject an ad           |
| `/admin-revenue`    | GET    | Admin — revenue dashboard      |

---

## 👤 User Roles

| Role    | Capabilities                                                  |
|---------|---------------------------------------------------------------|
| **User**  | Register, login, list properties, manage campaigns & ads    |
| **Admin** | Approve/reject properties & ads, view revenue & platform stats |

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👨‍💻 Author

**Musab** — [@03musab](https://github.com/03musab)
