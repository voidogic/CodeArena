# 🌐 CodeShala – Online Coding Learning & Practice Platform

CodeShala is a full-stack web application designed for coding practice, problem-solving, AI-assisted learning, and video-based explanations. It provides an interactive experience with a modern UI, real-time submissions, and powerful admin tools.

## 📚 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Running the Application](#️-running-the-application)
- [API Endpoints](#-api-endpoints)
- [Frontend Routes](#️-frontend-routes)
- [Database Models](#️-database-models)
- [Security Features](#-security-features)
- [License](#-license)
- [Contributing](#-contributing)

## 🎯 Overview

CodeShala is an interactive platform combining:

- Coding problem-solving
- Real-time submission results
- Video explanations
- AI chat support for doubts
- Admin dashboards for content management
- User progress tracking

It is built with React (Frontend) and Node.js + MongoDB (Backend).

## ✨ Features

### 👨‍🎓 User Features

- Register / Login / Logout
- Solve coding problems with built-in editor
- Submit solutions and view evaluation
- Watch solution videos
- Chat with AI for hints
- View submission history
- Track progress

### 🛠 Admin Features

- Add / Update / Delete problems
- Upload & manage videos
- Delete any submission
- Access admin dashboard

### ⚙ Backend Capabilities

- MongoDB for storage
- Redis caching
- Google Generative AI integration
- Cloudinary for media
- JWT-based authentication
- Rate limiting
- Schema validation with Zod

## 🧰 Tech Stack

### Frontend

- React 19
- Vite
- Tailwind CSS + DaisyUI
- Redux Toolkit
- React Router
- Axios
- Monaco Code Editor
- React Hook Form + Zod

### Backend

- Node.js
- Express.js
- MongoDB + Mongoose
- Redis
- JWT Authentication
- Bcrypt
- Google Generative AI
- Cloudinary
- Rate Limiting
- CORS

## 📁 Project Structure

```
CodeShala/
│
├── CodeShaala-Backend-main/
│   ├── index.js
│   ├── vercel.json
│   ├── package.json
│   └── src/
│       ├── config/          # DB & Redis config
│       ├── controllers/     # Business logic
│       ├── middleware/      # Auth, rate limiter, admin
│       ├── models/          # MongoDB schemas
│       ├── routes/          # API Routes
│       └── utils/           # Helper utilities
│
└── CodeShaala-Frontend-main/
    ├── index.html
    ├── package.json
    ├── vite.config.js
    └── src/
        ├── components/
        ├── pages/
        ├── store/
        └── utils/
```

## 🚀 Installation

### Prerequisites

- Node.js v16+
- MongoDB (Local / Atlas)
- Redis server
- Cloudinary account
- Google GenAI API key

### 🔧 Backend Setup

1. Navigate to backend:
```bash
cd CodeShaala-Backend-main
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file:
```env
PORT=5000

DB_CONNECT_STRING=your_mongodb_uri
REDIS_PASS=redis://localhost:6379
JWT_SECRET=your_jwt_secret
JUDGE0_KEY=your_judge0_secret_key
GOOGLE_AI_API_KEY=your_genai_key
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

### 🎨 Frontend Setup

1. Navigate:
```bash
cd CodeShaala-Frontend-main
```

2. Install:
```bash
npm install
```

3. Create `.env`:
```env
VITE_API_URL=http://localhost:5000
```

## ▶️ Running the Application

### Backend
```bash
cd CodeShaala-Backend-main
npm run dev
```

Server starts at: `http://localhost:5000`

### Frontend
```bash
cd CodeShaala-Frontend-main
npm run dev
```

Frontend runs at: `http://localhost:5173`

## 🔌 API Endpoints

### Authentication – `/user`

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/user/register` | Register user |
| POST | `/user/login` | Login user |
| POST | `/user/logout` | Logout |
| GET | `/user/profile` | Get user profile |
| GET | `/user/check-auth` | Validate token |

### Problems – `/problem`

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/problem` | Get all problems |
| GET | `/problem/:id` | Get problem details |
| POST | `/problem` | Create problem (Admin) |
| PUT | `/problem/:id` | Update (Admin) |
| DELETE | `/problem/:id` | Delete (Admin) |

### Submissions – `/submission`

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/submission` | Submit code |
| GET | `/submission/:userId` | User submissions |
| GET | `/submission/history` | Submission history |
| DELETE | `/submission/:id` | Delete submission |

### AI – `/ai`

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/ai/chat` | Chat with AI |
| POST | `/ai/solve-doubt` | AI help for problems |

### Videos – `/video`

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/video` | Get all videos |
| GET | `/video/:problemId` | Get problem videos |
| POST | `/video` | Upload video (Admin) |
| DELETE | `/video/:id` | Delete video |

## 🗺️ Frontend Routes

| Route | Page |
|-------|------|
| `/` | Landing Page |
| `/login` | Login |
| `/signup` | Sign Up |
| `/home` | Homepage |
| `/problem/:id` | Problem + Code Editor |
| `/submission-history` | User submissions |
| `/admin` | Admin Dashboard |
| `/admin/upload` | Add problems |
| `/admin/video` | Video manager |
| `/admin/delete` | Content removal |

## 🗄️ Database Models

### User
```javascript
{
  username: String,
  email: String,
  password: String,
  role: String,
  problemsSolved: [ObjectId],
  submissions: [ObjectId],
  createdAt: Date
}
```

### Problem
```javascript
{
  title: String,
  description: String,
  difficulty: String,
  testCases: Array,
  solutions: [ObjectId],
  creator: ObjectId,
  createdAt: Date
}
```

### Submission
```javascript
{
  userId: ObjectId,
  problemId: ObjectId,
  code: String,
  language: String,
  status: String,
  output: String,
  executionTime: Number,
  submittedAt: Date
}
```

### Solution Video
```javascript
{
  problemId: ObjectId,
  title: String,
  videoUrl: String,
  explanation: String,
  uploadedAt: Date
}
```

## 🔐 Security Features

- JWT Authentication
- Password hashing (bcrypt)
- Rate limiting
- Input validation with Zod
- Role-based access control
- CORS protection
- Redis caching

## 📜 License

ISC License

## 🤝 Contributing

Active development is in progress — features and updates are being added regularly.

---

Made with ❤️ by the CodeShala Team
