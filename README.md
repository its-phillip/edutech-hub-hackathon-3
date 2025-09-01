[README.md](https://github.com/user-attachments/files/22077445/README.md)
EduTech Hub - Full project bundle
---------------------------------
What's included:One-Click Deploy (preconfigured for this repo)
----------------------------------------------

### Deploy Frontend (Vercel)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/its-phillip/edutech-hub-hackathon-3&project-name=edutech-hub&repository-name=edutech-hub-hackathon-3&root-directory=frontend&build-command=npm%20run%20build&output-directory=dist)

### Deploy Frontend (Netlify)
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/its-phillip/edutech-hub-hackathon-3)

### Deploy Backend (Render)
[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)

Notes:
- After deploying the backend, set the backend URL as `VITE_API_URL` in your frontend environment variables on Vercel/Netlify.
- For Render, set the root directory to `backend` and start command `node index.js`.
- If you want Railway instead of Render, tell me and I'll add a Railway button.

- frontend/ (Vite + React + Tailwind)
- backend/  (Express with simple JSON storage)
- assets/   (place to add logo and extracted images)
- Dockerfile for building a production image
- This README with deploy instructions

Quick start (local)
-------------------
1) Frontend
   cd frontend
   npm install
   npm run dev
   Open http://localhost:5173

2) Backend (for API)
   cd backend
   npm install
   node index.js
   Server runs on http://localhost:4000 and serves the built frontend when frontend/dist exists.

Build and run combined (recommended)
------------------------------------
- Build frontend first:
    cd frontend
    npm install
    npm run build

- Start backend (which serves the built frontend):
    cd ../backend
    npm install
    node index.js

Docker (one-step)
-----------------
Build:
  docker build -t edutech-hub .
Run:
  docker run -p 4000:4000 edutech-hub

Notes / Next steps
------------------
- Replace assets/logo.png with the logo extracted from your pitch deck (I included the original PDF in the assets folder).
- To use a managed DB, swap the JSON file storage with PostgreSQL / MySQL.
- For production hosting: consider Render.com, Railway, Heroku (backend) + Netlify/Vercel (frontend) or deploy as a single Docker container as above.


One-Click Deploy (preconfigured for this repo)
----------------------------------------------

### Deploy Frontend (Vercel)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/its-phillip/edutech-hub-hackathon-3&project-name=edutech-hub&repository-name=edutech-hub-hackathon-3&root-directory=frontend&build-command=npm%20run%20build&output-directory=dist)

### Deploy Frontend (Netlify)
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/its-phillip/edutech-hub-hackathon-3)

### Deploy Backend (Render)
[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)

Notes:
- After deploying the backend, set the backend URL as `VITE_API_URL` in your frontend environment variables on Vercel/Netlify.
- For Render, set the root directory to `backend` and start command `node index.js`.
- If you want Railway instead of Render, tell me and I'll add a Railway button.

Postgres & Docker Compose
-------------------------
You can run the full stack locally with Docker Compose (Postgres + app):

  docker-compose up --build

The backend will connect to Postgres via the DATABASE_URL set in docker-compose.yml.
Migrations in backend/migrations will be executed automatically by the official postgres image.

Database fallback
-----------------
If DATABASE_URL is not present, the backend falls back to simple JSON storage at backend/data.json.
This makes local testing easy without a database, but for production use Postgres (or another DB).

GitHub Actions
--------------
- .github/workflows/ci.yml builds the frontend and installs backend dependencies for CI.
- .github/workflows/docker-publish.yml builds and pushes a Docker image to Docker Hub (requires secrets).

