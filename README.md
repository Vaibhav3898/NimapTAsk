# NimapTask
This project is a Spring Boot application designed to manage Categories and Products with a one-to-many relationship. It provides a REST API for performing CRUD (Create, Read, Update, Delete) operations on Categories and Products. The project also includes server-side pagination and relational data fetching.

How did you run the code? Ensure Java and Maven are Installed: Access the Application: The application should be running on http://localhost:3306. You can test the API using tools like Postman or cURL. Pagination verified using the page and size query parameters.

Features CRUD Operations: Categories: Create, Read, Update, Delete. Products: Create, Read, Update, Delete. Pagination: Server-side pagination for fetching records. Relational Mapping: One-to-Many relationship between Categories and Products. Annotation-Based Configuration: Uses annotations instead of XML configuration. Database Integration: Configured with MySQL using JPA and Hibernate. Technologies Used Backend: Spring Boot, Spring Data JPA, Hibernate Database: MySQL Language: Java Build Tool: Maven IDE: Eclipse Git Integration: EGit Plugin for Eclipse API Endpoints Category APIs HTTP Method Endpoint Description GET /api/categories?page={page} Fetch all categories with pagination. POST /api/categories Create a new category. GET /api/categories/{id} Fetch a category by ID. PUT /api/categories/{id} Update a category by ID. DELETE /api/categories/{id} Delete a category by ID. Product APIs HTTP Method Endpoint Description GET /api/products?page={page} Fetch all products with pagination. POST /api/products Create a new product. GET /api/products/{id} Fetch a product by ID. PUT /api/products/{id} Update a product by ID. DELETE /api/products/{id} Delete a product by ID. Project Structure bash Copy code src/main/java/com/example/demo ├── controller # REST Controllers for Category and Product APIs ├── model # Entity classes (Category, Product) ├── repository # Spring Data JPA Repositories ├── service # Service classes for business logic ├── NimapTaskApplication.java # Main application entry point Database Configuration Configure the MySQL database in the application.properties file:

properties Copy code spring.datasource.url=jdbc:mysql://localhost:3306/category_product_db spring.datasource.username=root spring.datasource.password=root spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver spring.jpa.hibernate.ddl-auto=update spring.jpa.show-sql=true spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect SQL Script for Table Creation sql Copy code CREATE DATABASE category_product_db;

CREATE TABLE categories ( id BIGINT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255) NOT NULL, description TEXT );

CREATE TABLE products ( id BIGINT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255) NOT NULL, description TEXT, price DECIMAL(10,2), category_id BIGINT, CONSTRAINT FK_category FOREIGN KEY (category_id) REFERENCES categories(id) ON DELETE CASCADE ); Setup Instructions Clone the Repository:

bash Copy code git clone https://github.com//.git cd Open in Eclipse:

Open Eclipse. Go to File > Import > Existing Maven Projects. Select the cloned repository and click Finish. Run the Application:

Right-click on NimapTaskApplication.java and select Run As > Java Application. Test APIs:

Use tools like Postman or Curl to test the APIs. Usage Example Create a new category:

json Copy code POST /api/categories { "name": "Electronics", "description": "Electronic items" } Create a product under the category:

json Copy code POST /api/products { "name": "Laptop", "description": "Gaming Laptop", "price": 75000, "category": { "id": 1 } } Fetch all products with pagination:

bash Copy code GET /api/products?page=0 Contributing Feel free to fork this repository and submit pull requests for improvements or bug fixes.

License This project is licensed under the MIT License.

Contact For queries or suggestions, feel free to reach out:

Email: shindevaibhav3898@gmail.com GitHub: Your GitHub Profile
