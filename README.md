# User Management Application

## Overview

This is a User Management application built using Spring Boot. It provides a RESTful API for managing users, including operations such as creating, reading, updating, and deleting users.

## Features

- Create a new user
- Retrieve all users
- Retrieve a specific user by ID
- Update a user's information
- Delete a user

## Technologies Used

- Spring Boot
- Spring Data JPA
- MySQL
- Maven

## Setup and Running the Application

### Prerequisites

- Java 17 or higher
- Maven
- MySQL

### Steps

1. **Clone the repository:**
   ```bash
   git clone <your-repository-url>
   cd <your-repository-directory>
   ```

2. **Configure the database:**
   Update the `application.properties` file in `src/main/resources` with your MySQL database configuration.
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/user_management
   spring.datasource.username=root
   spring.datasource.password=your_password
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
   ```

3. **Build the application:**
   ```bash
   mvn clean install
   ```

4. **Run the application:**
   ```bash
   mvn spring-boot:run
   ```

5. **Access the API:**
   You can access the API at `http://localhost:8080/api/users`.

## API Endpoints

### Create a new user

- **URL:** `/api/users`
- **Method:** `POST`
- **Request Body:**
  ```json
  {
      "username": "testuser",
      "email": "testuser@example.com",
      "password": "password123"
  }
  ```

### Retrieve all users

- **URL:** `/api/users`
- **Method:** `GET`

### Retrieve a specific user by ID

- **URL:** `/api/users/{id}`
- **Method:** `GET`

### Update a user

- **URL:** `/api/users/{id}`
- **Method:** `PUT`
- **Request Body:**
  ```json
  {
      "username": "updateduser",
      "email": "updateduser@example.com",
      "password": "newpassword123"
  }
  ```

### Delete a user

- **URL:** `/api/users/{id}`
- **Method:** `DELETE`

## Design Patterns Used

### Service Layer Pattern

The service layer pattern is used to define the application's business logic. The `UserService` interface defines the operations that can be performed on the `User` entity, and the `UserServiceImpl` class provides the implementation of these operations.

- **Advantages:**
  - Separation of concerns: The business logic is separated from the presentation and data access layers.
  - Easier testing: Business logic can be tested independently of other layers.

### Repository Pattern

The repository pattern is used to abstract the data access layer. The `UserRepository` interface extends `JpaRepository`, providing a set of CRUD operations for the `User` entity.

- **Advantages:**
  - Simplifies data access: Provides a clean and simple API for data access.
  - Decouples business logic from data access: Business logic does not need to know the details of data access.

### Annotations Used

- **@RestController:** Marks the class as a controller where every method returns a domain object instead of a view.
- **@RequestMapping:** Maps web requests to specific handler classes and/or handler methods.
- **@PostMapping, @GetMapping, @PutMapping, @DeleteMapping:** Specialized versions of @RequestMapping for specific HTTP methods.
- **@Autowired:** Used for dependency injection.
- **@Entity:** Specifies that the class is an entity and is mapped to a database table.
- **@Id:** Specifies the primary key of an entity.
- **@GeneratedValue:** Provides the specification of generation strategies for the values of primary keys.
