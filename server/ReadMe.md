# Task Management Server

This is the server-side component of a task management application built using Node.js, Express, and MongoDB. The server provides API endpoints for user authentication and task management. This documentation outlines the API endpoints and how to use them.

This documentation provides an overview of the API endpoints for the Task Management Server. You can use these endpoints to build a client-side application for task management.

## Table of Contents

- [Installation](#installation)
- [API Endpoints](#api-endpoints)
  - [Authentication](#authentication)
    - [Register](#register)
    - [Sign In](#sign-in)
  - [Tasks](#tasks)
    - [Add Task](#add-task)
    - [Get All Tasks](#get-all-tasks)
    - [Edit Task](#edit-task)
    - [Change Task Status](#change-task-status)
    - [Delete Task](#delete-task)

## Installation

Before running the server, make sure you have Node.js and MongoDB installed on your system. Follow these steps to set up the server:

### API Endpoints

#### Authentication

##### Register

- **URL:** `/auth/register`
- **Method:** POST
- **Description:** Register a new user.
- **Request Body:**
  ```json
  {
    "username": "exampleUser",
    "email": "user@example.com",
    "password": "examplePassword"
  }
  ```
- Response:

        200 OK: User successfully signed in, and a JWT token is provided.
        400 Bad Request: Invalid email, password, or user does not exist.

#### Tasks

##### Add Task

- **URL:** `/task/add`
- **Method:** POST
- **Description:** Add a new task.
- **Request Body:**

  ```json
  {
    "task": "Instruction Set To Add"
  }
  ```

- Response:

       200 OK: Task successfully added.
       400 Bad Request: Invalid task input.

##### Get All Tasks

- **URL:** `/task/all`
- **Method:** GET
- **Description:** Get all tasks for a specific user.
- **Query Parameters:**
- `id`: User ID

- Response:

       200 OK: List of tasks retrieved successfully.
       400 Bad Request: Invalid user ID or task retrieval failed.

##### Edit Task

- **URL:** `/task/edit/:id`
- **Method:** PUT
- **Description:** Edit a task by ID.
- **Request Parameters:**
- `id`: Task ID
- **Request Body:**

```json
{
  "task": "Instruction Set To Add"
}
```

- Response:

       200 OK: Task updated successfully.
       400 Bad Request: Invalid task input or task not found.

##### Change Task Status

- **URL:** `/task/status`
- **Method:** PUT
- **Description:** Change the status of a task (e.g., from "backlog" to "todo").
- **Request Body:**

```json
{
"id": "taskID",
"string": "right"
}

-------Changed To-------

{
"id": "taskID",
"string": "left"
}

```

- The "string" value of "right" moves the task status forward, while "left" moves it backward.

- Response:

       200 OK: Task status changed successfully.
       400 Bad Request: Invalid input or task not found.

##### Delete Task

- **URL:** `/task/delete/:id`
- **Method:** DELETE
- **Description:** Delete a task by ID.
- **Request Parameters:**
- `id`: Task ID

- Response:

       200 OK: Task deleted successfully.
       400 Bad Request: Task not found or deletion failed.
