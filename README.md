# Andhra Pradesh Citizen Complaint Portal

A fully functional, responsive web application for citizens of Andhra Pradesh to report and track civic issues. Built with HTML, CSS, JavaScript, and Firebase.

## 🚀 Features
- **Public Home Page:** Overview of recent reports and how the system works.
- **Submit Complaint:** Form with dynamic district/mandal selections (All 26 districts & 679 mandals included).
- **Track Complaint:** Real-time tracking using Complaint ID or Email, showing status timeline.
- **Detailed Location:** Support for specific Village, Ward, and Street reporting.
- **Admin Dashboard:** Secure dashboard for officials to manage complaints (Filter, Update Status, Delete).
- **Responsive Design:** Optimized for both Desktop and Mobile users.

## 🛠️ Tech Stack
- **Frontend:** Vanilla HTML5, CSS3 (Modern UI), JavaScript (ES6+ Modules)
- **Backend:** Firebase (Firestore for data, Authentication for admin login)
- **Icons:** FontAwesome 6

## 📁 Project Structure
```text
/
├── index.html           # Home Page
├── submit.html          # Submit Complaint Form
├── track.html           # Track Complaint Status
├── contact.html         # Contact Us Page
├── admin-login.html     # Admin Authentication
├── admin-dashboard.html # Admin Management Portal
├── css/
│   └── style.css        # Main Styling
└── js/
    ├── app.js           # Firebase Init & Global Logic
    ├── auth.js          # Admin Auth Logic
    ├── complaints.js    # Complaint CRUD Logic
    ├── location-data.js # AP Districts/Towns Data
    └── firebase-config.js # Firebase Configuration (Update this!)
```

## ⚙️ Setup Instructions

### 1. Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/).
2. Create a new project: `AP-Citizen-Portal`.
3. Go to **Authentication** -> **Sign-in method** -> Enable **Email/Password**.
4. Go to **Cloud Firestore** -> **Create Database** -> Choose **Start in Test Mode** (or production mode with updated rules).
5. Add a Web App to your project and copy the `firebaseConfig` object.

### 2. Configure the App
Open `js/firebase-config.js` and replace the placeholder values with your project credentials:
```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "...",
    projectId: "...",
    // ... rest
};
```

### 3. Create Admin Account
You can now create an admin account directly through the portal:
- Go to **Admin Login** -> **Register here**.
- Fill in your official email and password to create an account.
- Alternatively, you can add users manually in the **Firebase Console** -> **Authentication**.

### 4. Run Locally
You can run this project using any local web server.
- **VS Code:** Use the "Live Server" extension.
- **Terminal:** `npx serve .`

## 🛡️ Firestore Security Rules (Recommended)
Add these rules in the Firebase Console to protect your data while allowing public submissions:
```text
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /complaints/{complaintId} {
      allow read: if true;
      allow create: if true;
      allow update, delete: if request.auth != null;
    }
    match /messages/{messageId} {
      allow create: if true;
      allow read, update, delete: if request.auth != null;
    }
  }
}
```

## 📜 Acknowledgements
This project is a demonstration of a Citizen Complaint Management System for the State of Andhra Pradesh.
