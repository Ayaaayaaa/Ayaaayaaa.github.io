---
title: ServiceSphere - Freelance Marketplace Platform
date: 2024-06-20 22:04:00 -500
categories: [web development, full-stack, marketplace platform]
tags: [React.js, Node.js, Express.js, MySQL, Prisma ORM, JWT, bcrypt, Tailwind CSS]
---

# Overview:
ServiceSphere is a comprehensive freelance marketplace platform built using React.js, Node.js, Express.js, and MySQL. It provides a secure and scalable environment where freelancers can offer their services and clients can post project offers. The platform features role-based authentication, service management, offer posting, and a complete review system to facilitate professional collaboration in the digital economy.

# Technologies Used:
* React.js
* Node.js
* Express.js
* MySQL
* Prisma ORM
* JSON Web Tokens (JWT)
* bcrypt for password hashing
* Tailwind CSS
* Nodemon
* Postman

# Key Features:

### Multi-Role Authentication System:
* Supports three distinct user roles: Freelancers, Clients, and Administrators.
* Secure user registration and login with email validation and uniqueness checks.
* JWT-based authentication with role-specific access control and protected routes.
* Password encryption using bcrypt for maximum security.

### Service Management:
* Freelancers can create, read, update, and delete their service listings.
* Services include detailed information such as title, description, category, and hourly pricing.
* Skill association system allowing freelancers to tag relevant expertise areas.
* Search and filtering capabilities for service discovery.

### Offer Management:
* Clients can post detailed project offers with budgets, deadlines, and skill requirements.
* Freelancers can browse available offers and submit applications.
* Status tracking system for offer management and application monitoring.
* Automated notifications for offer applications and updates.

### User Profile System:
* Comprehensive user profiles with bio, location, availability, and social media integration.
* Portfolio showcase capabilities for freelancers to display previous work.
* Profile management with skill listings and professional information.
* Review and rating system for completed services.

### Comment and Review System:
* Interactive commenting system on service listings.
* Client feedback and rating mechanism for freelancer services.
* Public display of reviews and ratings on freelancer profiles.
* Moderation capabilities for maintaining platform quality.

### Responsive Design:
* Mobile-first approach ensuring optimal experience across all devices.
* Multilingual support for English, French, and Arabic interfaces.
* Modern UI components built with Tailwind CSS for consistent styling.
* Intuitive navigation and user experience design.

# Technical Approach:

#### Dependencies:
```json
{
  "dependencies": {
    "@prisma/client": "^5.0.0",
    "bcrypt": "^5.1.1",
    "express": "^4.19.2",
    "jsonwebtoken": "^9.0.2",
    "mysql2": "^3.6.0",
    "prisma": "^5.0.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "tailwindcss": "^3.3.0"
  },
  "devDependencies": {
    "nodemon": "^3.1.4"
  }
}
```

#### Project Structure:
The project follows a modern full-stack architecture with clear separation between frontend and backend components, ensuring maintainability and scalability.

##### Backend Structure:
```
backend/
├── prisma/
│   ├── migrations/
│   └── schema.prisma       # Database schema definition
├── src/
│   ├── config/
│   │   └── prisma.js       # Database configuration
│   ├── controllers/        # Business logic handlers
│   ├── middleware/
│   │   ├── authMiddleware.js # JWT authentication middleware
│   │   └── errorHandler.js   # Centralized error handling
│   ├── routes/             # API endpoint definitions
│   ├── services/           # Data access layer
│   └── utils/
│       ├── jwtUtil.js      # JWT utility functions
│       └── validation.js   # Input validation helpers
├── app.js                  # Application entry point
└── package.json
```

##### Frontend Structure:
```
frontend/
├── public/
│   ├── images/
│   └── index.html
├── src/
│   ├── api/
│   │   ├── auth.js         # Authentication API calls
│   │   ├── services.js     # Service management API
│   │   ├── offers.js       # Offer management API
│   │   └── profiles.js     # Profile management API
│   ├── components/
│   │   ├── Header.js       # Navigation component
│   │   ├── Footer.js       # Footer component
│   │   ├── Card.js         # Reusable card component
│   │   └── ProtectedRoute.js # Route protection wrapper
│   ├── pages/
│   │   ├── HomePage.js     # Landing page
│   │   ├── LoginPage.js    # User authentication
│   │   ├── RegisterPage.js # User registration
│   │   ├── FreelancerPage.js # Freelancer dashboard
│   │   ├── ClientPage.js   # Client dashboard
│   │   └── ProfilePage.js  # User profile management
│   ├── App.js              # Main application component
│   └── index.js            # Application entry point
```

##### Database Schema (MySQL with Prisma):
The database follows a normalized structure ensuring data integrity and optimal performance:

* **Users Table**: Stores user information including authentication credentials, profile details, and role assignments.
* **Services Table**: Contains freelancer service listings with pricing, descriptions, and skill associations.
* **Offers Table**: Manages client project postings with requirements, budgets, and deadlines.
* **Comments Table**: Handles user interactions and feedback on services.
* **Skills Table**: Maintains skill taxonomy for matching and filtering purposes.
* **SocialLinks Table**: Stores professional social media profiles and portfolio links.

##### API Endpoints:

* **User Authentication**:
  - Endpoint: /api/auth/register
  - HTTP Method: POST
  - Description: Handles user registration with role selection and email validation.

  - Endpoint: /api/auth/login
  - HTTP Method: POST
  - Description: Authenticates users and generates JWT tokens for session management.

  - Endpoint: /api/auth/profile
  - HTTP Method: GET
  - Description: Retrieves authenticated user profile information.

* **Service Management**:
  - Endpoint: /api/services
  - HTTP Method: GET
  - Description: Fetches paginated service listings with search and filter capabilities.

  - Endpoint: /api/services
  - HTTP Method: POST
  - Description: Creates new service listings for authenticated freelancers.

  - Endpoint: /api/services/:id
  - HTTP Method: PUT
  - Description: Updates existing service information (owner authorization required).

  - Endpoint: /api/services/:id
  - HTTP Method: DELETE
  - Description: Removes service listings (owner authorization required).

* **Offer Management**:
  - Endpoint: /api/offers
  - HTTP Method: GET
  - Description: Retrieves available project offers for freelancer browsing.

  - Endpoint: /api/offers
  - HTTP Method: POST
  - Description: Creates new project offers for authenticated clients.

  - Endpoint: /api/offers/:id/apply
  - HTTP Method: POST
  - Description: Submits freelancer applications to specific offers.

##### app.js (Backend):
This file establishes the core Express.js application infrastructure, including: Environment variable configuration, Express server initialization, middleware setup for CORS and JSON parsing, Prisma database connection establishment, route mounting for API endpoints, centralized error handling implementation, and server startup with port configuration.

##### App.js (Frontend):
The main React component that orchestrates the entire frontend application, including: React Router setup for client-side navigation, authentication context provider for state management, protected route implementations, component composition and layout structure, and global state management for user sessions.

# Development Challenges:

### Frontend-Backend Integration:
During the development process, significant challenges arose when integrating the frontend React application with the backend Express API. While both components functioned correctly in isolation, the integration phase revealed several technical hurdles including CORS configuration issues, API endpoint mismatches, and authentication token handling inconsistencies. This experience highlighted the critical importance of early integration testing and consistent API contract definition throughout the development lifecycle.

# Future Enhancements:
* Real-time messaging system between freelancers and clients using WebSocket technology.
* Payment gateway integration with Stripe or PayPal for secure transaction processing.
* Advanced search algorithms with Elasticsearch for improved service discovery.
* AI-powered matching system to connect relevant freelancers with suitable projects.
* Mobile application development using React Native for iOS and Android platforms.
* Analytics dashboard providing insights for freelancers, clients, and administrators.

# Project Link:
[GitHub Repository](https://github.com/m-elhamlaoui/projet-web-achchab_moukil.git)