# POST /task

The `POST /tasks` endpoint allows clients to create new tasks in the task management system. This endpoint is publicly accessible and does not require authentication.

A task represents a unit of work, including attributes such as title, description, due date, status, and priority. Developers can use this endpoint to add tasks dynamically to a user's list or queue.



## Use Cases

- User opens a to-do application.
- They enter task details such as the title, due date, and priority.
- The application sends a POST request to `/tasks` with the task data.
- The server responds with **201 Created** status and the created task details.



## How to Post Task

The `POST /tasks` endpoint allows you to create a new task by providing task details in the request body.

1. Send a `POST` request to `/tasks` endpoint.
2. Use **JSON** format in the request body.
3. Include the following fields in your request body:

   - `title` – The title of the task (**required**)
   - `description` – Details about the task (**optional**)
   - `due_date` – Due date in ISO 8601 format (**optional**)
   - `priority` – An integer from 1 (low) to 5 (high)

### Request Example

```json
{
  "title": "Finish API Documentation",
  "description": "Complete the POST /tasks section in the Task API doc.",
  "due_date": "2025-04-25T18:00:00Z",
  "priority": 3
}
```

### Response

On Success – `201 Created`

```json
{
  "id": "a1b2c3d4e5",
  "title": "Finish API Documentation",
  "description": "Complete the POST /tasks section in the Task API doc.",
  "due_date": "2025-04-25T18:00:00Z",
  "priority": 3,
  "status": "pending",
  "created_at": "2025-04-21T14:32:10Z"
}
```

### On Error – `400 Bad Request`

Returned when required fields are missing or data is invalid.



## POST Task Response Fields

| Field        | Type              | Description                                      |
|--------------|-------------------|--------------------------------------------------|
| `id`         | string            | Unique identifier of the task                    |
| `title`      | string            | Title of the task                                |
| `description`| string            | Additional details about the task                |
| `due_date`   | string (ISO 8601) | Deadline for the task                            |
| `priority`   | integer           | Priority level from 1 (low) to 5 (high)          |
| `status`     | string            | Current status (e.g., pending, completed)        |
| `created_at` | string (ISO 8601) | Timestamp when the task was created              |