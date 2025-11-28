# Task Management API

## Deployment URL
Deployed API is available at:

**https://assignment10-api.onrender.com**

A REST API for managing tasks with user authentication, built with Node.js, Express, and SQLite.



## Features

- User registration and authentication
- JWT-based authentication
- CRUD operations for tasks
- User-specific task management
- SQLite database using Sequelize ORM



## API Endpoints

### Authentication
- POST /api/register — Register a new user
- POST /api/login — Login user and receive JWT token

### Tasks (Protected Routes)
- GET /api/tasks — Get all tasks for authenticated user
- GET /api/tasks/:id — Get a single task
- POST /api/tasks — Create new task
- PUT /api/tasks/:id — Update an existing task
- DELETE /api/tasks/:id — Delete a task

### Utility
- GET /health — Basic server health check
- GET /api/health — API health, uptime, environment
- GET / — API root information



## Testing in Production

Use Postman to test the deployed API.

### Health Check
    GET https://assignment10-api.onrender.com/health

### API Health
    GET https://assignment10-api.onrender.com/api/health

### Register
    POST https://assignment10-api.onrender.com/api/register
    Content-Type: application/json

### Login
    POST https://assignment10-api.onrender.com/api/login
    Content-Type: application/json

### Get Tasks (requires JWT)
    GET https://assignment10-api.onrender.com/api/tasks
    Authorization: Bearer YOUR_JWT_TOKEN



## Local Development

1. Install dependencies:

        npm install

2. Seed the database (optional):

        npm run seed

3. Start the server:

        npm start

4. API available at:

        http://localhost:3000



## Sample Users (if seeded)

- john@example.com / password123  
- jane@example.com / password123  
- mike@example.com / password123  

Seeded by running:

        npm run seed



## Database

This API uses a local SQLite database for simplicity.

Note: On Render, SQLite storage resets when the container restarts.
For real production use, switch to PostgreSQL.



## Environment Variables

### Local Development (.env)

    NODE_ENV=development
    PORT=3000
    JWT_SECRET=your-dev-secret
    JWT_EXPIRES_IN=24h
    DB_NAME=tasks.db

### Production (Render Dashboard)

    NODE_ENV=production
    PORT=3000
    JWT_SECRET=your-secure-production-key
    JWT_EXPIRES_IN=24h
    DB_NAME=tasks.db



## Deployment Notes

This API is deployed to Render using:

- Build command: npm install
- Start command: npm start

Ensure:

1. package.json start script runs server.js
2. CORS is enabled in server.js
3. Environment variables are correctly configured in Render



## Auto-Deploy Verification

Render automatically redeploys when you push to the deployed branch.

To verify auto-deployment:

1. Modify a small part of the code (example: change the message in /api/health)
2. Commit and push:

        git add .
        git commit -m "Test auto-deploy with updated API health message"
        git push

3. Watch the Render Deploy Logs for a new build
4. Call the updated endpoint and confirm the change is live

