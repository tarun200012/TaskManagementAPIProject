
Swarina gupta <guptaswarina30@gmail.com>
8:30 PM (0 minutes ago)
to me

# Task Management API (Spring Boot)

 

A clean, RESTful Task Management API built with Spring Boot 3, JPA/Hibernate, Validation, H2, and comprehensive tests.

 

## Quickstart

 

```bash

# Java 17 and Maven are required

mvn spring-boot:run

# or

mvn test

```

 

H2 Console: http://localhost:8080/h2-console

 

## API Endpoints

 

- `POST /api/tasks` – Create a task

- `GET /api/tasks` – List tasks (optional `?status=PENDING|IN_PROGRESS|COMPLETED|CANCELLED`)

- `GET /api/tasks/{id}` – Get a single task

- `PUT /api/tasks/{id}` – Update a task (full update)

- `DELETE /api/tasks/{id}` – Delete a task

 

### Request/Response Example

 

**Create Task**

 

Request:

```http

POST /api/tasks

Content-Type: application/json

 

{

  "title": "Complete Spring Boot Assignment",

  "description": "Build a task management API",

  "status": "PENDING",

  "priority": "HIGH",

  "dueDate": "2025-08-14"

}

```

 

Response: `201 Created` with JSON body and `Location: /api/tasks/{id}` header.

 

**Validation Error Example**

 

Request:

```http

POST /api/tasks

Content-Type: application/json

 

{ "title": "Hi", "status": "INVALID_STATUS" }

```

 

Response: `400 Bad Request` with error messages.

 

## Sample curl

 

```bash

curl -X POST http://localhost:8080/api/tasks  -H "Content-Type: application/json"  -d '{"title":"Complete Spring Boot Assignment","description":"Build a task management API","status":"PENDING","priority":"HIGH","dueDate":"2025-08-14"}'

 

curl http://localhost:8080/api/tasks

 

curl http://localhost:8080/api/tasks/1

 

curl -X PUT http://localhost:8080/api/tasks/1  -H "Content-Type: application/json"  -d '{"title":"Updated","description":"Updated desc","status":"IN_PROGRESS","priority":"MEDIUM","dueDate":"2025-08-20"}'

 

curl -X DELETE http://localhost:8080/api/tasks/1 -i

```

 

## Tests

 

- `@WebMvcTest` controller tests with MockMvc

- `@DataJpaTest` repository tests

- `@SpringBootTest` application context test

 

Run:

```bash

mvn test

```

 

## Notes

 

- Uses DTOs to separate API contracts from entity.

- Global exception handler returns consistent error shapes.

- H2 in-memory DB for easy grading.

```
