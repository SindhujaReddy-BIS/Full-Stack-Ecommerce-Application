# Full-Stack E-Commerce Application

A full-stack e-commerce web application with a React frontend and a Java Spring Boot REST API. The application is organized around customer shopping flows and role-based administration/seller operations.

## Overview

The project brings together a browser-based storefront and a RESTful backend. The frontend communicates with the backend through Axios. The backend uses Spring MVC, Spring Security, Spring Data JPA, and PostgreSQL for application data.

## Main capabilities present in the source

- User registration, sign-in, sign-out, and current-user information.
- Cookie-based JWT authentication and Spring Security authorization.
- Product browsing, category browsing, keyword search, pagination, and sorting.
- Product and category management endpoints for administrative/seller workflows.
- Shopping cart and cart-item functionality.
- Address management for checkout.
- Order placement, order history/administrative order operations, and order-status updates.
- Product image upload and image-serving configuration.
- Stripe payment-intent/client-secret backend integration.
- Admin dashboard views for products, categories, sellers, users, and orders.
- Frontend route protection and Redux Toolkit state management.
- API documentation configuration using Springdoc OpenAPI.

Feature availability can depend on database setup, credentials, user roles, and payment-provider configuration. Payment-provider credentials are not included in this repository.

## Technology stack

### Frontend
- React 19
- JavaScript (ES modules)
- Vite
- React Router
- Redux Toolkit / React Redux
- Axios
- Material UI
- Tailwind CSS
- Stripe.js / React Stripe.js

### Backend
- Java 24 (as configured in `sb-ecom/pom.xml`)
- Spring Boot 4.0.1
- Spring MVC
- Spring Security
- Spring Data JPA / Hibernate
- JWT (JJWT)
- PostgreSQL JDBC driver
- Stripe Java SDK
- Maven
- Springdoc OpenAPI

## Architecture

```text
Browser
  |
  v
React + Vite frontend (ecom-frontend)
  |
  | HTTP requests / cookies (Axios)
  v
Spring Boot REST API (sb-ecom)
  |
  +--> Controllers
  +--> Services
  +--> Repositories
  +--> JPA / Hibernate
  |
  v
PostgreSQL database

Spring Security + JWT protects authenticated and role-restricted endpoints.
Stripe integration is used by the backend payment flow.
```

## Repository structure

```text
Full-Stack-Ecommerce-Application/
├── ecom-frontend/
│   ├── public/
│   ├── src/
│   │   ├── api/                 # Axios API client
│   │   ├── components/
│   │   │   ├── admin/           # Admin dashboard and management screens
│   │   │   ├── auth/            # Login and registration
│   │   │   ├── cart/            # Cart UI
│   │   │   ├── checkout/        # Address, checkout, and payment UI
│   │   │   ├── home/            # Home page
│   │   │   ├── products/        # Product listing and filtering
│   │   │   └── shared/          # Reusable UI components
│   │   ├── hooks/               # Filtering hooks
│   │   ├── store/               # Redux actions, reducers, and store
│   │   └── utils/               # Shared utilities
│   ├── .env.example
│   └── package.json
├── sb-ecom/
│   ├── src/main/java/com/ecommerce/project/
│   │   ├── config/              # Application and API configuration
│   │   ├── controller/          # REST endpoints
│   │   ├── exceptions/          # API exception handling
│   │   ├── model/               # JPA entities
│   │   ├── payload/              # Request/response DTOs
│   │   ├── repositories/        # Spring Data repositories
│   │   ├── security/             # Security and JWT components
│   │   ├── service/              # Business logic
│   │   └── util/                 # Shared helpers
│   ├── src/main/resources/
│   │   └── application.properties
│   └── pom.xml
├── .gitignore
└── README.md
```

## Prerequisites

Install the following before running the application:

- JDK 24 (or a compatible JDK supported by the configured Spring Boot version)
- Node.js and npm
- PostgreSQL
- Git
- Stripe test credentials if you want to exercise the Stripe payment flow

## Run locally

### 1. Clone the repository

```bash
git clone https://github.com/SindhujaReddy-BIS/Full-Stack-Ecommerce-Application.git
cd Full-Stack-Ecommerce-Application
```

### 2. Create the PostgreSQL database

Create a database named `ecommerce` in PostgreSQL:

```sql
CREATE DATABASE ecommerce;
```

### 3. Configure backend environment variables

The backend reads configuration from environment variables. Set these in the terminal/session used to start Spring Boot.

**Windows PowerShell:**

```powershell
$env:DB_URL="jdbc:postgresql://localhost:5432/ecommerce"
$env:DB_USERNAME="postgres"
$env:DB_PASSWORD="your_postgres_password"
$env:JWT_SECRET="replace_with_a_long_random_secret"
$env:JWT_EXPIRATION_MS="300000000"
$env:STRIPE_SECRET_KEY="your_stripe_test_secret_key"
$env:FRONTEND_URL="http://localhost:5173/"
$env:IMAGE_BASE_URL="http://localhost:8080/images"
```

**macOS / Linux:**

```bash
export DB_URL="jdbc:postgresql://localhost:5432/ecommerce"
export DB_USERNAME="postgres"
export DB_PASSWORD="your_postgres_password"
export JWT_SECRET="replace_with_a_long_random_secret"
export JWT_EXPIRATION_MS="300000000"
export STRIPE_SECRET_KEY="your_stripe_test_secret_key"
export FRONTEND_URL="http://localhost:5173/"
export IMAGE_BASE_URL="http://localhost:8080/images"
```

Use your own strong, randomly generated JWT secret. Never commit real passwords, API keys, or signing secrets.

### 4. Start the backend

Open a terminal:

```bash
cd sb-ecom
```

On Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

On macOS / Linux:

```bash
./mvnw spring-boot:run
```

The backend is configured to use port `8080` by default (unless changed in the project configuration).

### 5. Configure and start the frontend

Open a second terminal:

```bash
cd ecom-frontend
```

Copy `.env.example` to `.env` and adjust the backend URL if needed.

```bash
npm install
npm run dev
```

Vite normally serves the frontend at `http://localhost:5173`.

### 6. Build checks

Frontend production build:

```bash
cd ecom-frontend
npm run build
```

Frontend lint:

```bash
npm run lint
```

Backend tests/build:

```bash
cd sb-ecom
./mvnw test
```

On Windows, use `.\mvnw.cmd test`.

## API overview

The backend controllers expose REST endpoints under `/api`. The following are examples confirmed in the source:

| Area | Method | Endpoint | Purpose |
|---|---|---|---|
| Authentication | POST | `/api/auth/signup` | Register a user |
| Authentication | POST | `/api/auth/signin` | Sign in |
| Authentication | POST | `/api/auth/signout` | Sign out |
| Authentication | GET | `/api/auth/user` | Get current user details |
| Products | GET | `/api/public/products` | Browse products (supports query parameters for pagination, sorting, keyword, and category) |
| Products | GET | `/api/public/products/keyword/{keyword}` | Search products by keyword |
| Categories | GET | `/api/public/categories` | Browse categories |
| Orders | POST | `/api/order/users/payments/{paymentMethod}` | Place an order |
| Payments | POST | `/api/order/stripe-client-secret` | Create a Stripe payment intent client secret |
| Orders | GET | `/api/admin/orders` | Admin order listing |
| Orders | GET | `/api/seller/orders` | Seller order listing |

For the complete endpoint definitions, inspect the controller classes or use the configured OpenAPI/Swagger UI after starting the backend. Endpoint authorization depends on the configured Spring Security rules and user role.

## Security and configuration

- Secrets are intentionally externalized to environment variables.
- `.env` files and local application configuration are excluded by `.gitignore`.
- Use Stripe test keys for local development.
- Do not use real payment credentials in screenshots, source files, Postman exports, or commits.
- Before deploying, review CORS, cookie security/SameSite settings, HTTPS, database migrations, file-upload validation/storage, and production secret management.

## Development notes

- The backend is a layered Spring application: controllers handle HTTP requests, services contain business logic, repositories access persisted data, and DTOs define API payloads.
- The frontend separates page/features into React components and uses Redux Toolkit for shared application state.
- PostgreSQL is the configured backend database in this repository.
- Uploaded product images are runtime assets; add only non-sensitive sample images that are intended for public distribution.

## Author

**Sindhuja Beduduru**

Java Full Stack Developer

- GitHub: [SindhujaReddy-BIS](https://github.com/SindhujaReddy-BIS)

---

If you find this project useful, feel free to explore the code and share feedback.
