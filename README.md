# 🚀 Arewa-Digital-Hub-

**Northern Nigeria's Premier Tech Community Platform**

Arewa Digital Hub is a comprehensive web-based platform designed to empower tech professionals, students, entrepreneurs, and enthusiasts across Northern Nigeria. Built with pure HTML, CSS, and JavaScript, it features a modern dark-themed UI, localStorage-based authentication, and is ready for Firebase integration.

---

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Pages Overview](#pages-overview)
- [Getting Started](#getting-started)
- [Authentication System](#authentication-system)
- [Firebase Integration Guide](#firebase-integration-guide)
- [Customization](#customization)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features

### 🎓 Learning & Courses
- **200+ Courses** across Web Development, Mobile Development, Data Science, AI/ML, Cybersecurity, and UI/UX Design
- Progress tracking with visual progress bars
- Course enrollment and filtering by category
- Mobile-optimized learning experience

### 👥 Networking
- Member directory with search and filter capabilities
- Connect with tech professionals across Northern Nigeria
- Location-based filtering (Kano, Kaduna, Sokoto, Abuja, etc.)
- Role-based filtering (Developer, Designer, Data Scientist, Mentor)
- Mentor identification system

### 📅 Events & Meetups
- Upcoming events listing with virtual and in-person tags
- Event registration system
- Date-based event cards
- Location and time metadata

### 👤 User Profiles
- Editable personal information (name, phone, location, bio)
- Password change functionality
- Account deletion capability
- Profile badges (Account Type, Experience Level, Active Member)

### ⚙️ Settings & Preferences
- Notification toggles (Email, Push, Weekly Digest, Connection Alerts)
- Language selection (English, Hausa, Arabic)
- Dark mode toggle
- Privacy settings (Public Profile, Activity Status)
- Data management (Download data, Clear cache, Reset settings)

### 🔐 Authentication
- Multi-step registration (4 steps: Personal Info → Account Details → Interests → Confirmation)
- Login with email/username and password
- Password strength indicator
- "Show Password" toggle
- Demo account support (`demo@arewa.com` / `demo123`)
- Password recovery flow
- Social login placeholders (Google, GitHub)

### 📱 Responsive Design
- Mobile-first responsive layout
- Collapsible sidebar for dashboard pages
- Touch-friendly navigation
- Optimized for all screen sizes

---

## 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **HTML5** | Page structure and semantic markup |
| **CSS3** | Styling with CSS variables, Grid, Flexbox, and animations |
| **JavaScript (ES6+)** | Interactivity, DOM manipulation, and data handling |
| **localStorage** | Client-side data persistence (users, sessions, settings) |
| **Firebase** (Ready) | Backend integration for auth, database, and storage |

---

## 📁 Project Structure

```
arewa-digital-hub/
│
├── index.html              # Landing page / Public homepage
├── login.html              # User login page
├── register.html           # Multi-step registration page
├── forgot-password.html    # Password recovery page
├── dashboard.html          # User dashboard (main app entry)
├── courses.html            # Course catalog and enrolled courses
├── network.html            # Member networking page
├── events.html             # Events and meetups listing
├── profile.html            # User profile management
├── settings.html           # User preferences and settings
├── help.html               # Help center with FAQ and contact form
│
├── css/                    # (Optional) External stylesheets
├── js/                     # (Optional) External JavaScript files
├── images/                 # Images and assets
├── firebase/               # Firebase configuration
│   └── config.js           # Firebase SDK initialization
│
└── README.md               # This file
```

---

## 📄 Pages Overview

### Public Pages (No Authentication Required)

| Page | Description | File |
|------|-------------|------|
| **Homepage** | Landing page with hero section, features, courses preview, events, testimonials, and CTA | `index.html` |
| **Login** | User authentication with email/username and password | `login.html` |
| **Register** | 4-step registration wizard with validation | `register.html` |
| **Forgot Password** | Password recovery with email verification simulation | `forgot-password.html` |
| **Help Center** | FAQ accordion, search, and contact form | `help.html` |

### Protected Pages (Authentication Required)

| Page | Description | File |
|------|-------------|------|
| **Dashboard** | Main application dashboard with sidebar navigation | `dashboard.html` |
| **Courses** | Course catalog with enrollment and progress tracking | `courses.html` |
| **Network** | Member directory with connect functionality | `network.html` |
| **Events** | Events listing with registration | `events.html` |
| **Profile** | Personal information and security settings | `profile.html` |
| **Settings** | Preferences, notifications, and data management | `settings.html` |

---

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- A code editor (VS Code, Sublime Text, etc.)
- Basic knowledge of HTML, CSS, and JavaScript
- (Optional) Firebase account for backend features

### Installation

1. **Clone or download the project**
   ```bash
   git clone https://github.com/umarmuazuabdullahi/arewa-digital-hub.git
   cd arewa-digital-hub
   ```


2. **Open the project**
   - Simply open `index.html` in your browser to view the public site
   - Or use a local server:
     ```bash
     # Using Python
     python -m http.server 8000
     
     # Using Node.js (live-server)
     npx live-server
     ```

3. **Navigate to the app**
   - Visit `http://localhost:8000` or the address your server provides

---

## 🔐 Authentication System

### How It Works
The platform uses **localStorage** for client-side authentication during development:

1. **Registration** (`register.html`)
   - User fills 4-step form
   - Data is validated and stored in `localStorage` as `arewa_users`
   - Each user gets a unique ID based on timestamp

2. **Login** (`login.html`)
   - User enters email/username and password
   - System checks against `arewa_users` in localStorage
   - On success, stores session in `arewa_current_user`
   - Redirects to `dashboard.html`

3. **Session Management**
   - `arewa_current_user` stores the active session
   - All protected pages check for this key; if missing, redirect to login
   - Logout clears the session key

4. **Demo Account**
   - Email: `demo@arewa.com`
   - Password: `demo123`
   - Useful for testing without registration

### localStorage Keys

| Key | Purpose |
|-----|---------|
| `arewa_users` | Array of registered user objects |
| `arewa_current_user` | Currently logged-in user session |
| `arewa_settings` | User preferences and toggles |

---

## 🔥 Firebase Integration Guide

To replace localStorage with Firebase, follow these steps:

### Step 1: Create a Firebase Project
1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add Project" and name it "arewa-digital-hub"
3. Enable **Authentication**, **Firestore Database**, and **Storage**

### Step 2: Add Firebase Config
Create `firebase/config.js`:

```javascript
// firebase/config.js
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-app.js";
import { getAuth } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-auth.js";
import { getFirestore } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-firestore.js";
import { getStorage } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-storage.js";

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef123456"
};

const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
export const db = getFirestore(app);
export const storage = getStorage(app);
```

### Step 3: Update Authentication
Replace localStorage auth with Firebase Auth in:
- `login.html` → Use `signInWithEmailAndPassword()`
- `register.html` → Use `createUserWithEmailAndPassword()`
- `forgot-password.html` → Use `sendPasswordResetEmail()`

### Step 4: Update Data Storage
Replace localStorage with Firestore:
- User profiles → Firestore `users` collection
- Courses → Firestore `courses` collection
- Events → Firestore `events` collection
- Settings → Firestore `settings` document

### Step 5: Contact Form & Newsletter
Connect `help.html` contact form to Firestore:
```javascript
import { collection, addDoc } from "firebase/firestore";
import { db } from "./firebase/config.js";

// Submit contact form
async function submitContactForm(data) {
  await addDoc(collection(db, "contacts"), {
    ...data,
    timestamp: new Date()
  });
}
```

---

## 🎨 Customization

### Colors & Theme
The platform uses CSS variables defined in `:root`. Edit these to change the color scheme:

```css
:root {
  --primary-green: #4CAF50;
  --primary-blue: #2196F3;
  --accent-orange: #FF9800;
  --accent-gold: #FFD700;
  --dark-bg: #0f172a;
  --sidebar-bg: #1e293b;
  --card-bg: #1e293b;
  --text-primary: #f8fafc;
  --text-secondary: #94a3b8;
  --border-color: #334155;
}
```

### Adding New Courses
Edit the `courses` array in `courses.html`:

```javascript
const courses = [
  { 
    id: 9, 
    title: 'Your New Course', 
    desc: 'Description here...', 
    icon: '🎯', 
    tag: 'Category', 
    duration: '10 Weeks', 
    lessons: 30, 
    enrolled: false, 
    progress: 0, 
    category: 'web' 
  }
];
```

### Adding New Events
Edit the `events` array in `events.html`:

```javascript
const events = [
  { 
    id: 7, 
    title: 'New Event', 
    desc: 'Description...', 
    day: '01', 
    month: 'Jan', 
    time: '10:00 AM', 
    location: 'Kano', 
    type: 'in-person', 
    registered: false 
  }
];
```

### Adding New Members
Edit the `members` array in `network.html`:

```javascript
const members = [
  { 
    id: 9, 
    name: 'New Member', 
    role: 'Developer', 
    location: 'Kano', 
    skills: ['React', 'Node.js'], 
    connected: false, 
    isMentor: false 
  }
];
```

---

## 🌐 Deployment

### GitHub Pages
1. Push your code to a GitHub repository
2. Go to **Settings > Pages**
3. Select source as "Deploy from a branch"
4. Choose `main` branch and `/ (root)` folder
5. Your site will be live at `https://yourusername.github.io/arewa-digital-hub/`

### Netlify
1. Drag and drop your project folder to [Netlify Drop](https://app.netlify.com/drop)
2. Or connect your GitHub repository for continuous deployment

### Firebase Hosting
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

### Vercel
```bash
npm install -g vercel
vercel
```

---

## 🤝 Contributing

We welcome contributions from the Northern Nigeria tech community!

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines
- Follow the existing code style and structure
- Ensure all pages are responsive
- Test on multiple browsers and devices
- Update this README with any new features
- Write clear, descriptive commit messages

---

## 📞 Support

If you encounter any issues or have questions:

- 📧 Email: support@arewadigitalhub.com
- 📱 Phone: +234 800 123 4567
- 💬 WhatsApp: +234 800 123 4567
- 📍 Office: Kano State, Nigeria

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 🙏 Acknowledgments

- Built for the Northern Nigeria tech community
- Inspired by the need for localized tech education
- Special thanks to all contributors and community members

---

**Made with ❤️ in Northern Nigeria 🇳🇬**

**© 2026 Arewa Digital Hub. All rights reserved.**
