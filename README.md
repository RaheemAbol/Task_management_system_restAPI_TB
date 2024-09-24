### **Ticket Breakdown: Task Management System**

---

#### **Ticket 1: Set Up Spring Boot Project**

- **Tasks:**
  - Set up a Spring Boot project with the necessary dependencies (Spring Web, Spring Data JPA, MySQL Driver).
  - Make sure to configure the `application.properties` file with your MySQL credentials and set up the `ddl-auto` property for schema generation.

---

#### **Ticket 2: Create the `Task` Entity**

- **Tasks:**
  - Create the `Task` entity class with the following fields:
    - `id` (Primary key, auto-generated using `@Id` and `@GeneratedValue`)
    - `title` (a simple `String` field for task titles)
    - `description` (a `String` field for task descriptions)
    - `status` (a `String` field for the task status like "Pending", "In Progress", or "Completed")

- **Hints:**
  - Annotate the class with `@Entity` to map it to the database.
  - Use appropriate JPA annotations like `@Id` and `@GeneratedValue` for the primary key.

---

#### **Ticket 3: Create the `TaskRepository` Interface**

- **Tasks:**
  - Create a repository interface by extending `JpaRepository<Task, Long>` to automatically generate CRUD operations for the `Task` entity.

- **Hints:**
  - This interface will handle database operations like saving, updating, finding, and deleting tasks without requiring manual SQL queries.

---

#### **Ticket 4: Create the `TaskService` Class**

- **Tasks:**
  - Create a service class (`TaskService`) to implement the business logic for managing tasks.
  - Implement the following methods:
    - `getAllTasks()` to fetch all tasks from the repository.
    - `getTaskById(Long id)` to retrieve a task by its ID.
    - `createTask(Task task)` to create and save a new task.
    - `updateTask(Long id, Task updatedTask)` to update an existing task:
      - **Steps for `updateTask`:**
        1. Retrieve the task using `findById(id)`.
        2. If the task exists, modify its fields.
        3. Save the updated task using `save()`.
    - `deleteTask(Long id)` to delete a task.

---

#### **Ticket 5: Create the `TaskController` Class**

- **Tasks:**
  - Create a REST controller (`TaskController`) to expose task management functionality through HTTP endpoints.
  - Implement the following endpoints:
    - **GET** `/api/tasks` to retrieve all tasks.
    - **GET** `/api/tasks/{id}` to retrieve a specific task by its ID.
    - **POST** `/api/tasks` to create a new task.
    - **PUT** `/api/tasks/{id}` to update an existing task by ID:
      - Ensure that the `PUT` request body includes the updated task data.
      - Validate that the task exists before updating it.
    - **DELETE** `/api/tasks/{id}` to delete a task by ID.

- **Hints:**
  - Use `@GetMapping`, `@PostMapping`, `@PutMapping`, and `@DeleteMapping` for handling HTTP requests.

---

#### **Ticket 6: Test the API Endpoints**

- **Tasks:**
  - Use **Postman** or any API testing tool to fully test the endpoints you’ve created. Perform the following operations in sequence:

1. **Create a new task** using the `POST /api/tasks` endpoint:
   - In Postman, select the `POST` method and use the URL: `http://localhost:8080/api/tasks`.
   - In the **Body** section of Postman, choose **raw** and **JSON** format, and provide a sample JSON object like this:
     ```json
     {
       "title": "Complete project",
       "description": "Finish the task management project",
       "status": "In Progress"
     }
     ```
   - Click **Send** and ensure you get a `200 OK` status and a response body that includes the created task with an `id` field.

2. **Retrieve all tasks** using the `GET /api/tasks` endpoint:
   - In Postman, select the `GET` method and use the URL: `http://localhost:8080/api/tasks`.
   - Click **Send** and ensure you get a `200 OK` status and a list of tasks, including the one you just created.

3. **Retrieve a specific task by ID** using the `GET /api/tasks/{id}` endpoint:
   - In Postman, select the `GET` method and use the URL: `http://localhost:8080/api/tasks/{id}`, where `{id}` is the `id` of the task you created in step 1 (e.g., `http://localhost:8080/api/tasks/1`).
   - Click **Send** and ensure you get a `200 OK` status and the details of the task with the specified `id`.

4. **Update an existing task** using the `PUT /api/tasks/{id}` endpoint:
   - In Postman, select the `PUT` method and use the URL: `http://localhost:8080/api/tasks/{id}`, where `{id}` is the ID of the task you want to update (e.g., `http://localhost:8080/api/tasks/1`).
   - In the **Body** section of Postman, choose **raw** and **JSON** format, and provide a sample JSON object with updated fields:
     ```json
     {
       "title": "Complete project",
       "description": "Finish the task management project",
       "status": "Completed"
     }
     ```
   - Click **Send** and ensure you get a `200 OK` status and the updated task details in the response.

5. **Delete a task** using the `DELETE /api/tasks/{id}` endpoint:
   - In Postman, select the `DELETE` method and use the URL: `http://localhost:8080/api/tasks/{id}`, where `{id}` is the ID of the task you want to delete.
   - Click **Send** and ensure you get a `204 No Content` status, indicating the task has been successfully deleted.
   - Verify the task is deleted by sending another `GET /api/tasks` request and confirming the task no longer appears in the list.

- **Hints:**
   - For each `POST` and `PUT` request, ensure that the JSON body is correctly formatted and all necessary fields are provided (e.g., `title`, `description`, `status`).
   - After performing `DELETE`, attempt to retrieve the deleted task using `GET /api/tasks/{id}`. This should return a `404 Not Found` status, confirming the deletion.

---
