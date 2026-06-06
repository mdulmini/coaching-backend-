# CoachHub — Private Coaching App (Backend)

A private coaching application REST API built with Spring Boot and JWT Authentication.

## GitHub Repositories
- Backend: https://github.com/mdulmini/coaching-backend-
- Frontend: https://github.com/mdulmini/coaching-frontend

## Tech Stack
- Java 21
- Spring Boot 3.5
- Spring Security
- JWT Authentication
- Spring Data JPA
- H2 In-Memory Database
- Lombok
- Maven

## API Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/api/auth/health` | Health check | No |
| POST | `/api/auth/register` | Register user | No |
| POST | `/api/auth/login` | Login user | No |

## Request & Response Examples

### Register
Request:
```json
POST /api/auth/register
{
  "name": "Test User",
  "email": "test@gmail.com",
  "password": "password123"
}
```

Response:
```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9...",
  "email": "test@gmail.com",
  "name": "Test User",
  "message": "Registration successful"
}
```

### Login
Request:
```json
POST /api/auth/login
{
  "email": "test@gmail.com",
  "password": "password123"
}
```

Response:
```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9...",
  "email": "test@gmail.com",
  "name": "Test User",
  "message": "Login successful"
}
```

### Error Response
```json
{
  "error": "Invalid email or password"
}
```

## Setup Instructions

### Prerequisites
- Java 21
- Maven

### Installation

Clone the repo:
```bash
git clone https://github.com/mdulmini/coaching-backend-.git
cd coaching-backend-
```

Run the application:
```bash
./mvnw spring-boot:run
```

API runs at http://localhost:8080

## Environment Variables
| Variable | Description |
|----------|-------------|
| `JWT_SECRET` | JWT signing secret key |
| `JWT_EXPIRATION` | Token expiry in ms (default 86400000) |

## Project Structure
src/main/java/com/coaching/app/
├── CoachingBackendApplication.java
├── config/
│   └── SecurityConfig.java
├── controller/
│   └── AuthController.java
├── dto/
│   ├── LoginRequest.java
│   ├── RegisterRequest.java
│   └── AuthResponse.java
├── entity/
│   └── User.java
├── repository/
│   └── UserRepository.java
├── service/
│   ├── AuthService.java
│   └── JwtService.java
└── exception/
└── GlobalExceptionHandler.java

## Security
- Passwords encrypted with BCrypt
- JWT tokens expire after 24 hours
- CORS configured for frontend
- Stateless session management

## Testing the API

Health check:
```bash
curl http://localhost:8080/api/auth/health
```

Register:
```bash
curl -X POST http://localhost:8080/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"Test","email":"test@gmail.com","password":"test123"}'
```

Login:
```bash
curl -X POST http://localhost:8080/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@gmail.com","password":"test123"}'
```
