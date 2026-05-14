```markdown
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

### 2. Set up environment variables
Create a `.env` file inside the `server/` folder:
```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_super_secret_key_here
NODE_ENV=development
```

### 3. Install all dependencies with one command
```bash
npm run install-all
```

### 4. Run both servers with one command
```bash
npm run dev
```

The app runs at **http://localhost:3000**
The API runs at **http://localhost:5000**

---

## Available Scripts

Run from the **root folder**:

| Command | Description |
|---|---|
| `npm run dev` | Runs both frontend and backend together |
| `npm run server` | Runs backend only |
| `npm run client` | Runs frontend only |
| `npm run install-all` | Installs dependencies for root, server, and client |

---

## Project Structure

```
jobboard/
├── package.json            # Root package with concurrently scripts
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
    ├── routes/             # API endpoints
    └── uploads/            # Resume file storage (gitignored)
```

---

## API Endpoints

| Method | Endpoint                           | Access     | Description               |
|--------|------------------------------------|------------|---------------------------|
| POST   | `/api/auth/register`               | Public     | Register new user         |
| POST   | `/api/auth/login`                  | Public     | Login                     |
| GET    | `/api/auth/profile`                | Private    | Get profile               |
| PUT    | `/api/auth/profile`                | Private    | Update profile            |
| GET    | `/api/jobs`                        | Public     | List jobs (with filters)  |
| GET    | `/api/jobs/:id`                    | Public     | Get single job            |
| POST   | `/api/jobs`                        | Employer   | Create job posting        |
| PUT    | `/api/jobs/:id`                    | Employer   | Update job                |
| DELETE | `/api/jobs/:id`                    | Employer   | Delete job                |
| GET    | `/api/jobs/employer/myjobs`        | Employer   | Get my job postings       |
| POST   | `/api/applications/:jobId`         | Job Seeker | Submit application        |
| GET    | `/api/applications/myapplications` | Job Seeker | View my applications      |
| GET    | `/api/applications/job/:jobId`     | Employer   | View job applicants       |
| PUT    | `/api/applications/:id/status`     | Employer   | Update applicant status   |

---

## Environment Variables

| Variable | Description |
|---|---|
| `PORT` | Port for the backend server (default: 5000) |
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | Secret key for JWT token signing |
| `NODE_ENV` | Environment (development/production) |

---

## Deployment

- **Frontend:** Vercel
- **Backend:** Render
- **Database:** MongoDB Atlas

---