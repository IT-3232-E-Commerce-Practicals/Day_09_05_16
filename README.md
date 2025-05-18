# Employee Management System

## Introduction
This is a Spring Boot application designed to manage departments and employees in an organization. It provides RESTful APIs to perform CRUD (Create, Read, Update, Delete) operations on department and employee data. Currently, the main focus is on department management. Employee functionality is referenced but not fully implemented.

---
 
## Project Structure

### 1. Model Layer
- **Department**
  - Represents a department with the following attributes:
    - `id`: Unique identifier
    - `name`: Department name
    - `establishedDate`: Date the department was created
    - `employees`: List of associated employees (not detailed in code)

- **Employee**
  - Placeholder entity for employee details (not included in the provided code).

### 2. Repository Layer
- **DepartmentRepo**
  - JPA repository interface for the `Department` entity.
  - Extends `JpaRepository<Department, Long>` to support built-in CRUD operations.

### 3. Service Layer
- **DepartmentService**
  - Contains the business logic for handling department-related operations:
    - Get all departments
    - Get a department by ID

### 4. Controller Layer
- **DepartmentController**
  - REST controller to manage department API endpoints:
    - `GET /dept` - Retrieve all departments
    - `GET /dept/{id}` - Retrieve a department by ID
    - *(Commented-out methods for POST, PUT, DELETE exist but are not active)*

---
 
 ## Database Configuration

The application connects to a MySQL database using the following properties:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/employee
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
```
---

## How to Run

1. Ensure you have Java 11 or higher installed
2. Install MySQL and create a database named 'employee'
3. Configure the database connection in application.properties
4. Build the project using Maven: `mvn clean install`
5. Run the application: `mvn spring-boot:run`

## API Endpoints

### Department Endpoints

| Method | Endpoint     | Description                  | Response                    | Status Code |
|--------|--------------|------------------------------|-----------------------------|-------------|
| GET    | `/dept`      | Get a list of all departments | Array of Department objects | 200 OK      |
| GET    | `/dept/{id}` | Get details of a department by ID | Single Department object     | 200 OK / 404 Not Found |

 
 ![Screenshot (58)](https://github.com/user-attachments/assets/49b48ae7-339c-499e-aa31-628e9db2099a)
![Screenshot (59)](https://github.com/user-attachments/assets/da19faf4-c8b6-44ab-854c-cf25f37f55ea)
![Screenshot (60)](https://github.com/user-attachments/assets/68fb95ed-e08e-41bc-96fa-72e82ae59d11)



### Commented Department Endpoints
These endpoints exist in the code but are currently commented out, and can be implemented later:

- **GET /dept**  
  - Description: Fetches the complete list of departments  
  - Response: Returns a JSON array of Department objects  
  - Implementation Note: This endpoint saves a department to the database via the repository (to be activated)  

 ![Screenshot (63)](https://github.com/user-attachments/assets/5151a3cd-1d04-42a0-ad96-2ad39ed99d57)

- **GET /dept/{id}**  
  - Description: Fetch a department by its ID  
  - Path Parameter: `id` (ID of the department)  
  - Response: Returns the Department object  
  - Implementation Detail: Saves the department to the database using the repository (currently commented out)  
  
  ![Screenshot (65)](https://github.com/user-attachments/assets/e4bc75a6-7c8e-46fc-a82b-b9b3f94e77fa)

- **POST /dept**  
  - Description: Create a new department  
  - Request Body: Department object in JSON format  
  - Response: Confirmation message "New Department added"  
  - Implementation Detail: Saves the new department to the database via repository  
  
  ![Screenshot (61)](https://github.com/user-attachments/assets/099822f7-6ecf-4212-8814-1979bfe6b7dd)

- **PUT /dept/{id}**  
  - Description: Update details of an existing department  
  - Path Parameter: `id` (ID of the department to update)  
  - Request Body: Updated Department object  
  - Response: Success message "The Department Updated" or error message "Couldn't find the department" if not found  
  - Implementation Detail: Verifies existence before updating and saving the department  
  
  ![Screenshot (62)](https://github.com/user-attachments/assets/82f0c29d-b653-43a1-a004-385d9a6409ff)

- **DELETE /dept/{id}**  
  - Description: Delete a department by ID  
  - Path Parameter: `id` (ID of the department to delete)  
  - Response: Success message "The Department Deleted" or error message "Couldn't find the department" if not found  
  - Implementation Detail: Checks if the department exists and deletes it by ID

 
  ![Screenshot (66)](https://github.com/user-attachments/assets/d42d0003-9e02-42cb-bbce-6ca3296a16b1)


## Relationship Between Entities
- Each Department can include multiple Employees, defining a one-to-many association.
- This link is established through the `department` attribute within the Employee class.

## Additional Information
- The DepartmentController is designed with two implementation options:
  1. The active approach leverages a service layer (`DepartmentService`) to handle logic.
  2. An alternative, currently commented out, interacts directly with the repository for CRUD operations.
- The alternative version covers all main CRUD functions: fetching, creating, updating, and deleting departments.
- To activate the direct repository approach, simply uncomment the related code block in the controller and disable the service-based code.
- It is advisable to add comprehensive error handling and input validation before deploying in a real-world environment.
- Planned improvements include completing the Employee model and creating corresponding endpoints for employee management.


## Dependencies
- Spring Boot
- Spring Data JPA
- MySQL Connector
- Jakarta Persistence API

