# Task Management API

## Deployment URL
Deployed API will be available at:


URL placeholder


A REST API for managing tasks with user authentication, built with Node.js, Express, and SQLite.

## Features

- User registration and authentication
- JWT-based authentication
- CRUD operations for tasks
- User-specific task management
- SQLite database with Sequelize ORM

## API Endpoints

### Authentication
- `POST /api/register` - Register a new user
- `POST /api/login` - Login user

### Tasks (Protected Routes)
- `GET /api/tasks` - Get all tasks for authenticated user
- `GET /api/tasks/:id` - Get single task
- `POST /api/tasks` - Create new task
- `PUT /api/tasks/:id` - Update task
- `DELETE /api/tasks/:id` - Delete task

### Utility
- `GET /health` - Health check endpoint
- `GET /` - API information

## Testing in Production

Once deployed, I will test the API using Postman.



### Health Check

GET https://placeholder-app-name.onrender.com/health

### API Health
GET https://placeholder-app-name.onrender.com/api/health

### Register
POST https://placeholder-app-name.onrender.com/api/register
Content-Type: application/json

### Login
POST https://placeholder-app-name.onrender.com/api/login
Content-Type: application/json

### Get Tasks (requires JWT)
GET https://placeholder-app-name.onrender.com/api/tasks
Authorization: Bearer YOUR_JWT_TOKEN

## Local Development

1. Install dependencies:
   ```bash
   npm install
   ```
2. Seed the database (optional):
    ```bash
    npm run seed
    ```
3. Start the server:
    ```bash
    npm start
    ``
4. The API will be available at `http://localhost:3000`

### Sample Users
If you run the seed script, you'll have these test users available:
- **john@example.com** / password123 (3 tasks)
- **jane@example.com** / password123 (3 tasks)
- **mike@example.com** / password123 (4 tasks)

You can use these accounts to test the API without having to register new users.

### Testing
Use the following sample requests to test the API:

**Register a user:**

```bash
POST /api/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

**Login:**

```bash
POST /api/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

**Create a task (requires authentication):**
```bash
POST /api/tasks
Content-Type: application/json
Authorization: Bearer YOUR_JWT_TOKEN

{
  "title": "Complete project",
  "description": "Finish the task management API",
  "priority": "high"
}
```

### Database
This API uses SQLite for simplicity. The database file (tasks.db) will be created automatically when you start the server.
**Note for deployment**: SQLite databases on platforms like Render will reset when containers restart. For persistent storage in production, consider upgrading to PostgreSQL.

### Environment Variables
- `NODE_ENV` - Environment (development/production)
- `PORT` - Server port (default: 3000)
- `JWT_SECRET` - Secret key for JWT tokens
- `JWT_EXPIRES_IN` - JWT token expiration time
- `DB_NAME` - Database file name

## Environment Variables (Production)

These must be configured in the Render dashboard:

- `NODE_ENV=production`
- `PORT=3000` (Render may override this automatically)
- `JWT_SECRET=your-secure-production-key`
- `JWT_EXPIRES_IN=24h`
- `DB_NAME=tasks.db`


### Deployment
This API is ready to deploy to cloud platforms like Render. Make sure to:
1. Set appropriate environment variables
2. Use a secure JWT secret in production
3. Consider database limitations with SQLite


## Auto-Deploy Verification

Render automatically redeploys whenever you push to the deployed branch.

To verify auto-deployment:

1. Add or modify a small endpoint (for example, `/api/health`)
2. Commit and push the change to GitHub
3. Watch Render’s “Deploy Logs” tab to see the new build start
4. Once live, test the updated endpoint in Postman to confirm changes deployed successfully
