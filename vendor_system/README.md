# Arua City Street Vendor Management System (v2.0)

A modern, secure, and robust web application for the **Arua City Council** to manage street vendor registrations, revenue collection, violations, and financial oversight.

---

## 🚀 Key Features

- **Multi-Role Access Control (RBAC)**: Secure access for Admin, Finance Officers, Field Officers, and Vendors.
- **Automated Revenue Tracking**: Manage pitch fees, monthly permits, and daily collections.
- **Violations & Fines Registry**: Issue and track penalties for street-level violations.
- **Financial Oversight**: Verification system for Finance Officers to audit cash collections.
- **Printable IDs & Receipts**: Automated PDF generation for Vendor Permits and Payment Receipts.
- **QR Code Verification**: Secure, scannable QR codes on all documents for instant authenticity checks.
- **Progressive Web App (PWA)**: Install the system on any smartphone as a native-like app with a dedicated home screen icon.
- **Mobile-Responsive UI**: Fully optimized interface for field officers using mobile devices.

---

## 👥 System Roles & Permissions

| Role | Permissions |
| :--- | :--- |
| **Admin** | Full system control, User Management, Database resets, and all reporting. |
| **Field Officer** | Register vendors, issue receipts, and assign penalty fines in the field. |
| **Finance Officer** | View revenue reports, verify transactions, and monitor financial health. |
| **Vendor** | View personal payment history, check permit status, and pay outstanding fines. |

---

## 🔑 Test Credentials

| Username | Password | Default Role |
| :--- | :--- | :--- |
| `admin` | `admin123` | Administrator |
| `field` | `field123` | Field Officer |
| `finance` | `finance123` | Finance Officer |
| `grace` | `vendor123` | Vendor (VND-005) |

---

## 🛠️ Tech Stack

- **Backend**: Python 3.13 + Flask
- **Database**: SQLite (SQLAlchemy ORM)
- **Frontend**: HTML5, Vanilla CSS, JavaScript (Chart.js for analytics)
- **PDFs**: ReportLab / FPDF
- **Security**: Werkzeug (Password Hashing), Flask-Login (Session Management)

---

## 📂 Project Structure

```text
vendor_system/
├── app.py              # Main Application & Business Logic
├── models.py           # Database Schema & Relationships
├── static/             # CSS, JS, and Branding Images
├── templates/          # HTML Layouts & Components
├── instance/           # SQLite Database Files
└── requirements.txt    # Python Dependencies
```

---

## ⚙️ Local Setup

1. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Run the Server**:
   ```bash
   python app.py
   ```

3. **Access the App**:
   Open `http://127.0.0.1:5000` in your browser.

---

## 🗄️ Database Access

### 1. Local Database (SQLite)
Your local data is stored in the `instance/vendors_v2.db` file.
- **Graphical Tool**: Download [DB Browser for SQLite](https://sqlitebrowser.org/) to open and view your tables.
- **Python Shell**: Run `python` in your terminal and use SQLAlchemy to query data directly from the models.

### 2. Production Database (Supabase)
- **Dashboard**: Visit your [Supabase Project](https://supabase.com/dashboard) to use the Table Editor.
- **Data Export**: Use the "Export to CSV" feature in Supabase to get data for your report.

---

## 🚀 Deployment (Vercel)

The system is pre-configured for deployment on **Vercel**. 

### 1. Database Requirement
Vercel is serverless and its filesystem is read-only. **SQLite will not work** for persistence. You must use a cloud PostgreSQL database (e.g., **Vercel Postgres**, **Neon**, or **Supabase**).

### 2. Environment Variables
Set the following variables in your Vercel Project Settings:
- `DATABASE_URL`: Your cloud PostgreSQL connection string.
- `SECRET_KEY`: A long, random string for session security.

---

## 🐍 Deployment (PythonAnywhere)

PythonAnywhere provides a persistent filesystem. You can use either SQLite or Supabase.

### 1. Upload & Install
- Upload your code to a folder (e.g., `/home/username/vendor_system`).
- Open a Bash Console and run:
  ```bash
  mkvirtualenv --python=/usr/bin/python3.10 myenv
  pip install -r requirements.txt
  ```

### 2. WSGI Configuration
In the **Web** tab of PythonAnywhere, edit your WSGI file and use this configuration:
```python
import sys
import os

path = '/home/yourusername/vendor_system'
if path not in sys.path:
    sys.path.append(path)

from app import app as application
```

### 3. Environment Variables
Since PythonAnywhere doesn't use `.env` by default, ensure you add this to the top of your `app.py` (which I have already included):
`from dotenv import load_dotenv; load_dotenv()`

---

## 📱 Mobile Installation (PWA)
The system is built as a **Progressive Web App**. To install it on your smartphone:
1. Open the system URL in **Chrome** (Android) or **Safari** (iOS).
2. Tap the **Menu/Share** button.
3. Select **"Add to Home Screen"** or **"Install App"**.
4. A dedicated **Arua VendorMS** icon will appear on your home screen for instant access.

---

## 📝 Developer Note
This system was localized for **Arua City Council** to support digital transformation in municipal revenue management. Every line of code is commented for transparency and academic review.

*Built for Arua Street Vendor Authority — 2026*
