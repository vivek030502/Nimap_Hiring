# Nimap_Hiring - Category-Product Management System

This project is a RESTful web service built using **Spring Boot**, **JPA**, **Hibernate**, and **MySQL**. It provides CRUD operations for managing **Categories** and **Products**, along with server-side pagination. Categories and Products have a one-to-many relationship, with one category having multiple products.

## Features

- **Category Management**: Create, Read, Update, Delete (CRUD) operations.
- **Product Management**: Create, Read, Update, Delete (CRUD) operations.
- **One-to-Many Relationship**: Categories can have multiple products.
- **Server-Side Pagination**: Efficiently fetch paginated data from the server.
- **REST API**: The project exposes REST endpoints to perform operations.

## Technologies Used

- **Spring Boot**: Framework for building the application.
- **Spring Data JPA**: For interacting with the database.
- **Hibernate**: ORM tool for managing database entities.
- **MySQL**: Relational database for storing data.
- **Maven**: Project management and dependency management.
- **Java 17**: Programming language used for development.

## Prerequisites

- JDK 17 or higher.
- Maven 3.8.x or higher.
- MySQL 8.0 or higher.
- IDE such as IntelliJ IDEA or Eclipse.
- Postman (optional, for API testing).

## Database Configuration

The project uses MySQL as the database. Before running the application, configure the database connection in `application.properties`:

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password

# Hibernate Configuration
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
```

Replace `your_database_name`, `your_username`, and `your_password` with your actual MySQL database details.

## Running the Application

1. Clone the repository or download the source code.
   ```bash
   git clone https://github.com/yourusername/category-product-management.git
   ```
2. Configure the MySQL database and update the `application.properties` file as mentioned in the **Database Configuration** section.
3. Run the application using Maven.
   ```bash
   mvn spring-boot:run
   ```
4. The application will start at `http://localhost:8080`.

## REST API Endpoints

### Category APIs

1. **GET All Categories with Pagination:**
   ```
   GET /api/categories?page={page}&size={size}
   ```
   Example: `http://localhost:8080/api/categories?page=0&size=10`

2. **POST Create a New Category:**
   ```
   POST /api/categories
   Body (JSON):
   {
     "name": "Electronics"
   }
   ```

3. **GET Category by ID:**
   ```
   GET /api/categories/{id}
   Example: http://localhost:8080/api/categories/1
   ```

4. **PUT Update a Category by ID:**
   ```
   PUT /api/categories/{id}
   Body (JSON):
   {
     "name": "Updated Category Name"
   }
   ```

5. **DELETE Delete a Category by ID:**
   ```
   DELETE /api/categories/{id}
   Example: http://localhost:8080/api/categories/1
   ```

### Product APIs

1. **GET All Products with Pagination:**
   ```
   GET /api/products?page={page}&size={size}
   ```
   Example: `http://localhost:8080/api/products?page=0&size=10`

2. **POST Create a New Product:**
   ```
   POST /api/products
   Body (JSON):
   {
     "name": "Laptop",
     "price": 1000,
     "categoryId": 1
   }
   ```

3. **GET Product by ID:**
   ```
   GET /api/products/{id}
   Example: http://localhost:8080/api/products/1
   ```

4. **PUT Update a Product by ID:**
   ```
   PUT /api/products/{id}
   Body (JSON):
   {
     "name": "Updated Product Name",
     "price": 1200
   }
   ```

5. **DELETE Delete a Product by ID:**
   ```
   DELETE /api/products/{id}
   Example: http://localhost:8080/api/products/1
   ```

## One-to-Many Relationship (Category-Products)

- Each **Category** can have multiple **Products**.
- When fetching a product by its ID, the corresponding category details will also be included.

## Pagination

- Server-side pagination is implemented using `Pageable` and `PageRequest` in Spring Data JPA.
- You can pass `page` and `size` parameters in the API to fetch paginated data.

## Project Structure

```
src
├── main
│   ├── java
│   │   └── com.example.categoryproductmanagement
│   │       ├── controller
│   │       │   ├── CategoryController.java
│   │       │   ├── ProductController.java
│   │       ├── entity
│   │       │   ├── Category.java
│   │       │   ├── Product.java
│   │       ├── repository
│   │       │   ├── CategoryRepository.java
│   │       │   ├── ProductRepository.java
│   │       ├── service
│   │       │   ├── CategoryService.java
│   │       │   ├── ProductService.java
│   ├── resources
│   │   ├── application.properties
└─── pom.xml
```
## ER - Diagram


---
## Future Enhancements

- Implement search and filtering functionalities for products and categories.
- Add authentication and authorization using JWT.
- Improve validation for category and product creation.

## License

This project is open-source and free to use.
