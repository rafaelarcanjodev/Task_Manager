# 📝 Task Manager API | iPaaS Technical Challenge

![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![JUnit5](https://img.shields.io/badge/JUnit%205-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Swagger](https://img.shields.io/badge/-Swagger-%23C1E814?style=for-the-badge&logo=swagger&logoColor=black)

This repository contains a **RESTful API** designed for managing complex task and subtask workflows. Developed as a **Technical Challenge** for the **Mid-Level Java Backend Developer** role at iPaaS.

---

## 🛠️ Tech Stack

* **Backend:** Java 17+, Spring Boot 3.x
* **Persistence:** Spring Data JPA (Hibernate)
* **Database:** H2 (In-memory for development/testing)
* **Documentation:** Springdoc OpenAPI (Swagger UI)
* **Testing:** JUnit 5, Mockito, Maven Surefire
* **DevOps:** Docker, Docker Compose
* **Other:** Lombok, Jakarta Validation, Logback (SLF4J)

---

## 📂 Project Architecture

The project implements a **Layered Architecture** to ensure separation of concerns and maintainability:

```text
src/main/java/com/ipaas/taskManager  
├── controller       # REST Controllers (API Endpoints)  
├── configuration    # Config classes (Swagger, DB Seeding)  
├── dto              # Request/Response Data Transfer Objects  
├── exception        # Custom Exception Handlers  
├── model            # JPA Entities (User, Task, Subtask)  
├── repository       # Spring Data JPA Repositories  
├── service          # Business Logic & Validation Rules
└── TaskManagerApplication.java # Main Application Entry
````

---

## 🚀 Getting Started

You can run the application in two ways:

---

## 1. Using Maven (Native)

Ensure you have **Java 17+** and **Maven** installed.

### Clone the repository

```bash
git clone https://github.com/rafarcanjoatos/Task_Manager
cd taskManager
```

### Build the project

```bash
./mvnw clean install
```

### Run the application

```bash
./mvnw spring-boot:run
```

*The API will be available at:*
**[http://localhost:8080](http://localhost:8080)**

---

## 2. Using Docker & Docker Compose (Recommended)

The easiest way to set up the application and its dependencies.

### Clone the repository

```bash
git clone https://github.com/rafarcanjoatos/Task_Manager
cd taskManager
```

### Build and run with Docker Compose

```bash
docker-compose up --build
```

*The application will be available at:*
**[http://localhost:8080](http://localhost:8080)**

---

# 📖 API Endpoints & Documentation

Once the application is running, you can access:

## H2 Database Console

To inspect the in-memory database.

* **URL:** [http://localhost:8080/h2-console](http://localhost:8080/h2-console)

### Credentials (default from `application.properties`)

* **JDBC URL:** `jdbc:h2:file:./data/task_manager_db`
* **User Name:** `sa`
* **Password:** *(empty)*

---

## Swagger UI (Interactive API Docs)

Used to explore and test endpoints.

* **URL:** [http://localhost:8080/swagger-ui.html](http://localhost:8080/swagger-ui.html)

---

# 📌 Endpoint Summary

## Users

* **GET /usuarios**
  *List all registered users.*

* **GET /usuarios/{id}**
  *Find a user by ID.*

* **POST /usuarios**
  *Create a new user.*

* **PATCH /usuarios/{id}**
  *Update an existing user's data.*

* **DELETE /usuarios/{id}**
  *Remove a user.*

---

## Tasks

* **GET /tarefas**
  *List tasks (with status filtering options).*

* **GET /tarefas/{id}**
  *Find a specific task by ID.*

* **POST /tarefas**
  *Create a new task for a user.*

* **PATCH /tarefas/{id}**
  *Update task title and description.*

* **PATCH /tarefas/{id}/status**
  *Update task status.*

**Note:**
*A task can only be set to **COMPLETED** if all its subtasks are also **COMPLETED**.*

* **DELETE /tarefas/{id}**
  *Remove a task (only if no subtasks are attached).*

---

## Subtasks

* **GET /tarefas/{tarefaId}/subtarefas**
  *List all subtasks for a specific task.*

* **POST /tarefas/{tarefaId}/subtarefas**
  *Create a new subtask.*

* **GET /tarefas/{tarefaId}/subtarefas/{subtarefaId}**
  *Find a subtask by ID.*

* **PATCH /tarefas/{tarefaId}/subtarefas/{subtarefaId}**
  *Update subtask title and description.*

* **PATCH /tarefas/{tarefaId}/subtarefas/{subtarefaId}/status**
  *Update subtask status.*

* **DELETE /subtarefas/{id}**
  *Remove a subtask.*
