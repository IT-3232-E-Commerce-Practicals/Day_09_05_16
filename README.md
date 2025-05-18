# Employee Management System

## Overview
This is a Spring Boot application for managing departments and employees in an organization. The application provides RESTful APIs to perform CRUD (Create, Read, Update, Delete) operations on department and employee data.

## Project Structure

### Models
- **Department**: Entity class representing a department with attributes such as id, name, established date, and a list of employees.
- **Employee**: Entity class representing employees (referenced in Department but not shown in the provided code).

### Repository
- **DepartmentRepo**: JPA repository interface for Department entity that extends JpaRepository to provide CRUD operations.

### Service
- **DepartmentService**: Service class that handles business logic for department operations.
  - Gets all departments
  - Gets a department by ID

### Controller
- **DepartmentController**: REST controller that handles HTTP requests for department operations.
  - GET /dept - Retrieves all departments
  - GET /dept/{id} - Retrieves a specific department by ID
  - (Commented out) POST, PUT, DELETE operations for departments

## Database Configuration
The application uses MySQL database with the following configuration:
- Database URL: jdbc:mysql://localhost:3306/employee
- Username: root
- Password: (empty)
- Hibernate DDL Auto: update (creates/updates tables automatically)

## How to Run
1. Ensure you have Java 11 or higher installed
2. Install MySQL and create a database named 'employee'
3. Configure the database connection in application.properties
4. Build the project using Maven: `mvn clean install`
5. Run the application: `mvn spring-boot:run`

## API Endpoints

### Department Endpoints
- **GET /dept**: Retrieves all departments
  - Response: List of Department objects
  - Status codes: 200 OK
 
 ![Screenshot (58)](https://github.com/user-attachments/assets/49b48ae7-339c-499e-aa31-628e9db2099a)



- **GET /dept/{id}**: Retrieves a specific department by ID
  - Path variable: id (Department ID)
  - Response: Department object
  - Status codes: 200 OK (if found), 404 NOT_FOUND (if not found)

 
![Screenshot (59)](https://github.com/user-attachments/assets/da19faf4-c8b6-44ab-854c-cf25f37f55ea)
![Screenshot (60)](https://github.com/user-attachments/assets/68fb95ed-e08e-41bc-96fa-72e82ae59d11)



### Commented Department Endpoints (Ready for Implementation)
The following endpoints are commented out in the code but ready for implementation:
- **GET /dept**: Retrieves all departments
  - Response: List of Department objects
  - Implementation: Saves the department to the database using repository
 ![Screenshot (63)](https://github.com/user-attachments/assets/5151a3cd-1d04-42a0-ad96-2ad39ed99d57)





- **GET /dept/{id}**: Retrieves a specific department by ID
  - Path variable: id (Department ID)
  - Response: Department object
  - Implementation: Saves the department to the database using repository
 
 ![Screenshot (65)](https://github.com/user-attachments/assets/e4bc75a6-7c8e-46fc-a82b-b9b3f94e77fa)

- **POST /dept**: Creates a new department
  - Request body: Department object
  - Response: String message "New Department added"
  - Implementation: Saves the department to the database using repository
 ![Screenshot (61)](https://github.com/user-attachments/assets/099822f7-6ecf-4212-8814-1979bfe6b7dd)

  

- **PUT /dept/{id}**: Updates an existing department
  - Path variable: id (Department ID)
  - Request body: Updated Department object
  - Response: String message "The Department Updated" if successful, "Couldn't find the department" if not found
  - Implementation: Checks if department exists, then saves the updated department
 
   ![Screenshot (62)](https://github.com/user-attachments/assets/82f0c29d-b653-43a1-a004-385d9a6409ff)


- **DELETE /dept/{id}**: Deletes a department
  - Path variable: id (Department ID)
  - Response: String message "The Department Deleted" if successful, "Couldn't find the department" if not found
  - Implementation: Checks if department exists, then deletes the department by ID
 
  ![Screenshot (66)](https://github.com/user-attachments/assets/d42d0003-9e02-42cb-bbce-6ca3296a16b1)


## Entity Relationships
- A Department has many Employees (One-to-Many relationship)
- The relationship is mapped by the 'department' field in the Employee entity

## Notes
- The Department Controller includes two implementation approaches:
  1. Current active implementation using a service layer (DepartmentService)
  2. Commented out direct repository implementation that can be uncommented for simpler usage
- The commented implementation provides full CRUD operations (GET, POST, PUT, DELETE)
- To use the commented implementation, uncomment the code in DepartmentController and comment out the current service-based implementation
- Consider implementing proper exception handling and validation for production use
- Future development could include implementing the Employee entity and related endpoints

## Dependencies
- Spring Boot
- Spring Data JPA
- MySQL Connector
- Jakarta Persistence API

