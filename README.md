# JobBoard

A full-stack job board platform built with the **MERN stack** (MongoDB, Express, React, Node.js) - connecting employers with job seekers.

---

## Features

**For Job Seekers**
- Browse and search jobs by keyword, location, and job type
- Apply with a cover letter and resume upload (PDF/Word)
- Track application status in a personal dashboard

**For Employers**
- Post, manage, and delete job listings
- View all applicants per job with full details
- Update application status (Pending → Reviewed → Shortlisted → Accepted/Rejected)

**General**
- JWT-based authentication with role-based access control
- Responsive UI — works on mobile, tablet, and desktop
- Protected routes for employer-only and job-seeker-only pages

---

## Tech Stack

| Layer      | Technology                          |
|------------|--------------------------------------|
| Frontend   | React 19, Tailwind CSS, React Router v7 |
| Backend    | Node.js, Express 5                  |
| Database   | MongoDB with Mongoose               |
| Auth       | JWT (JSON Web Tokens) + bcryptjs    |
| File Upload| Multer (resume uploads)             |
| HTTP Client| Axios                               |

---

## Getting Started (Local Development)

### Prerequisites
- Node.js v18+
- MongoDB Atlas account (free) or local MongoDB
- npm

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/jobboard.git
cd jobboard
```

### 2. Set up the server
```bash
cd server
npm install
```

Create a `.env` file inside the `server/` folder:
```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_super_secret_key_here
NODE_ENV=development
```

### 3. Set up the client
```bash
cd ../client
npm install
```

### 4. Run both servers

In one terminal (backend):
```bash
cd server
npm run dev
```

In another terminal (frontend):
```bash
cd client
npm start
```

The app runs at **http://localhost:3000**

---

## Project Structure

```
jobboard/
├── client/                 # React frontend
│   └── src/
│       ├── components/     # Reusable UI (Navbar, JobCard, Spinner)
│       ├── context/        # Auth state management
│       ├── pages/          # Route-level components
│       └── utils/          # Axios instance
└── server/                 # Express backend
    ├── config/             # MongoDB connection
    ├── controllers/        # Business logic
    ├── middleware/         # Auth & file upload
    ├── models/             # Mongoose schemas
    └── routes/             # API endpoints
```

---

## API Endpoints

| Method | Endpoint                          | Access         | Description               |
|--------|-----------------------------------|----------------|---------------------------|
| POST   | `/api/auth/register`              | Public         | Register new user         |
| POST   | `/api/auth/login`                 | Public         | Login                     |
| PUT    | `/api/auth/profile`               | Private        | Update profile            |
| GET    | `/api/jobs`                       | Public         | List jobs (with filters)  |
| POST   | `/api/jobs`                       | Employer       | Create job posting        |
| DELETE | `/api/jobs/:id`                   | Employer       | Delete job                |
| POST   | `/api/applications/:jobId`        | Job Seeker     | Submit application        |
| GET    | `/api/applications/myapplications`| Job Seeker     | View my applications      |
| GET    | `/api/applications/job/:jobId`    | Employer       | View job applicants       |
| PUT    | `/api/applications/:id/status`    | Employer       | Update applicant status   |

---

## Deployment

- **Frontend:** Vercel
- **Backend:** Render
- **Database:** MongoDB Atlas

See [Deployment Guide](#) for step-by-step instructions.

---

## License

MIT
