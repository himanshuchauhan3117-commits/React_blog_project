# DevPulse - Modern React Blog Management System

A complete, modern, and responsive **Blog Management System** engineered purely with **React.js** and **Browser Local Storage**. No Node.js, Express, MongoDB, MySQL, PHP, or any other backend server is used.

---

## 🚀 Quick Start Guide

### 1. Installation
In the project directory, run:
```bash
npm install
```

### 2. Start Development Server
```bash
npm run dev
```

Open your browser at the local URL provided by Vite (typically `http://localhost:5173`).

---

## 🔑 Pre-Configured Test Credentials

For quick evaluation, you can test right away with the pre-seeded author account or register your own new account:

- **Email:** `user@gmail.com`
- **Password:** `password123`
- *(Or click the **"Fill Demo"** button on the Login page for 1-click credential population)*

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **React 19** | Component-driven frontend architecture & modern hooks |
| **React Router DOM 7** | Client-side routing, protected routes & URL navigation |
| **Axios** | Configured HTTP client for external inspirational quotes & APIs |
| **HTML5 & CSS3** | Modern semantic structure & responsive styling |
| **Tailwind CSS v4** | Clean light-mode design system, soft gradients & shadows |
| **Browser Local Storage** | Persistent client-side data store for users, auth, & blogs |
| **Lucide React** | Consistent, modern vector iconography |

---

## 📁 Project Architecture & Local Storage Keys

### Local Storage Keys:
- `registeredUsers`: Array of user accounts with credentials and registration timestamps.
- `currentUser`: The currently authenticated user session object (persists across browser refreshes).
- `blogs`: Array of all published blog posts with ownership identifiers.

```json
{
  "id": 1,
  "title": "Introduction to React: Building Next-Gen Web Interfaces",
  "image": "https://images.unsplash.com/photo-1633356122544-f134324a6cee?q=80&w=1200&auto=format&fit=crop",
  "description": "React is a powerful and flexible JavaScript library...",
  "author": "Himanshu Chauhan",
  "authorEmail": "user@gmail.com",
  "category": "React & Frontend",
  "createdAt": "2026-10-30"
}
```

---

## 📂 Project Structure

```
blog_project/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── Navbar.jsx          # Responsive header with dynamic auth states
│   │   ├── BlogCard.jsx        # Professional article card with ownership badges
│   │   ├── ProtectedRoute.jsx  # Route guard redirecting unauthorized visitors
│   │   ├── ConfirmModal.jsx    # Accessible modal for blog deletion confirmations
│   │   └── Footer.jsx          # Professional SaaS footer
│   ├── pages/
│   │   ├── Home.jsx            # Hero banner, features, live Axios quote, trending blogs
│   │   ├── Login.jsx           # Credential verification & demo autofill
│   │   ├── Register.jsx        # Full name, email, password confirmation validation
│   │   ├── Blogs.jsx           # All blogs with live search, category filters & sort
│   │   ├── BlogDetails.jsx     # Full blog view, reading time, share link & actions
│   │   ├── CreateBlog.jsx      # Title, cover URL/upload, presets & content form
│   │   ├── EditBlog.jsx        # Ownership-protected update form
│   │   └── Dashboard.jsx       # Stats (Total blogs, My blogs), table & management
│   ├── services/
│   │   ├── storageService.js   # Complete Local Storage CRUD engine
│   │   └── apiService.js       # Axios HTTP client instance & external API calls
│   ├── context/
│   │   ├── AuthContext.jsx     # Authentication state & login/register/logout hooks
│   │   └── ToastContext.jsx    # Floating animated toast notifications system
│   ├── styles/
│   │   └── index.css           # Tailwind CSS imports & animations
│   ├── App.jsx                 # Route definitions & scroll-to-top handler
│   └── main.jsx                # Application root mount
├── index.html
├── package.json
└── vite.config.js
```

---

## ✨ Features Implemented

1. **Authentication & Session Persistence:**
   - Registration with duplicate email checking, required field checks, and password matching.
   - Login with credential verification against stored users.
   - Session hydration from `localStorage.getItem('currentUser')` on page refresh.
   - Secure Logout clearing session state.
   - Protected routes guarding `/create-blog`, `/edit-blog/:id`, and `/dashboard`.

2. **Complete Blog CRUD Operations:**
   - **Create:** Validated form supporting image URLs, stock cover presets, or local image file uploads (converted to base64 data URLs).
   - **Read:** Modern cards on Home and All Blogs pages, live search, categories, and dedicated details page with reading time estimator.
   - **Update:** Pre-filled edit form with ownership verification.
   - **Delete:** Interactive confirmation modal dialog preventing accidental loss.

3. **Ownership Protection:**
   - Anyone can view published blogs.
   - Only the original author (`blog.authorEmail === currentUser.email`) can edit or delete their own blogs.

4. **Axios HTTP Client:**
   - Configured Axios instance with interceptors in `src/services/apiService.js`.
   - Real Axios HTTP call to fetch daily inspirational quotes on the Home page.
   - Blog and Auth CRUD strictly use `storageService.js` and Local Storage directly as required.
