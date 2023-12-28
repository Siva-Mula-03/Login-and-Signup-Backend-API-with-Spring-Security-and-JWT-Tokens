## Problem Statement
## Backend Implementation of Secure Login and Signup REST API with JWT Tokens
Overview:
Develop a backend application using Java and Spring Boot that provides RESTful API endpoints for user registration (signup) and authentication (login). Ensure the security of the endpoints using JWT (JSON Web Tokens). Data persistence should be handled using the H2 database.

## Installation and Setup

```
### Prerequisites
- Java Development Kit (JDK) 8 or later
- Maven
- Postman (for testing the API)
```

### 1. Clone the Repository

```
git clone https://github.com/Siva-Mula-03/Login-and-Signup-Backend-API-with-Spring-Security-and-JWT-Tokens.git
```

### 2. Go the Project

```
cd Login-and-Signup-Backend-API-with-Spring-Security-and-JWT-Tokens

```

### 3. Run the Application
- For GitBash
```
./mvnw spring-boot:run

```
**The application will start running on [http://localhost:8081](http://localhost:8081)**

### **API Endpoints**

### User Signup

- Method: POST
- Path: `http://localhost:8081/app/signup`
- Description: Register a new user.
- Request Body: User data in the JSON format (e.g., name, email, password).

```

{
  "fullName": "SivaMula",
  "password": "Springbootuser@123",
  "email": "abcd@gmail.com"
}
```

- Response:

```
{
    "id": 1,
    "fullName": "SivaMula",
    "password": "$2a$10$A3QI.WarkpLH1wGvBaizduVlByAzuWAmOTjigjBCMp490uZqLEXhO",
    "email": "abcd@gmail.com",
    "role": "ROLE_USER"
}
```

### User Login

- Method: GET
- Path: `http://localhost:8081/signIn`
- Description: Authenticate a user and retrieve their details.
- Authentication: Basic Authentication (Username and Password)
    - Username: [springboot@gmail.com](mailto:springboot@gmail.com)
    - Password: Springuser@99

Basic Auth-->username:email,value:Base64URL_encoded_password  

For Base64URL_encoded_password visit -> https://mixedanalytics.com/tools/basic-authentication-generator/
- Response:

```
{
    "id": 1,
    "fullName": "Siva Mula",
    "password": "$2a$10$8nvvF1K0c6FwZNm1RwnDHevJwpkqT2LyTSP1VbPXUjsFnA/KAY3dy",
    "email": "springboot@gmail.com",
    "role": "ROLE_USER"
}

```

### Welcome Endpoint (Requires Authentication)

- Method: GET
- Path: `http://localhost:8081/logged-in/user`
- Description: A protected endpoint that requires authentication to access.
- Authentication: Bearer Token
- Request Header:
    - Authorization: Bearer <token>
- Response: A welcome message string.
- Example:
    - Bearer Token: eyJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJTaGltYmh1Iiwic3ViIjoiSldUIFRva2VuIiwidXNlcm5hbWUiOiJzcHJpbmdib290QGdtYWlsLmNvbSIsInJvbGUiOiJST0xFX1VTRVIiLCJpYXQiOjE3MDM3NjQzMTgsImV4cCI6MTcwMzc5NDMxOH0.H239t-JZtNTNkirTnsmknSBNS_lW-Xbqf7AVHJ_w9ng
    - Response: Welcome to SivaMula's Website  : Siva Mula

![Bearerauthresponse](https://github.com/Siva-Mula-03/Login-and-Signup-Backend-API-with-Spring-Security-and-JWT-Tokens/assets/111627965/37ffecbd-4dcb-48d7-b61e-50cfcda3f1c2)

### Tech Stack

- Java
- Spring Boot
- H2 Database
- Spring Security
- JWT Token
- Lombok
- Maven

### Validation Rules

The following validation rules are applied to the user entity:

- Full Name:
    - Minimum length: 3 characters
    - Maximum length: 20 characters
- Password:
    - At least 8 characters
    - Contains at least one digit
    - Contains at least one lowercase letter
    - Contains at least one uppercase letter
    - Contains at least one special character
- Email:
    - Valid email format

### Development

The project can be imported and run using an IDE like Eclipse.

### Test API

You can use Postman to test the API endpoints.

## H2 Database Configuration

The project uses the H2 in-memory database by default.

The application is configured to use the H2 database. The configuration can be found in the `application.properties` file:

```
# Server Port Configuration
server.port=8081

# H2 Database Configuration
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=
spring.datasource.password=
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

```

 
