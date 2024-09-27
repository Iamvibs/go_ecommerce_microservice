# Go eCommerce Microservice

This project is a Go-based eCommerce microservice featuring user authentication and management. It uses Docker for containerization and provides a RESTful API for user-related operations.

## Table of Contents

1. [Getting Started](#getting-started)
2. [API Endpoints](#api-endpoints)
3. [Testing with Postman](#testing-with-postman)
4. [Known Issues](#known-issues)

## Getting Started

1. Clone the repository:
   ```
   git clone https://github.com/your-username/go-ecommerce-microservice.git
   cd go-ecommerce-microservice
   ```

2. Navigate to the scripts directory:
   ```
   cd scripts
   ```

3. Run the project using Docker Compose:
   ```
   docker-compose up -d --build
   ```

   This command will build and start all the necessary containers for the project.

4. The service will be available at `http://localhost:8083`.

## API Endpoints

The following endpoints are available:

- **POST /api/v1/auth**: User authentication
- **GET /api/v1/users**: Retrieve all users
- **GET /api/v1/users/:id**: Retrieve a single user
- **POST /api/v1/users**: Create a new user
- **PUT /api/v1/users**: Update an existing user
- **DELETE /api/v1/users**: Soft delete an existing user
- **GET /ping**: Health check endpoint

## Testing with Postman

Here are the Postman calls to test the API endpoints:

1. **Create a New User**
   - Method: POST
   - URL: `http://localhost:8083/api/v1/users`
   - Body (raw JSON):
	 ```json
	 {
	   "email": "testuser@example.com",
	   "password": "testpassword"
	 }
	 ```

2. **Authenticate User**
   - Method: POST
   - URL: `http://localhost:8083/api/v1/auth`
   - Body (raw JSON):
	 ```json
	 {
	   "email": "testuser@example.com",
	   "password": "testpassword"
	 }
	 ```

3. **Get All Users**
   - Method: GET
   - URL: `http://localhost:8083/api/v1/users`

4. **Get Single User**
   - Method: GET
   - URL: `http://localhost:8083/api/v1/users/1`

5. **Update User**
   - Method: PUT
   - URL: `http://localhost:8083/api/v1/users`
   - Body (raw JSON):
	 ```json
	 {
	   "id": 1,
	   "email": "updateduser@example.com"
	 }
	 ```

6. **Delete User**
   - Method: DELETE
   - URL: `http://localhost:8083/api/v1/users/1`

7. **Ping (Health Check)**
   - Method: GET
   - URL: `http://localhost:8083/ping`

Note: The service uses session-based authentication. After successful login, Postman will automatically manage the session cookies for subsequent requests.

## Known Issues

1. The API uses session-based authentication instead of token-based (JWT) authentication.
2. Error handling for authentication failures returns 500 Internal Server Error instead of more appropriate status codes (e.g., 401 Unauthorized).
3. Some error messages may be inconsistent.
