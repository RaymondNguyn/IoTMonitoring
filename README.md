# A full-stack web application for monitoring sensor data, featuring a **FastAPI** backend and a **React** frontend. Sensor data is stored in **MongoDB**.

## Tech Stack
- **Backend**: Python, FastAPI, MongoDB
- **Frontend**: React, Vite, TailwindCSS
- **Database**: MongoDB

## Project Structure
```
issp-test/
├── backend/                  # FastAPI backend
│   ├── routes/               # API routes
│   ├── services/             # Business logic (e.g., auth, sensor)
│   ├── models/               # Data models (assets, sensors, users, etc.)
│   ├── main.py               # Entry point for FastAPI
│   ├── database.py           # DB connection and schemas
│   ├── requirements.txt      # Python dependencies
│
├── my-app/                   # React frontend
│   ├── src/
│   │   ├── assets/           # Static assets
│   │   ├── components/       # Reusable UI components
│   │   ├── lib/              # Utilities and configs
│   │   ├── pages/            # Page components
│   │   │   └── projects/     # Project-specific pages
│   ├── public/               # Public assets
│   ├── package.json          # Project dependencies and scripts
│   ├── vite.config.js        # Vite configuration
│
├── README.md                 # Project documentation
```

## Environment Setup

### Prerequisites
- Python 3.10+
- Node.js 18+
- MongoDB

###  Backend Setup (FastAPI)
1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   .\venv\Scripts\activate  # Windows
   source venv/bin/activate # Mac/Linux
   ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a .env file in the backend/ directory with the following:
   ```ini
   MONGO_URI=mongodb://localhost:27017/your-database-name
   SECRET_KEY=your-secret-key
   DEBUG=True
   ```

5. Run the FastAPI server:
   ```bash
   uvicorn main:app --reload
   ```

###  Frontend Setup (React)
1. Navigate to the frontend directory:
   ```bash
   cd my-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a .env file in my-app/ with the following:
   ```ini
   VITE_API_BASE_URL=http://localhost:8000
   ```

4. Run the React development server:
   ```bash
   npm run dev
   ```

##  API Endpoints

###  Authentication
- POST `/api/register` – Register a new user
- POST `/token` – Generate access token
- POST `/api/login` – Log in a user

###  Users
- GET `/api/user` – Fetch user details
- GET `/api/admin/users/{user_id}` – Get user by ID (Admin only)
- GET `/api/admin/dashboard/users` – Get all users from the database (Admin only)
- POST `/api/admin/users/{user_id}/reset-password` – Reset user password (Admin only)
- POST `/api/admin/users/{user_id}/login-as` – Login as another user (Admin only)

###  Projects
- POST `/api/add-projects` – Add a new project
- POST `/api/add-projects/{project_id}/assets` – Get the assets of a project
- GET `/api/add-projects` – Get all projects
- GET `/api/add-projects/{project_id}/assets` – Get the assets of a project
- POST `/api/add-projects/{project_id}/ass-assets` – Add assets to a project

###  Sensors
- POST `/api/receive-sensor-data` – Add sensor data
- POST `/api/add-sensors` – Add a new sensor
- GET `/api/sensor-data/{sensor_id}` – Get data of a specific sensor
- GET `/api/sensor/{asset_id}` – Get sensor data by asset ID

## Example Usage

### Running the Backend

To run the backend:

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Start the FastAPI server:
   ```bash
   uvicorn main:app --reload
   ```

The backend should now be running on http://localhost:8000.

### Running the Frontend

To run the frontend:

1. Navigate to the my-app directory:
   ```bash
   cd my-app
   ```

2. Start the React development server:
   ```bash
   npm run dev
   ```

The frontend should now be available at http://localhost:3000.

##  Notes
- Ensure MongoDB is installed and running on your local machine.
- To configure the backend and frontend, make sure to set up the correct environment variables in .env files as described in the setup sections.
- The API is designed to manage sensor data and user authentication in a secure and scalable way.
