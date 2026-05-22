# 🛒 Spring Boot eCommerce Backend Application

A professional backend eCommerce application developed using Java and Spring Boot.  
This project demonstrates real-world backend development concepts including JWT Authentication, REST APIs, Product Management, Category Management, Pagination, Sorting, File Uploads, and Role-Based Authorization.

---

# 🚀 Features

## 🔐 Authentication & Authorization
- User Registration (Sign Up)
- User Login (JWT Authentication)
- Role-Based Access (ADMIN / USER)
- Secure REST APIs
- Logout Functionality

---

## 📦 Product Management
- Add Product
- Update Product
- Delete Product
- Upload Product Images
- Get All Products
- Search Products by Keyword
- Get Products By Category
- Pagination & Sorting

---

## 📂 Category Management
- Create Category
- Update Category
- Delete Category
- View All Categories

---

## 👥 Social Media APIs
- Create Users
- Get All Users
- Get User By ID
- Delete User

---

## 🧪 Hello World APIs
- Simple GET and POST APIs for testing

---

# 🛠️ Tech Stack

## Backend
- Java
- Spring Boot
- Spring MVC
- Spring Security
- Spring Data JPA
- Hibernate
- JWT Authentication

## Database
- MySQL

## Tools
- Maven
- Postman
- REST APIs

---

# 📁 Project Structure

```bash
src
 ┣ main
 ┃ ┣ java
 ┃ ┃ ┗ com.ecommerce
 ┃ ┃    ┣ controller
 ┃ ┃    ┣ service
 ┃ ┃    ┣ repository
 ┃ ┃    ┣ entity
 ┃ ┃    ┣ dto
 ┃ ┃    ┣ security
 ┃ ┃    ┣ config
 ┃ ┃    ┗ exception
 ┃ ┗ resources
 ┃    ┣ application.properties
 ┃    ┗ static
```

---

# 🔑 Authentication APIs

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/signin` | User Login |
| POST | `/api/auth/signup` | User Registration |
| POST | `/api/auth/signout` | Logout |
| GET | `/api/auth/user` | Get Logged In User |

---

# 📂 Category APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/public/categories` | Get All Categories |
| POST | `/api/public/categories` | Create Category |
| PUT | `/api/public/categories/{id}` | Update Category |
| DELETE | `/api/admin/categories/{id}` | Delete Category |

---

# 📦 Product APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/public/products` | Get All Products |
| GET | `/api/public/products/keyword/{keyword}` | Search Products |
| GET | `/api/public/categories/{id}/products` | Products By Category |
| POST | `/api/admin/categories/{id}/product` | Add Product |
| PUT | `/api/admin/products/{id}` | Update Product |
| PUT | `/api/products/{id}/image` | Upload Product Image |
| DELETE | `/api/admin/products/{id}` | Delete Product |

---

# 👥 Social Media APIs

| Method | Endpoint | Description |
|---|---|---|
| GET | `/social/users` | Get All Users |
| GET | `/social/users/{id}` | Get User By ID |
| POST | `/social/users` | Create User |
| DELETE | `/social/users/{id}` | Delete User |

---

# 📌 Sample Product JSON

```json
{
  "productName": "Adjustable dumbbell set for home workouts",
  "description": "Premium quality adjustable dumbbells",
  "quantity": 90,
  "price": 90,
  "discount": 10
}
```

---

# 🔐 JWT Authentication

After successful login, the application returns a JWT token.

Example:

```json
{
  "token": "your-jwt-token"
}
```

Add the token in request headers:

```http
Authorization: Bearer your-jwt-token
```

---

# ⚙️ How To Run The Project

## 1️⃣ Clone Repository

```bash
git clone https://github.com/your-username/your-repository-name.git
```

---

## 2️⃣ Configure Database

Update `application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
spring.datasource.username=root
spring.datasource.password=yourpassword
```

---

## 3️⃣ Build Project

```bash
mvn clean install
```

---

## 4️⃣ Run Application

```bash
mvn spring-boot:run
```

---

# 🧪 API Testing

Use Postman Collection to test APIs.

---

# 🎯 Concepts Covered

- REST API Development
- Layered Architecture
- JWT Security
- CRUD Operations
- Pagination & Sorting
- Multipart File Upload
- Exception Handling
- DTO Mapping
- Spring Security
- Database Relationships
- Role-Based Authentication

---

# 🔮 Future Enhancements

- Shopping Cart
- Order Management
- Payment Gateway Integration
- Wishlist Feature
- Email Notifications
- Docker Deployment
- React Frontend
- Microservices Architecture

---

# 👨‍💻 Author

Developed by Sindhuja Beduduru

---

# ⭐ If you like this project

Give this repository a star ⭐ on GitHub.
