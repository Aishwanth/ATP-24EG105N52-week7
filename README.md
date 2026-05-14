# Blog App

A blogging platform built with React, Node.js, Express, and MongoDB. Users can register, write articles, and interact with content based on their role (User, Author, or Admin).

## Project Overview

This is a full-stack blog application with role-based access control:
- **Users**: Read articles
- **Authors**: Create and manage articles
- **Admins**: Manage users and platform

## Project Structure

```
blog-app/
├── blog-app-backend/        # Express.js backend API
│   ├── APIs/                # Route handlers
│   ├── config/              # Cloudinary and file upload
│   ├── middlewares/         # Token verification
│   ├── models/              # Database schemas
│   └── server.js            # Server entry point
│
└── blog-app-frontend/       # React frontend
    ├── src/
    │   ├── components/      # React components
    │   ├── store/           # State management
    │   ├── styles/          # CSS utilities
    │   └── assets/          # Images and files
    └── vite.config.js       # Vite setup
```

## Quick Start

### Backend Setup
```bash
cd blog-app/blog-app-backend
npm install
# Create .env file with MongoDB URL and other credentials
node server.js
```
Backend runs on `http://localhost:4000`

### Frontend Setup
```bash
cd blog-app/blog-app-frontend
npm install
npm run dev
```
Frontend runs on `http://localhost:5173`

## Key Features

- User authentication with JWT tokens
- Article creation, editing, and deletion
- Image uploads to Cloudinary
- Role-based access control
- User profiles and dashboards

## Technologies

Backend: Node.js, Express.js, MongoDB, JWT, bcryptjs, Cloudinary
Frontend: React, Vite, Tailwind CSS, Axios, Zustand

## Environment Setup

Create a `.env` file in the backend with:
```
PORT=4000
DB_URL=your_mongodb_url
JWT_SECRET=your_secret_key
CLOUDINARY_NAME=your_name
CLOUDINARY_API_KEY=your_key
CLOUDINARY_API_SECRET=your_secret
```

### Build Backend
The backend runs directly with Node.js. For production:
```bash
NODE_ENV=production node server.js
```

## 🤝 Contributing

1. Create a feature branch (`git checkout -b feature/amazing-feature`)
2. Commit your changes (`git commit -m 'Add amazing feature'`)
3. Push to the branch (`git push origin feature/amazing-feature`)
4. Open a Pull Request

## 📝 License

This project is licensed under the ISC License.

## 👤 Author

Created as a capstone project for full-stack development.

## 🆘 Support

For issues or questions, please refer to:
- Backend documentation: See `blog-app-backend/README.md`
- Frontend documentation: See `blog-app-frontend/README.md`

---

**Happy Blogging! 🎉**
