# AI BlogNest API

## Overview

The **AI BlogNest API** is a powerful, secure, and intelligent REST API platform designed to simplify blog creation, content management, and AI-assisted writing.

Built with a modular **Model-View-Controller (MVC)** architecture, it serves as a headless, AI-powered **Content Management System (CMS)** that combines traditional blogging capabilities with Generative AI.

The platform integrates **Google Gemini AI** to provide intelligent features such as automated thematic blog generation and semantic content summarization, helping content creators generate and manage content efficiently.

---

## Tech Stack

- **Runtime Environment:** Node.js
- **Web Framework:** Express.js
- **Database:** MongoDB
- **ODM:** Mongoose
- **Authentication:** JSON Web Tokens (JWT) for stateless authentication
- **Security:** bcrypt.js for password hashing, input sanitization, and role-based route guards
- **AI Integration:** Google Gemini API

---

## Core Features

1. **Stateless JWT Authentication**  
   Secure user registration and login workflows with token-based authentication.

2. **Role-Based Access Control**  
   Middleware-based authorization to evaluate user permissions across different roles such as Admin, Editor, Author, and Reader.

3. **CRUD Blog Engine**  
   Complete blog content management with support for creating, reading, updating, and deleting blog posts.

4. **AI Blog Generation**  
   Generates full-length, structured blog posts from high-level thematic prompts using Google Gemini AI.

5. **AI Content Summarizer**  
   Processes lengthy article content and generates concise summaries using AI-powered semantic compression.

---

## Prerequisites

Before running this project locally, make sure the following are installed:

- **Node.js** v16 or above
- **npm** v8 or above
- **MongoDB Community Server** running locally on port `27017`, or a **MongoDB Atlas** cloud cluster
- **Postman** or the **Thunder Client** VS Code extension for API testing

---

## Local Setup & Installation

### 1. Clone the Repository

Clone the repository and navigate to the project root directory:

    git clone https://github.com/balafromtn/BlogNest-API.git
    cd AI-BlogNest-API

### 2. Install Dependencies

Install all required Node.js dependencies:

    npm install

### 3. Configure Environment Variables

Create a `.env` file in the root directory alongside `server.js`.

Add the following environment variables:

    PORT=8000
    MONGO_URI=mongodb://127.0.0.1:27017/blognest
    JWT_SECRET=your_secure_random_string
    GEMINI_API_KEY=your_google_gemini_api_key

> **Note:** If you are using MongoDB Atlas, replace the `MONGO_URI` value with your MongoDB Atlas connection string.

### 4. Start the Development Server

Run the backend development server:

    npm run dev

If everything is configured correctly, the console should display messages similar to:

    Server running on port 8000
    MongoDB connected

---

# API Endpoints Reference

## Authentication Routes

**Base URL:** `/api/auth`

### Register

    POST /api/auth/register

Registers a new user.

**Request Body:**

    {
      "name": "John Doe",
      "email": "john@example.com",
      "password": "your_password"
    }

### Login

    POST /api/auth/login

Authenticates an existing user and returns a JWT token.

**Request Body:**

    {
      "email": "john@example.com",
      "password": "your_password"
    }

---

## Blog Management Routes

**Base URL:** `/api/blogs`

### Authentication Required

Include the following header in requests:

    Authorization: Bearer <token>

### Get All Blogs

    GET /api/blogs

Fetches a list of all existing blog posts.

### Create a Blog

    POST /api/blogs

Creates a new blog document.

**Request Body:**

    {
      "title": "Introduction to Artificial Intelligence",
      "content": "Artificial Intelligence is...",
      "category": "Technology"
    }

---

## AI Services

**Base URL:** `/api/ai`

### Authentication Required

Include the following header in requests:

    Authorization: Bearer <token>

### Generate Blog

    POST /api/ai/generate-blog

Uses Google Gemini AI to generate a structured blog post based on a given topic and category.

**Request Body:**

    {
      "topic": "Future of Artificial Intelligence",
      "category": "Technology"
    }

### Summarize Content

    POST /api/ai/summarize

Uses AI to generate a concise summary from existing content.

**Request Body:**

    {
      "content": "Your long-form article content goes here..."
    }

---

# Authentication

Protected endpoints require a valid JWT token.

Add the token to the request header:

    Authorization: Bearer <your_jwt_token>

The server validates the token before allowing access to protected resources.

---

# Project Structure

A typical project structure looks like this:

    AI-BlogNest-API/
    │
    ├── controllers/
    ├── middleware/
    ├── models/
    ├── routes/
    ├── config/
    ├── .env
    ├── .gitignore
    ├── package.json
    ├── package-lock.json
    └── server.js

> **Note:** The exact folder structure may vary depending on the implementation.

---

# Security

The API implements multiple security mechanisms:

- JWT-based stateless authentication
- Password hashing using `bcrypt.js`
- Protected API routes
- Role-based authorization
- Input validation and sanitization
- Environment variables for sensitive credentials
- Secure handling of Gemini API credentials

> **Important:** Never commit your `.env` file or API keys to GitHub.

Make sure `.env` and `node_modules/` are included in your `.gitignore`:

    .env
    node_modules/

---

# Testing the API

You can test the API using:

- **Postman**
- **Thunder Client**
- **Any REST API client**

## Typical Testing Workflow

    Register User
          ↓
    Login
          ↓
    Receive JWT Token
          ↓
    Add Authorization Header
          ↓
    Access Protected Routes
          ↓
    Create / Read Blogs
          ↓
    Use AI Generation & Summarization

---

# Environment Variables

| Variable | Description | Example |
|---|---|---|
| `PORT` | Port used by the Express server | `8000` |
| `MONGO_URI` | MongoDB connection string | `mongodb://127.0.0.1:27017/blognest` |
| `JWT_SECRET` | Secret key used for JWT authentication | `your_secure_random_string` |
| `GEMINI_API_KEY` | Google Gemini API key | `your_google_gemini_api_key` |

---

# License

This project is intended for educational and development purposes.