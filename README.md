# Todo Responsive Application

This is a Todo application built with Node.js, Express, and SQLite. It allows users to register, log in, and perform CRUD (Create, Read, Update, Delete) operations on tasks. Only authenticated users can manage tasks and update their profile information.

       +-------------+              +-------------+
       |  regUsers   |              |    tasks    |
       +-------------+              +-------------+
       | id (PK)     |              | id (PK)     |
       | email       |              | task        |
       | password    |              | status      |
       | name        |              | userIdn (FK)|
       | phone       |              +-------------+
       +-------------+

## Features

- **User Authentication**: Users can register and log in. Passwords are securely hashed with bcrypt, and JSON Web Tokens (JWT) are used for authorization.
- **CRUD Operations**: Authenticated users can create, read, update, and delete their tasks.
- **Profile Management**: Authenticated users can update their profile details.
- **Protected Routes**: Certain routes require JWT-based authentication for access.

## Project Structure

- `index.js`: The main index file, which initializes the Express app, database connection, and defines the API endpoints.
- `todo.db`: SQLite database file that stores user and task information.

## Prerequisites

- Node.js
- SQLite3

## Installation

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_folder>

2. Install Dependencies
    
    npm install

3. Start the server
 
    node index.js

## API Endpoints


## User Registration

Endpoint: /
Method: POST
Description: Registers a new user.
Request Body:{
  "id": "user_id",
  "mailId": "user_email",
  "pswrd": "user_password",
  "name": "user_name",
  "mblNum": "user_phone"
}
Response: "ok" if registration is successful, otherwise "not ok".

## User Login

Endpoint: /login
Method: POST
Description: Logs in a user and provides a JWT token.
Request Body:{
  "mailId1": "user_email",
  "pswrd1": "user_password"
}
Response:

Success:

{
  "jwtToken": "token",
  "userLoginName": "user_name",
  "userIdt": "user_id"
}

Failure:

 status:401 (password Mismatch)
 message:'not ok1'

 status:404 (User Not Found)
 message:'not ok2'

## Middleware for Authorization

Description: Protects routes by checking for a valid JWT in the Authorization header.

## Update Profile Information

Endpoint: /detailsupdate/:userIdtn
Method: PUT
Description: Updates a user's profile information.
Request Body:{
  "updName": "new_name",
  "updEmail": "new_email",
  "updPswd": "new_password",
  "updPhone": "new_phone"
}
Response:'updated' if successful and "error message" if unsuccessful.

## Get Profile Information

Endpoint: /profileInfo/:pid
Method: GET
Description: Retrieves profile information of a specific user.
Response: User profile data.

## Delete User

Endpoint: /delUser/:delId
Method: DELETE
Description: Deletes a user and all their associated tasks.
Response: "deleted" if successful and "error message" if unsuccessful.

+-----------------------------------------------------------------------------------------+

## Get Tasks

Endpoint: /todos/:id
Method: GET
Description: Retrieves all tasks for a specific user.
Response: Array of tasks if successful, "error message" if unsuccessful.

## Add New Task

Endpoint: /todos
Method: POST
Description: Adds a new task for a user.
Request Body:{
  "id": "task_id",
  "task": "task_description",
  "status": "task_status",
  "userId": "user_id"
}
Response: "ok" if successful,"error message" if unsuccessful.

## Delete Task

Endpoint: /todos/:id
Method: DELETE
Description: Deletes a task by its ID.
Response: "deleted" if successful,"error message" if unsuccessful.

## Update Task Status

Endpoint: /todos/:id
Method: PUT
Description: Updates the status of a task.
Request Body:{
  "status": "new_status"
}
Response: "updated" if successful, "error message" if unsuccessful.
