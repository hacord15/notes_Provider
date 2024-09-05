# Secure File Sharing Web Application

This project is a React-based web application that allows parents to securely upload files (PDFs, videos, images) and share them with their children using a unique OTP or code. Each parent has their own protected directory, and children can access shared files by entering the provided OTP.

## Features

- **Secure Parent Login:** Parents have individual accounts and secure access to their own file directories.
- **File Upload:** Parents can upload PDFs, videos, and images to their personal directory.
- **OTP/Code-based Sharing:** Parents generate a unique OTP or code for each file, which the child can use to access the file.
- **Directory Structure:** Each parent has their own directory, isolated from others.
- **Responsive UI:** Mobile-friendly design for easy access by parents and children.

## Tech Stack

### Frontend

- **React.js:** The application is built using React for dynamic user interfaces.
- **TailwindCSS / Bootstrap:** For UI styling and responsive design.
- **Axios/Fetch:** For API communication between frontend and backend.
- **Redux/Context API:** To manage global state.

### Backend

- **Node.js / Express.js:** The backend API handles authentication, file uploads, and OTP/code generation.
- **Database:** MongoDB/PostgreSQL/MySQL for storing user data, file metadata, and OTPs.
- **Amazon S3/Google Cloud Storage:** For storing uploaded files securely.
- **JWT (JSON Web Tokens):** For secure authentication and session management.

### Security

- **Encryption:** Passwords are encrypted using bcrypt, and sensitive data such as file URLs are protected.
- **Role-based Access:** Differentiated access control for parents and children.
- **OTP Verification:** Files are only accessible with a valid OTP or specific code provided by the parent.

## System Design Overview

### 1. Frontend: React Application
- **User Roles:**
  - Parents: Can upload files and generate OTPs for sharing.
  - Children: Can access shared files via OTP or code.
- **Components:**
  - Authentication (Login/Register)
  - File Upload Interface
  - OTP/Code Generation
  - File Access Interface for Children

### 2. Backend: REST API/GraphQL
- **Endpoints:**
  - `POST /register`: Register a new parent.
  - `POST /login`: Authenticate parent with JWT.
  - `POST /upload`: Upload file to the parent’s directory.
  - `POST /generate-otp`: Generate an OTP or specific code for a file.
  - `POST /verify-otp`: Verify OTP and grant access to the child.

### 3. Database Design
- **User Schema:**
  - UserID, username, email, password, directoryPath
- **File Metadata Schema:**
  - FileID, filePath, fileType, associatedParent
- **OTP Schema:**
  - OTP, associatedFile, expirationTime

### 4. Storage System
- **File Storage:** Files are stored securely in cloud storage services like Amazon S3.
- **Parent Directories:** Each parent has their own isolated directory for storing files.

## Flow Diagram

+--------------------+ +---------------------------+ | React App |<------>| Backend API (Node.js) | +--------------------+ +---------------------------+ | | | | v v +--------------------+ +---------------------------+ | Authentication |<----->| OTP/Code Logic | +--------------------+ +---------------------------+ | | v v +--------------------+ +---------------------------+ | File Management |<------>| Storage (AWS S3, etc.) | +--------------------+ +---------------------------+ | | v v +--------------------+ +---------------------------+ | Database | | Parent Directories | +--------------------+ +---------------------------+
