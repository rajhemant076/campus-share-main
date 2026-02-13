# CampusShare - Complete Documentation

## 📚 Table of Contents
1. [Project Overview](#project-overview)
2. [Live Demo](#live-demo)
3. [Repository Structure](#repository-structure)
4. [Frontend Documentation](#frontend-documentation)
5. [Backend Documentation](#backend-documentation)
6. [Installation Guide](#installation-guide)
7. [API Reference](#api-reference)
8. [Environment Variables](#environment-variables)
9. [Deployment Guide](#deployment-guide)
10. [Adding Favicon](#adding-favicon)
11. [Contributing](#contributing)
12. [License](#license)

---

## 🎯 Project Overview

CampusShare is a MERN stack application that enables students to share and discover academic resources. The platform allows users to upload notes, assignments, previous year questions, and lab manuals, with an admin approval system for quality control.

**Tech Stack**
- **Frontend**: React.js, React Router, Context API, Framer Motion
- **Backend**: Node.js, Express.js, MongoDB, Mongoose
- **File Storage**: GridFS
- **Authentication**: JWT, Bcrypt
- **Styling**: CSS with custom variables

---

## 🌐 Live Demo

- **Frontend**: [https://campusshare-frontend.vercel.app](https://campusshare-frontend.vercel.app)
- **Backend API**: [https://campusshare-backend-1.onrender.com](https://campusshare-backend-1.onrender.com)
-

---

## 📁 Repository Structure

This is the main repository that contains links to the frontend and backend repositories.


### GitHub Repositories
- **Frontend Repository**: [https://github.com/rajhemant076/campusshare-frontend](https://github.com/rajhemant076/campusshare-frontend)
- **Backend Repository**: [https://github.com/rajhemant076/campusshare-backend](https://github.com/rajhemant076/campusshare-backend)

---

# 🚀 Frontend Documentation

## 📁 Frontend Structure

campusshare-frontend/
├── public/
│ ├── favicon.ico
│ ├── index.html
│ └── ...
├── src/
│ ├── api/
│ │ └── api.js
│ ├── components/
│ │ ├── Footer.jsx
│ │ ├── Navbar.jsx
│ │ ├── ProtectedRoute.jsx
│ │ └── ResourceCard.jsx
│ ├── context/
│ │ └── AuthContext.jsx
│ ├── pages/
│ │ ├── About.jsx
│ │ ├── Bookmarks.jsx
│ │ ├── Contact.jsx
│ │ ├── Features.jsx
│ │ ├── Home.jsx
│ │ ├── Login.jsx
│ │ ├── Profile.jsx
│ │ ├── Signup.jsx
│ │ └── Upload.jsx
│ ├── App.jsx
│ ├── App.css
│ └── Main.jsx
├── .env
├── .gitignore
├── package.json
├── package-lock.json


## 🎨 Frontend Pages and Features

### Authentication Pages

**Login Page** (`src/pages/Login.jsx`)
- Email/password login functionality
- JWT token storage in localStorage
- Role-based redirection (admin/student)
- Form validation and error handling

**Signup Page** (`src/pages/Signup.jsx`)
- User registration with form fields:
  - Full Name
  - Email Address
  - Password (min 6 characters)
  - Branch (CSE, ECE, EEE, MECH, CIVIL, IT, OTHER)
  - Semester (1-8)
- Automatic login after successful registration

### Main Pages

**Home Page** (`src/pages/Home.jsx`)
- Resource listing with pagination (12 items per page)
- Debounced search functionality (500ms delay)
- Filter system with:
  - Branch filter (CSE, ECE, EEE, MECH, CIVIL, IT, OTHER)
  - Semester filter (1-8)
  - Subject filter (text input)
  - Type filter (Notes, Assignment, PYQ, Lab)
- Responsive grid layout (3 columns on desktop, 2 on tablet, 1 on mobile)
- Load more button for pagination

**Features Page** (`src/pages/Features.jsx`)
- Platform statistics display (total users, resources, downloads)
- Feature cards with icons and descriptions
- Live data fetched from backend API
- Branch-wise resource distribution chart
- How it works timeline with 5 steps
- Call-to-action buttons for signup

**About Page** (`src/pages/About.jsx`)
- Mission statement section
- Real-time statistics cards:
  - Total Active Users
  - Total Resources
  - Total Downloads
  - Approved Uploads
- Journey timeline with milestones
- Core values cards (6 values)
- Tech stack showcase with icons
- Call-to-action section

**Contact Page** (`src/pages/Contact.jsx`)
- Contact information cards (Email, Location, Hours)
- Contact form with validation:
  - Name, Email, Subject, Message
  - Category dropdown
- FAQ section with category filters
- Team contact cards with response times
- Social media links

### User Pages

**Profile Page** (`src/pages/Profile.jsx`)
- User information display with:
  - Basic info (name, email, phone)
  - Academic info (branch, semester, graduation year)
  - Bio/About section
  - Social links (LinkedIn, GitHub, Twitter)
- Edit profile functionality with form
- Upload history table with status badges:
  - Pending (yellow)
  - Approved (green)
  - Rejected (red)
- Profile visibility settings

**Bookmarks Page** (`src/pages/Bookmarks.jsx`)
- List of bookmarked resources
- Bookmark/Unbookmark functionality
- Empty state with illustration
- Resource count display

**Upload Page** (`src/pages/Upload.jsx`)
- Resource upload form:
  - Title (required)
  - Description (required)
  - Branch (dropdown)
  - Semester (dropdown)
  - Subject (required)
  - Type (dropdown: Notes, Assignment, PYQ, Lab)
- File upload with validation:
  - PDF only
  - Max 10MB file size
- Success/error messages
- Auto-redirect to profile after upload

### Components

**Navbar Component** (`src/components/Navbar.jsx`)
- Responsive design with hamburger menu on mobile
- Conditional rendering based on authentication:
  - Public: Home, Features, About, Contact, Login, Signup
  - Student: + Upload, Bookmarks, Profile, Logout
  - Admin: + Admin Panel link
- Active link highlighting
- Smooth animations for mobile menu

**Footer Component** (`src/components/Footer.jsx`)
- Brand section with tagline
- Social media links (GitHub, LinkedIn, Instagram)
- Quick links section
- Support links section
- Contact information
- Copyright and legal links
- Dynamic year in copyright

**ResourceCard Component** (`src/components/ResourceCard.jsx`)
- Resource details display with:
  - Title, description, type badge
  - Branch, semester, subject tags
  - Uploader information
- Interactive features:
  - Like/Unlike with optimistic updates
  - Bookmark/Unbookmark
  - View PDF in new tab
  - Download PDF with progress
- Memoized for performance
- Error handling with alerts

**ProtectedRoute Component** (`src/components/ProtectedRoute.jsx`)
- Route protection based on authentication
- Admin-only route protection
- Loading spinner while checking auth
- Redirect to login for unauthenticated users
- Redirect to home for non-admin users

### Context and State Management

**Auth Context** (`src/context/AuthContext.jsx`)
- Provides authentication state throughout the app
- Manages user data, token, and role
- Handles login, logout, and token persistence
- Auto-login on page refresh
- Admin status detection

**API Configuration** (`src/api/api.js`)
- Axios instance with base URL configuration
- Request interceptor for JWT attachment
- Response interceptor for error handling
- Automatic logout on 401 responses
- Environment-based API URL

### Styling Architecture

**CSS Variables** (`src/App.css`)
- Color palette with primary, secondary, accent colors
- Background colors for different components
- Text colors for light/dark themes
- Border colors and styles
- Shadow presets (sm, md, lg)
- Spacing scale (xs, sm, md, lg, xl)
- Border radius scale
- Transition timings

**Component-Specific Styles**
- Navbar styles (sticky, shadow, hover effects)
- Button styles (primary, secondary, outline, sizes)
- Card styles (hover effects, borders)
- Form styles (inputs, selects, textareas)
- Badge styles (status colors)
- Alert styles (success, error, warning, info)
- Loading spinner animations
- Filter container styles
- Empty state styles
- Footer styles (dark theme, responsive)
- Responsive breakpoints for all components

### Responsive Design Breakpoints

- **Desktop (>1200px)**: Full layout with 3-4 column grids
- **Laptop (1024px - 1200px)**: Reduced padding, 3 column grids
- **Tablet (768px - 1024px)**: 2 column grids, adjusted spacing
- **Mobile (480px - 768px)**: 1 column grids, hamburger menu
- **Small Mobile (<480px)**: Compact spacing, stacked elements

---

# ⚙️ Backend Documentation

## 📁 Backend Folder Structure

campusshare-backend/
├── config/
│ └── db.js
├── controllers/
│ ├── aboutController.js
│ ├── adminController.js
│ ├── authController.js
│ ├── contactController.js
│ ├── featuresController.js
│ ├── fileController.js
│ └── resourceController.js
├── middleware/
│ ├── admin.js
│ ├── auth.js
│ └── gridfsUploadDirect.js
├── models/
│ ├── Contact.js
│ ├── Resource.js
│ └── User.js
├── routes/
│ ├── aboutRoutes.js
│ ├── adminRoutes.js
│ ├── authRoutes.js
│ ├── contactRoutes.js
│ ├── featuresRoutes.js
│ ├── fileRoutes.js
│ └── resourceRoutes.js
├── uploads/
├── .env
├── .gitignore
├── createAdmin.js
├── package-lock.json
├── package.json
├── render.yaml
└── server.js


## 📊 Database Models

### User Model
- **Fields**: name, email, password, role, branch, semester
- **Optional Fields**: phone, enrollmentId, graduationYear, college, bio
- **Social Links**: linkedin, github, twitter (nested object)
- **Relations**: likedResources (array of Resource IDs), bookmarks (array of Resource IDs)
- **Settings**: profileVisibility (public/private/contacts), accountStatus (active/suspended)
- **Timestamps**: createdAt, updatedAt, lastActive
- **Indexes**: email (unique)

### Resource Model
- **Required Fields**: title, description, branch, semester, subject, type
- **File Fields**: fileId (GridFS reference), fileUrl, fileName
- **Metadata**: uploadedBy (User reference), status (pending/approved/rejected), rejectionReason
- **Counters**: likesCount, downloadCount
- **Timestamps**: createdAt, updatedAt
- **Indexes**: branch, semester, subject, type (compound), status, text search on title/description

### Contact Model
- **Fields**: name, email, subject, message
- **Category**: general, support, feedback, report, partnership
- **Status**: unread, read, replied
- **Admin Fields**: repliedAt, repliedBy (User reference)
- **Timestamps**: createdAt, updatedAt

## 🔧 Controllers Overview

### Auth Controller
- User registration with password hashing (bcrypt)
- User login with JWT token generation
- Profile retrieval and update
- Password validation and security

### Resource Controller
- Resource upload with GridFS file handling
- Resource listing with filters and pagination
- Like/unlike functionality
- Bookmark/unbookmark functionality
- User-specific resource queries
- File download and view handling

### Admin Controller
- Dashboard statistics aggregation
- Pending resources management
- Resource approval/rejection
- User management (list, suspend, activate)
- Contact message management

### Features Controller
- Platform-wide statistics
- Branch-wise resource distribution
- Type-wise resource distribution
- Recent and popular resources
- Features list for frontend

### File Controller
- GridFS file streaming
- PDF viewing in browser
- File download with proper headers
- Error handling for missing files

### Contact Controller
- Contact form submission
- Message categorization
- Status tracking
- Admin reply functionality

## 🔐 Middleware

### Auth Middleware
- JWT token verification
- User authentication check
- Request user attachment

### Admin Middleware
- Role-based access control
- Admin-only route protection

### Upload Middleware
- GridFS storage configuration
- File size limiting (10MB)
- File type validation (PDF only)
- Error handling for uploads

---

# 💻 Installation Guide

## Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- Git
- npm or yarn

## Frontend Setup

```bash
# Clone frontend repository
git clone https://github.com/rajhemant076/campusshare-frontend
cd campusshare-frontend

# Install dependencies
npm install

# Create .env file
# Add: REACT_APP_API_URL=https://campusshare-backend-1.onrender.com/api

# Start development server
npm start
```

# Backend setup
```bash

# Clone backend repository
git clone https://github.com/rajhemant076/campusshare-backend
cd campusshare-backend

# Install dependencies
npm install

# Create .env file (see Environment Variables section)

# Create admin user
npm run createAdmin

# Start development server
npm run dev

