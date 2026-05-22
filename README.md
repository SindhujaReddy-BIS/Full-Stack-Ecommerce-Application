Java Spring Boot eCommerce Application

A professional full-stack eCommerce backend application built using Spring Boot and REST APIs.
This project demonstrates real-world backend development concepts such as authentication, authorization, product management, category management, image upload, pagination, sorting, filtering, and secure API development.

Features
Authentication & Authorization
User Registration (Sign Up)
User Login (JWT Authentication)
Role-Based Access Control (ADMIN / USER)
Secure APIs using JWT Token
Logout Functionality
Category Management
Create Category
Update Category
Delete Category
Get All Categories
Pagination & Sorting Support
Product Management
Add Product
Update Product
Delete Product
Upload Product Images
Search Products by Keyword
Get Products by Category
Product Pagination & Sorting
Social Media APIs
Create Users
Get All Users
Get User By ID
Delete User
Hello World APIs
Simple GET and POST APIs for testing
Tech Stack
Backend
Java
Spring Boot
Spring MVC
Spring Security
JWT Authentication
Spring Data JPA
Hibernate
Database
MySQL
Tools & Utilities
Postman
Maven
REST APIs
Multipart File Upload
Project Structure
src
 ┣ main
 ┃ ┣ java
 ┃ ┃ ┗ com.ecommerce
 ┃ ┃    ┣ controller
 ┃ ┃    ┣ service
 ┃ ┃    ┣ repository
 ┃ ┃    ┣ entity
 ┃ ┃    ┣ dto
 ┃ ┃    ┣ config
 ┃ ┃    ┣ security
 ┃ ┃    ┗ exception
 ┃ ┗ resources
 ┃    ┣ application.properties
 ┃    ┗ static
API Endpoints
Authentication APIs
Method	Endpoint	Description
POST	/api/auth/signin	User Login
POST	/api/auth/signup	User Registration
POST	/api/auth/signout	Logout
GET	/api/auth/user	Get User Details
Category APIs
Method	Endpoint	Description
GET	/api/public/categories	Get All Categories
POST	/api/public/categories	Create Category
PUT	/api/public/categories/{id}	Update Category
DELETE	/api/admin/categories/{id}	Delete Category
Product APIs
Method	Endpoint	Description
GET	/api/public/products	Get All Products
GET	/api/public/products/keyword/{keyword}	Search Products
GET	/api/public/categories/{id}/products	Products By Category
POST	/api/admin/categories/{id}/product	Add Product
PUT	/api/admin/products/{id}	Update Product
PUT	/api/products/{id}/image	Upload Product Image
DELETE	/api/admin/products/{id}	Delete Product
Sample Product JSON
{
  "productName": "Adjustable dumbbell set for home workouts",
  "description": "Premium quality adjustable dumbbells",
  "quantity": 90,
  "price": 90,
  "discount": 10
}
JWT Authentication

After successful login, the API returns a JWT token.

Example:

{
  "token": "your-jwt-token"
}

Use this token in headers:

Authorization: Bearer your-jwt-token
How To Run The Project
1. Clone Repository
git clone <repository-url>
2. Configure Database

Update application.properties

spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
spring.datasource.username=root
spring.datasource.password=yourpassword
3. Run Application
mvn spring-boot:run
4. Test APIs

Use Postman collection to test all APIs.

Key Concepts Covered
REST API Development
Layered Architecture
JWT Security
CRUD Operations
Pagination & Sorting
File Upload
Exception Handling
DTO Mapping
Spring Security
Database Relationships
Role-Based Authentication
Future Enhancements
Shopping Cart
Order Management
Payment Gateway Integration
Wishlist Feature
Email Notifications
Docker Deployment
React Frontend
Microservices Architecture
