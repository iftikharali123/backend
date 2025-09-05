# Express.js CRUD Application

A simple RESTful API built with Node.js and Express.js that demonstrates CRUD (Create, Read, Update, Delete) operations for managing users.

## Features

- ✅ **Create** - Add new users
- ✅ **Read** - Get all users or a specific user by ID
- ✅ **Update** - Modify existing user information
- ✅ **Delete** - Remove users from the system
- ✅ **Error Handling** - Comprehensive error handling and validation
- ✅ **CORS Support** - Cross-origin resource sharing enabled
- ✅ **Input Validation** - Request validation and sanitization

## Prerequisites

- Node.js (version 14 or higher)
- npm (Node Package Manager)

## Installation

1. **Clone or download this project**
   ```bash
   cd /home/iftikhar/dev
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the server**
   ```bash
   # For development (with auto-restart)
   npm run dev
   
   # For production
   npm start
   ```

4. **Server will start on** `http://localhost:3000`

## API Endpoints

### Base URL
```
http://localhost:3000/api
```

### 1. Get All Users
```http
GET /api/users
```

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "John Doe",
      "email": "john@example.com",
      "age": 30
    }
  ],
  "count": 1
}
```

### 2. Get User by ID
```http
GET /api/users/:id
```

**Example:** `GET /api/users/1`

**Response:**
```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "age": 30
  }
}
```

### 3. Create New User
```http
POST /api/users
Content-Type: application/json

{
  "name": "Jane Smith",
  "email": "jane@example.com",
  "age": 25
}
```

**Response:**
```json
{
  "success": true,
  "message": "User created successfully",
  "data": {
    "id": 4,
    "name": "Jane Smith",
    "email": "jane@example.com",
    "age": 25
  }
}
```

### 4. Update User
```http
PUT /api/users/:id
Content-Type: application/json

{
  "name": "John Updated",
  "email": "john.updated@example.com",
  "age": 31
}
```

**Example:** `PUT /api/users/1`

**Response:**
```json
{
  "success": true,
  "message": "User updated successfully",
  "data": {
    "id": 1,
    "name": "John Updated",
    "email": "john.updated@example.com",
    "age": 31
  }
}
```

### 5. Delete User
```http
DELETE /api/users/:id
```

**Example:** `DELETE /api/users/1`

**Response:**
```json
{
  "success": true,
  "message": "User deleted successfully",
  "data": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "age": 30
  }
}
```

### 6. Health Check
```http
GET /api/health
```

**Response:**
```json
{
  "success": true,
  "message": "Server is running",
  "timestamp": "2024-01-01T12:00:00.000Z"
}
```

## Testing the API

### Using cURL

1. **Get all users:**
   ```bash
   curl http://localhost:3000/api/users
   ```

2. **Get user by ID:**
   ```bash
   curl http://localhost:3000/api/users/1
   ```

3. **Create a new user:**
   ```bash
   curl -X POST http://localhost:3000/api/users \
     -H "Content-Type: application/json" \
     -d '{"name":"Alice Johnson","email":"alice@example.com","age":28}'
   ```

4. **Update a user:**
   ```bash
   curl -X PUT http://localhost:3000/api/users/1 \
     -H "Content-Type: application/json" \
     -d '{"name":"Alice Updated","email":"alice.updated@example.com","age":29}'
   ```

5. **Delete a user:**
   ```bash
   curl -X DELETE http://localhost:3000/api/users/1
   ```

### Using Postman or Thunder Client

Import the following collection or create requests manually:

- **GET** `http://localhost:3000/api/users`
- **GET** `http://localhost:3000/api/users/1`
- **POST** `http://localhost:3000/api/users` (with JSON body)
- **PUT** `http://localhost:3000/api/users/1` (with JSON body)
- **DELETE** `http://localhost:3000/api/users/1`

## Error Handling

The API includes comprehensive error handling:

- **400 Bad Request** - Missing required fields or validation errors
- **404 Not Found** - User not found
- **500 Internal Server Error** - Server-side errors

**Error Response Format:**
```json
{
  "success": false,
  "message": "Error description",
  "error": "Detailed error message"
}
```

## Data Structure

Each user object contains:
- `id` (number) - Unique identifier
- `name` (string) - User's full name
- `email` (string) - User's email address (must be unique)
- `age` (number) - User's age

## Project Structure

```
├── package.json          # Project dependencies and scripts
├── server.js             # Main server file with all CRUD operations
└── README.md             # This documentation file
```

## Dependencies

- **express** - Web framework for Node.js
- **cors** - Cross-Origin Resource Sharing middleware
- **body-parser** - Parse incoming request bodies
- **nodemon** - Development dependency for auto-restart

## Next Steps

To extend this application, you could:

1. **Add a Database** - Replace in-memory storage with MongoDB, PostgreSQL, or MySQL
2. **Add Authentication** - Implement JWT or session-based authentication
3. **Add Pagination** - Implement pagination for the GET /api/users endpoint
4. **Add Filtering/Search** - Add query parameters for filtering users
5. **Add Logging** - Implement proper logging with Winston or similar
6. **Add Tests** - Write unit and integration tests
7. **Add Validation** - Use libraries like Joi or express-validator for better validation

## License

MIT License - feel free to use this code for learning and development purposes.
