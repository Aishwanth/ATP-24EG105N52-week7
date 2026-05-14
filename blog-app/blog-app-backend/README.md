# Blog App Backend

Express.js API server for the blog application. Handles user authentication, article management, and role-based access.

## Overview

This backend provides REST APIs for managing users, articles, and authentication with three user roles: USER, AUTHOR, and ADMIN.

## Folder Structure

```
blog-app-backend/
├── APIs/                    # Route handlers
│   ├── UserAPI.js          # User routes
│   ├── AuthorAPI.js        # Author routes
│   ├── AdminAPI.js         # Admin routes
│   └── CommonAPI.js        # Auth routes
├── config/                 # File upload config
├── middlewares/            # Token verification
├── models/                 # Database schemas
└── server.js              # Main server
```

## Getting Started

### Install Dependencies
```bash
npm install
```

### Create .env File
```
PORT=4000
DB_URL=your_mongodb_url
JWT_SECRET=your_secret_key
CLOUDINARY_NAME=your_name
CLOUDINARY_API_KEY=your_key
CLOUDINARY_API_SECRET=your_secret
```

### Start Server
```bash
node server.js
```
Server runs on `http://localhost:4000`

## Main Dependencies

- express: Web framework
- mongoose: MongoDB connection
- jsonwebtoken: JWT authentication
- bcryptjs: Password hashing
- cors: Cross-origin requests
- multer: File uploads
- cloudinary: Cloud storage

## API Routes

### Authentication
- POST `/auth/user-register` - Register user
- POST `/auth/author-register` - Register author
- POST `/auth/login` - Login
- GET `/auth/logout` - Logout
- GET `/auth/check-auth` - Verify login

### User Routes
- GET `/user-api/user-profile` - Get profile
- GET `/user-api/articles` - Get articles

### Author Routes
- GET `/author-api/author-profile` - Get profile
- GET `/author-api/articles` - Get articles
- POST `/author-api/articles` - Create article
- PUT `/author-api/articles/:id` - Update article
- DELETE `/author-api/articles/:id` - Delete article

### Admin Routes
- GET `/admin-api/users` - Get all users
- GET `/admin-api/articles` - Get all articles
- DELETE `/admin-api/users/:id` - Remove user
- DELETE `/admin-api/articles/:id` - Remove article

## Login Response

```json
{
  "message": "login success",
  "payload": {
    "_id": "user_id",
    "email": "user@example.com",
    "role": "USER"
  }
}
```
GET /admin-api/users
Headers: {
  "Authorization": "Bearer <token>",
  "Role": "ADMIN"
}
```

#### Get All Articles
```
GET /admin-api/articles
Headers: {
  "Authorization": "Bearer <token>",
  "Role": "ADMIN"
}
```

#### Delete User
```
DELETE /admin-api/users/:id
Headers: {
  "Authorization": "Bearer <token>",
  "Role": "ADMIN"
}
```

#### Delete Article
```
DELETE /admin-api/articles/:id
Headers: {
  "Authorization": "Bearer <token>",
  "Role": "ADMIN"
}
```

## 🔐 Authentication

### JWT Token Format

The API uses JWT tokens for authentication. Include the token in the Authorization header:

```
Authorization: Bearer <your_token_here>
```

### Token Verification Middleware

The `verifyToken` middleware validates JWT tokens and extracts user information. Protected routes will automatically verify the token.

## 📊 Database Schema

### User Model
```javascript
{
  username: String (required, unique),
  email: String (required, unique),
  password: String (required, hashed),
  role: String (enum: ['USER', 'AUTHOR', 'ADMIN'], default: 'USER'),
  phone: String,
  address: String,
  profileImage: String (Cloudinary URL),
  createdAt: Date (default: now),
  updatedAt: Date (default: now)
}
```

### Article Model
```javascript
{
  title: String (required),
  body: String (required),
  category: String,
  image: String (Cloudinary URL),
  authorId: ObjectId (reference to User),
  status: String (enum: ['PUBLISHED', 'DELETED'], default: 'PUBLISHED'),
  createdAt: Date (default: now),
  updatedAt: Date (default: now)
}
```

## ⚙️ Configuration

### Cloudinary Setup

1. Sign up at [Cloudinary.com](https://cloudinary.com)
2. Get your credentials:
   - Cloud Name
   - API Key
   - API Secret

3. Add to `.env`:
```env
CLOUDINARY_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

### MongoDB Setup

1. Create a MongoDB Atlas account at [MongoDB.com](https://mongodb.com)
2. Create a cluster
3. Get your connection string: `mongodb+srv://user:password@cluster.mongodb.net/db_name`
4. Add to `.env`:
```env
DB_URL=mongodb+srv://user:password@cluster.mongodb.net/blog_app
```

## 🧪 Testing

Use the provided HTTP request files to test endpoints:

- `user-req.http` - User API endpoints
- `author-req.http` - Author API endpoints
- `admin-req.http` - Admin API endpoints

Tools:
- VS Code REST Client extension
- Postman
- Thunder Client
- curl commands

Example with curl:
```bash
curl -X POST http://localhost:4000/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "password123"
  }'
```

## 🛡️ Security Features

### Password Security
- Passwords hashed with bcryptjs before storage
- Hash rounds: 10
- Never store plain-text passwords

### JWT Security
- Token expiration set to 24 hours
- Secret key required (minimum 32 characters)
- Tokens verified on protected routes

### CORS Configuration
```javascript
cors({
  origin: "http://localhost:5173",  // Frontend URL
  credentials: true
})
```

### Environment Variables
- All sensitive data in `.env`
- Never commit `.env` to version control
- Use strong, unique secrets

## 📝 Error Handling

All endpoints return consistent error responses:

```json
{
  "message": "Error description",
  "error": "Detailed error information"
}
```

Common Status Codes:
- `200` - Success
- `201` - Created
- `400` - Bad Request
- `401` - Unauthorized
- `403` - Forbidden
- `404` - Not Found
- `500` - Server Error

## 🚀 Deployment

### Production Build

1. Set environment variable:
```bash
NODE_ENV=production
```

2. Start server:
```bash
node server.js
```

### Deployment Options
- Heroku
- AWS EC2
- Google Cloud Run
- DigitalOcean
- Railway
- Render

## 📚 Additional Resources

- [Express.js Documentation](https://expressjs.com)
- [Mongoose ODM Guide](https://mongoosejs.com)
- [JWT.io](https://jwt.io)
- [Cloudinary Docs](https://cloudinary.com/documentation)

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Submit a pull request

## 📄 License

ISC License - See LICENSE file for details

---

**Questions or Issues?** Please refer to the main [README.md](../README.md)
