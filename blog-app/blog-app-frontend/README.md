# Blog App Frontend

React application built with Vite and Tailwind CSS. Provides a user interface for reading and writing blog articles.

## Overview

This is a single-page React application that connects to the backend API. It supports different user roles (USER, AUTHOR, ADMIN) with different features for each.

## Folder Structure

```
blog-app-frontend/
├── src/
│   ├── components/              # React components
│   ├── store/                   # State management
│   ├── styles/                  # CSS utilities
│   ├── assets/                  # Images
│   ├── App.jsx                  # Main app
│   └── main.jsx                 # Entry point
├── vite.config.js              # Vite config
└── package.json
```

## Getting Started

### Install Dependencies
```bash
npm install
```

### Start Development Server
```bash
npm run dev
```
App runs on `http://localhost:5173`

Make sure backend is running on `http://localhost:4000`

## Main Dependencies

- react: UI library
- vite: Build tool
- tailwindcss: Styling
- axios: HTTP requests
- zustand: State management
- react-router: Navigation
- react-hook-form: Form handling
- react-hot-toast: Notifications

## Pages

- `/` - Home page
- `/register` - User registration
- `/login` - User login
- `/user-profile` - User dashboard
- `/author-profile` - Author dashboard
- `/admin-profile` - Admin dashboard
- `/article/:id` - Read article
- `/write-article` - Create article
- `/edit-article` - Edit article

## User Roles

- **USER**: Can read articles
- **AUTHOR**: Can create and edit articles
- **ADMIN**: Can manage users

## Key Components

- Header: Navigation bar
- Login: Login form
- Register: Registration form
- Articles: Article listing
- WriteArticles: Article editor
- UserProfile: User dashboard
- AuthorProfile: Author dashboard
- AdminProfile: Admin dashboard

## Build for Production
```bash
npm run build
```

Creates optimized build in `dist/` folder.
```jsx
import Login from "./components/Login"
import Register from "./components/Register"
```
- Form validation
- Error messages
- Success feedback

## 🔄 State Management (Zustand)

### Auth Store
```javascript
import { useAuth } from "../store/authStore"

// Usage
const { isAuthenticated, currentUser, login, logout } = useAuth()
```

### Store Structure
```javascript
{
  currentUser: {
    id: string,
    username: string,
    email: string,
    role: 'USER' | 'AUTHOR' | 'ADMIN'
  },
  isAuthenticated: boolean,
  token: string,
  login: (credentials) => Promise,
  logout: () => void
}
```

## 📡 API Communication

### Axios Setup
```javascript
import axios from 'axios'

const api = axios.create({
  baseURL: 'http://localhost:4000'
})

// Add token to requests
api.interceptors.request.use((config) => {
  const token = useAuth.getState().token
  if (token) {
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})
```

### Making API Calls
```javascript
try {
  const response = await api.get('/user-api/articles')
  console.log(response.data)
} catch (error) {
  console.error('Error fetching articles:', error)
}
```

## 🎯 Features

### User Features
- ✅ Browse all published articles
- ✅ View article details
- ✅ User profile management
- ✅ Register and login

### Author Features
- ✅ All user features
- ✅ Create new articles
- ✅ Edit own articles
- ✅ Delete articles
- ✅ Upload article images
- ✅ View author-specific statistics

### Admin Features
- ✅ All author features
- ✅ Manage all users
- ✅ Remove inappropriate articles
- ✅ Monitor platform activity

## 🧪 Development

### Build Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Run ESLint
npm run lint
```

### Code Quality

The project uses ESLint for code consistency. Check your code:
```bash
npm run lint
```

Fix issues automatically:
```bash
npm run lint -- --fix
```

## 🚀 Production Build

Build optimized production version:
```bash
npm run build
```

This creates a `dist/` folder with:
- Minified JavaScript
- Optimized CSS
- Compressed assets
- Source maps (optional)

## 📱 Responsive Design

The frontend is fully responsive:
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

### Breakpoints
```tailwind
sm: 640px
md: 768px
lg: 1024px
xl: 1280px
2xl: 1536px
```

## 🔧 Troubleshooting

### Common Issues

**Issue**: CORS errors
- **Solution**: Ensure backend is running on port 4000
- **Solution**: Check CORS configuration in backend

**Issue**: Token expiration
- **Solution**: Clear browser localStorage and login again
- **Solution**: Check JWT_SECRET in backend .env

**Issue**: Image upload fails
- **Solution**: Verify Cloudinary credentials in backend
- **Solution**: Check file size limits in Multer config

**Issue**: Blank page on load
- **Solution**: Open browser DevTools for error messages
- **Solution**: Clear browser cache (Ctrl+Shift+Del)
- **Solution**: Check console for React errors

## 📚 Additional Resources

- [React Documentation](https://react.dev)
- [Vite Documentation](https://vitejs.dev)
- [Tailwind CSS Docs](https://tailwindcss.com)
- [React Router](https://reactrouter.com)
- [Zustand Store](https://github.com/pmndrs/zustand)
- [Axios HTTP Client](https://axios-http.com)

## 🎓 Learning Resources

### React Concepts
- Components and JSX
- Hooks (useState, useEffect, useContext)
- Component lifecycle
- Event handling

### State Management
- Zustand basics
- Store subscription
- Persistence

### Routing
- Route configuration
- Protected routes
- Nested routes
- Navigation

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Run linting: `npm run lint`
4. Build: `npm run build`
5. Submit a pull request

## 📄 License

ISC License - See LICENSE file for details

## 🆘 Support

For issues:
1. Check the console for error messages
2. Verify backend is running
3. Check backend logs
4. Refer to main [README.md](../README.md)

---

