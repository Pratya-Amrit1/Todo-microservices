# User Service

A microservice for managing user authentication and user data in a Todo microservices architecture. This service handles user registration and user retrieval operations.

## Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js 5.2.1
- **Database**: MongoDB (via Mongoose 9.1.6)
- **Security**: bcrypt 6.0.0 (password hashing)
- **Environment**: dotenv 17.2.3
- **CORS**: cors 2.8.6

## How It Works

This service provides RESTful API endpoints for user management:
- **User Registration**: Allows new users to register with name, email, and password. Passwords are automatically hashed using bcrypt before storage.
- **User Retrieval**: Fetches all registered users from the database.
- The service connects to MongoDB and handles user data with proper validation and error handling.

## Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or remote instance)
- npm or yarn

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd user-service
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```env
PORT=3000
MONGO_URI=mongodb://localhost:27017/todo-app
```

4. Update the `MONGO_URI` with your MongoDB connection string.

## Running the Application

### Development Mode
```bash
npm run dev
```
This will start the server with nodemon for automatic reloading on file changes.

### Production Mode
```bash
npm start
```

The server will start on the port specified in your `.env` file (default: 3000).
