# Learning Platform

![License](https://img.shields.io/badge/license-ISC-blue.svg)
![Node](https://img.shields.io/badge/node-%3E%3D14.0.0-brightgreen.svg)
![MongoDB](https://img.shields.io/badge/database-MongoDB-green.svg)
![AngularJS](https://img.shields.io/badge/framework-AngularJS-red.svg)

A full-stack web application that provides an online learning platform where users can browse, search, and enroll in various courses.

## � Table of Contents

- [Project Overview](#-project-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Screenshots](#-screenshots)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Application](#running-the-application)
- [API Endpoints](#-api-endpoints)
- [Usage](#-usage)
- [Security Features](#-security-features)
- [Troubleshooting](#-troubleshooting)
- [Development](#-development)
- [Contributing](#-contributing)
- [License](#-license)

## 📋 Project Overview

This Learning Platform is a modern web application built with a full-stack approach featuring:
- **Frontend**: AngularJS with vanilla CSS for a responsive UI
- **Backend**: Node.js with Express.js for robust API handling
- **Database**: MongoDB with Mongoose ODM for flexible data management
- **Authentication**: Secure user signup/login with bcrypt password hashing

## ✨ Features

### User Authentication
- ✅ User registration with secure password hashing
- ✅ Login/logout functionality
- ✅ Session management with localStorage
- ✅ Protected routes requiring authentication

### Course Management
- ✅ Browse featured courses (Web Development, Data Science, Machine Learning, Graphic Design)
- ✅ Real-time search functionality to find courses
- ✅ Course enrollment system with confirmation modals
- ✅ View enrolled courses in user profile
- ✅ Personalized course recommendations

### User Interface
- ✅ Responsive design optimized for all devices
- ✅ Dynamic navbar with profile toggle
- ✅ Sidebar navigation for easy access
- ✅ Modal dialogs for enrollment confirmation
- ✅ Toast notifications for user feedback
- ✅ Modern CSS animations and transitions

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| **AngularJS** | JavaScript framework for dynamic UI |
| **HTML5/CSS3** | Structure and styling |
| **Font Awesome** | Icon library |
| **Vanilla JavaScript** | Additional functionality and DOM manipulation |

### Backend
| Technology | Purpose |
|------------|---------|
| **Node.js** | JavaScript runtime environment |
| **Express.js** | Web application framework |
| **MongoDB** | NoSQL database |
| **Mongoose** | MongoDB object modeling |
| **bcryptjs** | Password hashing and security |
| **dotenv** | Environment variable management |
| **cors** | Cross-origin resource sharing |
| **body-parser** | Request body parsing middleware |
| **express-session** | Session management |

## � Screenshots

> **Note**: Add screenshots of your application here to showcase the UI

### Homepage
<!-- ![Homepage](screenshots/homepage.png) -->
*Browse and search through available courses*

### User Profile
<!-- ![User Profile](screenshots/profile.png) -->
*View enrolled courses and manage your account*

### Course Enrollment
<!-- ![Enrollment Modal](screenshots/enrollment.png) -->
*Easy one-click enrollment process*

## �📁 Project Structure

```
learning_platform-main/
├── frontend/                # Frontend application
│   ├── index.html          # Main landing page with course grid
│   ├── login.html          # User login page
│   ├── signup.html         # User registration page
│   ├── profile.html        # User profile and enrolled courses
│   ├── navbar.html         # Navigation bar component
│   ├── sidebar.html        # Sidebar component
│   ├── style.css           # Main stylesheet
│   ├── profile.css         # Profile page specific styles
│   ├── app.js              # AngularJS application logic
│   ├── filter.js           # Search and filter functionality
│   ├── slidebar.js         # Sidebar toggle functionality
│   ├── Angular.js          # AngularJS library
│   └── images/             # Image assets and icons
│
├── backend/                # Backend application
│   ├── server.js           # Express server configuration
│   ├── models/             # Mongoose data models
│   │   └── User.js         # User model schema
│   ├── routes/             # API route handlers
│   │   ├── auth.js         # Authentication endpoints
│   │   └── enrollment.js   # Course enrollment endpoints
│   ├── controllers/        # Business logic controllers
│   ├── .env                # Environment variables (not in git)
│   └── package.json        # Backend dependencies
│
├── node_modules/           # Root dependencies
├── package.json            # Root package configuration
├── package-lock.json       # Dependency lock file
└── README.md               # Project documentation
```

## 🚀 Getting Started

### Prerequisites

Before running this application, make sure you have:

- **Node.js** (v14 or higher) - [Download here](https://nodejs.org/)
- **MongoDB** (running locally or MongoDB Atlas account) - [Download here](https://www.mongodb.com/try/download/community)
- **npm** or **yarn** package manager (comes with Node.js)
- A modern web browser (Chrome, Firefox, Edge, or Safari)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/0SAKESH0/Learning-Platform.git
   cd Learning-Platform
   ```

2. **Install root dependencies**
   ```bash
   npm install
   ```

3. **Install backend dependencies**
   ```bash
   cd backend
   npm install
   cd ..
   ```

4. **Configure environment variables**
   
   Create a `.env` file in the `backend` directory with the following content:
   ```env
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/learning-platform
   ```
   
   For MongoDB Atlas (cloud database):
   ```env
   PORT=5000
   MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/learning-platform?retryWrites=true&w=majority
   ```

5. **Start MongoDB** (if running locally)
   ```bash
   # Windows
   mongod
   
   # macOS/Linux
   sudo systemctl start mongod
   ```

### Running the Application

1. **Start the backend server**
   ```bash
   cd backend
   npm start
   ```
   
   You should see:
   ```
   Server is running on port 5000
   MongoDB connected successfully!
   ```

2. **Start the frontend**
   
   Option A: Using Live Server (VS Code extension)
   - Install the Live Server extension in VS Code
   - Right-click on `frontend/index.html`
   - Select "Open with Live Server"
   - It will open at `http://127.0.0.1:5500`

   Option B: Using Python's HTTP server
   ```bash
   cd frontend
   python -m http.server 5500
   ```

3. **Access the application**
   
   Open your browser and navigate to:
   - Frontend: `http://127.0.0.1:5500`
   - Backend API: `http://localhost:5000`

## 🔌 API Endpoints

### Authentication Routes

| Method | Endpoint | Description | Request Body |
|--------|----------|-------------|--------------|
| POST | `/api/auth/signup` | Register a new user | `{ username, email, password }` |
| POST | `/api/auth/login` | User login | `{ email, password }` |

### Course Routes

| Method | Endpoint | Description | Query Parameters |
|--------|----------|-------------|------------------|
| GET | `/api/courses` | Get enrolled courses for a user | `email={userEmail}` |

### Enrollment Routes

| Method | Endpoint | Description | Request Body |
|--------|----------|-------------|--------------|
| POST | `/api/enrollment/enroll` | Enroll a user in a course | `{ username, email, courseName }` |

### Example API Calls

**Register a new user:**
```bash
curl -X POST http://localhost:5000/api/auth/signup \
  -H "Content-Type: application/json" \
  -d '{"username":"john_doe","email":"john@example.com","password":"securepass123"}'
```

**Enroll in a course:**
```bash
curl -X POST http://localhost:5000/api/enrollment/enroll \
  -H "Content-Type: application/json" \
  -d '{"username":"john_doe","email":"john@example.com","courseName":"Web Development"}'
```

## 🎯 Usage

### Getting Started with the Platform

1. **Sign Up**
   - Navigate to the signup page
   - Enter your username, email, and password
   - Click "Sign Up" to create your account

2. **Log In**
   - Go to the login page
   - Enter your registered email and password
   - Click "Login" to access your account

3. **Browse Courses**
   - View featured courses on the homepage
   - Each course displays a title, description, and enrollment option

4. **Search for Courses**
   - Use the search bar in the navigation to find specific courses
   - Results update in real-time as you type

5. **Enroll in Courses**
   - Click "Enroll Now" on any course card
   - Confirm your enrollment in the modal dialog
   - See a success notification upon enrollment

6. **View Your Profile**
   - Click the profile icon in the navbar
   - View all your enrolled courses
   - Access course materials and progress

## 🔒 Security Features

- ✅ **Password Hashing**: Passwords are hashed using bcryptjs before storage
- ✅ **CORS Protection**: Configured to accept requests only from authorized origins
- ✅ **Environment Variables**: Sensitive data stored in `.env` files (not in repository)
- ✅ **Input Validation**: Server-side validation for all user inputs
- ✅ **Error Handling**: Comprehensive error handling and logging
- ✅ **Session Management**: Secure localStorage-based session handling

## 🐛 Troubleshooting

### Common Issues and Solutions

**Problem: MongoDB connection error**
```
Error connecting to MongoDB: MongoNetworkError
```
**Solution:**
- Ensure MongoDB is running: `mongod` (local) or check MongoDB Atlas status
- Verify the connection string in `.env` is correct
- Check if port 27017 is not blocked by firewall

---

**Problem: CORS error in browser console**
```
Access to fetch at 'http://localhost:5000' has been blocked by CORS policy
```
**Solution:**
- Verify frontend is running on `http://127.0.0.1:5500`
- Check CORS origin in `backend/server.js` matches your frontend URL
- Clear browser cache and restart both servers

---

**Problem: "Cannot POST /api/auth/signup" error**
```
Cannot POST /api/auth/signup
```
**Solution:**
- Ensure backend server is running on port 5000
- Check that all dependencies are installed: `npm install` in backend folder
- Verify route files exist in `backend/routes/`

---

**Problem: Login not persisting after page reload**

**Solution:**
- Check browser's localStorage is enabled
- Ensure you're not in incognito/private mode
- Clear localStorage and try logging in again

---

**Problem: Port 5000 already in use**
```
Error: listen EADDRINUSE: address already in use :::5000
```
**Solution:**
- Change the PORT in `.env` file to another port (e.g., 5001)
- Or kill the process using port 5000:
  ```bash
  # Windows
  netstat -ano | findstr :5000
  taskkill /PID <PID> /F
  
  # macOS/Linux
  lsof -ti:5000 | xargs kill -9
  ```

## � Development

### Development Mode

Run the backend in development mode with auto-restart on file changes:
```bash
cd backend
npm run dev
```

This uses nodemon to automatically restart the server when you make changes.

### CORS Configuration

The backend is configured to accept requests from:
- Frontend URL: `http://127.0.0.1:5500`

To update the allowed origin, modify `backend/server.js`:
```javascript
app.use(cors({
    origin: 'http://your-frontend-url:port',
    // ... rest of config
}));
```

### Adding New Courses

To add more courses, edit `frontend/index.html` and add new course cards:
```html
<div class="course-card" id="course-5">
    <div class="course-info">
        <h3>Your Course Name</h3>
        <p>Course description goes here.</p>
        <button class="enroll-btn" data-course="Your Course Name">Enroll Now</button>
    </div>
</div>
```

### Database Schema

**User Model** (`backend/models/User.js`)
```javascript
{
  username: String,
  email: String (unique),
  password: String (hashed),
  courses: [String],
  createdAt: Date
}
```

## 👥 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open a Pull Request**

### Contribution Guidelines
- Follow the existing code style
- Write clear commit messages
- Add tests for new features
- Update documentation as needed

## 📝 License

This project is licensed under the ISC License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [AngularJS](https://angularjs.org/) - Framework for dynamic web apps
- [Express.js](https://expressjs.com/) - Fast, minimalist web framework
- [MongoDB](https://www.mongodb.com/) - NoSQL database
- [Font Awesome](https://fontawesome.com/) - Icon library
- All contributors and open-source community

## 📞 Contact & Support

If you have any questions or need support:
- Create an issue in the GitHub repository
- Email: your.email@example.com
- Project Link: [https://github.com/0SAKESH0/Learning-Platform](https://github.com/0SAKESH0/Learning-Platform)

---

**Made with ❤️ for learners everywhere**

> **Note**: This is a learning/educational project. For production deployment, implement additional security measures, comprehensive testing, performance optimization, and proper error logging.
