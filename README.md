
# Bookstore API

A RESTful API for managing books in a bookstore. This project provides CRUD operations for books and includes authentication and role-based access control.

## Features

- **User Authentication**: Register and login with JWT-based authentication.
- **Role-Based Access Control**:
  - **Admin**: Can create, update, and delete books.
  - **User**: Can view the list of books.
- **CRUD Operations for Books**:
  - Add new books (Admin only).
  - Update book details (Admin only).
  - Delete books (Admin only).
  - Retrieve all books (All users).

## Getting Started

Follow these steps to set up and run the project locally.

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or higher)
- [MongoDB](https://www.mongodb.com/) (Local or Atlas Cloud)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/bienherasme/Bookstore-API.git
   cd bookstore-api
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the project root and configure the following variables:
   ```env
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   PORT=5000
   ```

4. Start the server:
   ```bash
   npx nodemon src/app.js
   ```

5. Use Postman or any REST client to interact with the API.

## API Endpoints

### Authentication

| Method | Endpoint              | Description              | Access  |
|--------|-----------------------|--------------------------|---------|
| POST   | `/api/auth/register`  | Register a new user      | Public  |
| POST   | `/api/auth/login`     | Login and get a token    | Public  |

### Books

| Method | Endpoint          | Description               | Access      |
|--------|-------------------|---------------------------|-------------|
| GET    | `/api/books`      | Get all books             | Authenticated |
| POST   | `/api/books`      | Add a new book            | Admin Only  |
| PUT    | `/api/books/:id`  | Update a book by ID       | Admin Only  |
| DELETE | `/api/books/:id`  | Delete a book by ID       | Admin Only  |

## Project Structure

```
bookstore-api/
├── src/
│   ├── controllers/      # Controllers for business logic
│   ├── models/           # Mongoose models for MongoDB
│   ├── routes/           # Route definitions
│   ├── middlewares/      # Custom middleware
│   ├── config/           # Database connection
│   ├── app.js            # Application entry point
├── package.json          # Project metadata and dependencies
├── .env                  # Environment variables
└── README.md             # Project documentation
```

## Authentication & Authorization

- **Token**: Users must send a JWT in the `Authorization` header:
  ```
  Authorization: Bearer <token>
  ```
- **Roles**:
  - **Admin**: Full access (create, update, delete books).
  - **User**: Limited access (view books only).

## Built With

- [Node.js](https://nodejs.org/) - Backend runtime
- [Express](https://expressjs.com/) - Web framework
- [MongoDB](https://www.mongodb.com/) - NoSQL database
- [Mongoose](https://mongoosejs.com/) - ODM library for MongoDB
- [JWT](https://jwt.io/) - JSON Web Tokens for authentication

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
