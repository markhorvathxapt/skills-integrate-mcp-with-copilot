# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities as an authenticated teacher
- Log in and out with server-managed teacher sessions

## Getting Started

1. Install the dependencies:

   ```
   pip install fastapi uvicorn
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/auth/login`                                                       | Start a teacher session                                             |
| POST   | `/auth/logout`                                                      | End the current teacher session                                     |
| GET    | `/auth/me`                                                          | Get the current teacher                                            |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu`   | Sign up for an activity as a teacher                               |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student as a teacher                                  |

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

Activity data and sessions are stored in memory, which means they will be reset when the server restarts. Teacher credentials are stored in `teachers.json` as salted PBKDF2 password hashes.

The starter teacher account is `teacher` with password `mergington-teacher`.
