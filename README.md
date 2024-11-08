# User Authentication and Profile Management API

This is a simple API for user authentication, registration, and profile management, built using Node.js, Express.js, and MongoDB. The API supports user registration, login, updating account information, handling avatar and cover images, and secure routes for logged-in users.

## Features

- **User Registration**: Allows new users to register with their username, email, full name, password, avatar image, and cover image.
- **User Login**: Users can log in with their email and password to receive an access token for subsequent requests.
- **Profile Management**: Users can update their account information, including username, full name, avatar, and cover images.
- **Secure Routes**: Only accessible with a valid JWT token:
  - Change password
  - Logout
  - Refresh access token
  - Get current user information
  - Update account details

## API Routes

### 1. **Register a New User**

- **Endpoint**: `/register`
- **Method**: `POST`
- **Description**: Register a new user with email, username, password, full name, and images (avatar and cover).
- **Request Body**:
  ```json
  {
    "userName": "newuser",
    "email": "newuser@example.com",
    "fullName": "New User",
    "password": "password123",
    "avatarImage": "image_url",
    "coverImage": "image_url"
  }
  ```

### 2. **Login User**

- **Endpoint**: `/login`
- **Method**: `POST`
- **Description**: Logs in a user and returns an access token and refresh token.
- **Request Body**:
  ```json
  {
    "email": "user@example.com",
    "password": "password123"
  }
  ```

### 3. **Logout User**

- **Endpoint**: `/logout`
- **Method**: `POST`
- **Description**: Logs the user out by invalidating the current JWT token.
- **Headers**:
  - Authorization: `Bearer <AccessToken>`

### 4. **Refresh Token**

- **Endpoint**: `/refresh-token`
- **Method**: `POST`
- **Description**: Refreshes the access token using the refresh token.
- **Headers**:
  - Authorization: `Bearer <RefreshToken>`

### 5. **Change Password**

- **Endpoint**: `/change-password`
- **Method**: `POST`
- **Description**: Changes the user's password.
- **Headers**:
  - Authorization: `Bearer <AccessToken>`
- **Request Body**:
  ```json
  {
    "oldPassword": "oldpassword",
    "newPassword": "newpassword123"
  }
  ```

### 6. **Get Current User Info**

- **Endpoint**: `/get-current-user`
- **Method**: `GET`
- **Description**: Retrieves the current user's details.
- **Headers**:
  - Authorization: `Bearer <AccessToken>`

### 7. **Update Account Info**

- **Endpoint**: `/update-account`
- **Method**: `PATCH`
- **Description**: Updates the current user's account information.
- **Headers**:
  - Authorization: `Bearer <AccessToken>`
- **Request Body**:
  ```json
  {
    "userName": "updatedusername",
    "fullName": "Updated Full Name"
  }
  ```

### 8. **Update Avatar Image**

- **Endpoint**: `/update-user-avatar`
- **Method**: `PATCH`
- **Description**: Updates the user's avatar image.
- **Headers**:
  - Authorization: `Bearer <AccessToken>`
- **Body**: `multipart/form-data` with `avatarImage` as a file.

### 9. **Update Cover Image**

- **Endpoint**: `/update-user-cover`
- **Method**: `PATCH`
- **Description**: Updates the user's cover image.
- **Headers**:
  - Authorization: `Bearer <AccessToken>`
- **Body**: `multipart/form-data` with `coverImage` as a file.

## Middleware

- **verifyJWT**: A middleware function to protect secured routes by checking if the JWT token is valid.
- **upload**: Middleware to handle file uploads for avatar and cover images.

## Technologies Used

- **Node.js**: JavaScript runtime for server-side logic.
- **Express.js**: Web framework for Node.js.
- **MongoDB**: NoSQL database to store user data.
- **Mongoose**: ODM for MongoDB, used for defining the user model and interacting with the database.
- **JWT (JSON Web Tokens)**: For secure authentication and token management.
- **Cloudinary**: For storing and managing avatar and cover images (or any other image hosting service).

## How to Run

### 1. **Clone the Repository**

```bash
git clone https://github.com/yourusername/your-repository.git
cd your-repository
```

### 2. **Install Dependencies**

```bash
npm install
```

### 3. **Set Up Environment Variables**

```bash
PORT =
CORS_ORIGIN =
MONGODB_URI =
ACCESS_TOKEN_SECRET =
ACCESS_TOKEN_EXPIRY =
REFRESH_TOKEN_SECRET =
REFRESH_TOKEN_EXPIRY =
CLOUDINARY_CLOUD_NAME =
CLOUDINARY_API_KEY =
CLOUDINARY_API_SECRET =
```

### 4. **Start the Server**

```bash
npm run dev
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -am 'Add feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new pull request.

We welcome all contributions! Please make sure your code adheres to the existing coding style, and include tests for new functionality where applicable.
