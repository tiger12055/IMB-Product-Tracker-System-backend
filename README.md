# IMB Product Tracker System

This is a Spring Boot backend project that serves as a RESTful API for a full-stack application for IMB job application.

## Project Description

This project is built using Spring Boot(version 3.05), and provides API endpoints for managing products and developers in a product management system. It supports CRUD operations and search functionality for products by Scrum Master and developer names.

## Prerequisites

- Java Development Kit (JDK) 11 or later(I am using Jave 17)
- Maven (optional, the project includes a Maven Wrapper)

## Running the Application

To run the application, follow these steps:

1. Open a terminal and navigate to the project's root directory (the same level where `pom.xml` is located).

2. Run the following command(the default port is 3000):

   For Unix-based systems:
   ```
   ./mvnw spring-boot:run
   ```
   or
   ```
   ./mvnw spring-boot:run -Dspring-boot.run.arguments="--server.port=PORT_NUMBER"
   ```

   For Windows:
   ```
   mvnw.cmd spring-boot:run
   ```
   or
   ```
   mvnw.cmd spring-boot:run -Dspring-boot.run.arguments="--server.port=PORT_NUMBER"
   ```

   If you have Maven installed on your system, you can use:
    ```
    mvn spring-boot:run
    ```
    ```
    mvn spring-boot:run -Dspring-boot.run.arguments="--server.port=PORT_NUMBER"
    ```
## Assumption I made
The new developer(only developer info this including developer name) must first inserted into developer table using (POST /api/developer) then user can add this specific new developer under products. Otherwise, user can only add existing developers to the new created product.
You can use the postman script to add developer and simple test scripts are provided under postman folder.

3. Once the application starts successfully, you should see log messages indicating that the application is running, including the port number it's listening on (3000 by default).

## Postman Scripts
The simple postman scripts for you to test backend application are provided under postman folder.

## Swagger doc
4. You can also access Swagger API by accessing (http://localhost:3000/api/api-docs) once application is running.

## Health check end point
5. You can also check health endpoint that indicating my component is healthy by accessing (http://localhost:3000/api/actuator/health)

## In memory Database
6. For this project, I am using in-memory H2 database and you can find my sql and schema file under resources/ folder. To check the database update, you can go to (http://localhost:3000/h2-console/) once application is running and you can log in to h2 database with the following info:

```
Driver Class: org.h2.Driver
JDBC URL: jdbc:h2:mem:testdb
User Name: sa
```
The database will get updated everytime when you perform addition and update operation from Angular frontend.

7. You can now access the API endpoints using an API client, such as Postman, or by connecting the backend to a frontend application.

## API Endpoints
- `GET /api/developer`: Fetch all developers
- `POST /api/developer`: Add a new developer
- `GET /api/products`: Fetch all products
- `POST /api/products`: Create a new product（my assumption: the developer must be in my database then user can add this specific developer under products otherwise user can hit developer api to add developer）
- `GET /api/products/{productNumber}`: Fetch a single product by product number
- `PUT /api/products/{productNumber}`: Update a product by product number（my assumption: the developer must be in my database then user can add this specific developer under products otherwise user can hit developer api to add developer）
- `GET /api/products/search/scrum-master?name={name}`: Search products by Scrum Master name
- `GET /api/products/search/developer?name={name}`: Search products by developer name


