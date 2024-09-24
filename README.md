# Task_management_system


---

### **Ticket Breakdown for Task Management System**

---

#### **Ticket 1: Set Up Spring Boot Project**

- **Tasks:**
  - Set up a Spring Boot project with the necessary dependencies (Spring Web, Spring Data JPA, MySQL Driver, and Lombok).
 ---

#### **Ticket 2: Create the `Task` Entity**

- **Tasks:**
  - Create a `Task` entity with the following fields:
    - `id` (Primary key, auto-incremented)
    - `title` (Task title)
    - `description` (Task description)
    - `status` (Task status)

---

#### **Ticket 3: Create the `TaskRepository` Interface**

- **Tasks:**
  - Create a repository interface that extends `JpaRepository<Task, Long>` to provide CRUD operations for the `Task` entity.

---

#### **Ticket 4: Create the `TaskService` Class**

- **Tasks:**
  - Implement the following methods in the service layer:
    - `getAllTasks()` to retrieve all tasks.
    - `getTaskById(Long id)` to retrieve a specific task by its ID.
    - `createTask(Task task)` to create a new task.
    - `updateTask(Long id, Task updatedTask)` to update an existing task.
    - `deleteTask(Long id)` to delete a task by its ID.

---

#### **Ticket 5: Create the `TaskController` Class**

- **Tasks:**
  - Add endpoints for CRUD operations:
    - **GET** `/api/tasks` to retrieve all tasks.
    - **GET** `/api/tasks/{id}` to retrieve a specific task.
    - **POST** `/api/tasks` to create a new task.
    - **PUT** `/api/tasks/{id}` to update an existing task.
    - **DELETE** `/api/tasks/{id}` to delete a task by its ID.

---

