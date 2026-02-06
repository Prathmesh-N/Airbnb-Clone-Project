# Listing & Review Platform

A full-stack web application built with Node.js and Express that allows users to create, view, and review property listings. This platform provides a seamless experience for users to manage listings with authentication, authorization, and review functionality.

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [File Descriptions](#file-descriptions)
- [Contributing](#contributing)
- [License](#license)

## Features

✨ **User Authentication**
- User signup and login functionality
- Secure session management
- Password encryption and validation

📍 **Listings Management**
- Create, read, update, and delete (CRUD) listings
- Display listings with detailed information
- Edit and manage your own listings
- Image upload support

⭐ **Review System**
- Add reviews and ratings to listings
- View all reviews for a listing
- Edit and delete reviews
- User-friendly rating interface

🗺️ **Map Integration**
- Interactive map display for listing locations
- Geolocation features

🔒 **Security**
- Input validation and error handling
- Authorization checks for user actions
- CSRF protection with session management

## Tech Stack

**Backend:**
- Node.js
- Express.js
- MongoDB (Database)
- Mongoose (ODM)
- EJS (Template Engine)

**Frontend:**
- HTML5
- CSS3
- JavaScript (Vanilla & Client-side)
- Bootstrap/Custom CSS

**Additional Libraries:**
- express-session (Session management)
- passport.js (Authentication)
- joi (Schema validation)
- multer (File upload)

## Project Structure

```
project-root/
├── app.js                 # Main application entry point
├── cloudConfig.js         # Cloud storage configuration (Cloudinary)
├── middleware.js          # Custom middleware functions
├── package.json           # Project dependencies
├── schema.js              # Validation schemas
│
├── controllers/           # Business logic handlers
│   ├── listings.js        # Listing controller methods
│   ├── reviews.js         # Review controller methods
│   └── users.js           # User controller methods (auth)
│
├── routes/                # API route definitions
│   ├── listing.js         # Listing routes
│   ├── review.js          # Review routes
│   └── user.js            # User authentication routes
│
├── models/                # Database schemas
│   ├── listing.js         # Listing model
│   ├── review.js          # Review model
│   └── user.js            # User model
│
├── views/                 # EJS templates
│   ├── error.ejs          # Error page template
│   ├── includes/          # Reusable components
│   │   ├── navbar.ejs     # Navigation bar
│   │   ├── footer.ejs     # Footer component
│   │   └── flash.ejs      # Flash messages
│   ├── layouts/
│   │   └── boilerplate.ejs # Main layout template
│   ├── listings/
│   │   ├── index.ejs      # Listings list page
│   │   ├── show.ejs       # Listing detail page
│   │   ├── new.ejs        # Create listing form
│   │   └── edit.ejs       # Edit listing form
│   └── users/
│       ├── signup.ejs     # User signup form
│       └── login.ejs      # User login form
│
├── public/                # Static files
│   ├── css/
│   │   ├── style.css      # Global styles
│   │   └── rating.css     # Rating component styles
│   └── js/
│       ├── script.js      # Global scripts
│       └── map.js         # Map initialization
│
├── utils/                 # Utility functions
│   ├── expressError.js    # Custom error class
│   └── wrapAsync.js       # Async error wrapper
│
└── init/                  # Database initialization
    ├── index.js           # Initialization script
    └── data.js            # Seed data
```

## Installation

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- MongoDB (local or MongoDB Atlas cloud)

### Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd MajorProject
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Create environment configuration**
   - Create a `.env` file in the root directory
   - Add the following variables:
   ```
   MONGODB_URI=your_mongodb_connection_string
   SESSION_SECRET=your_session_secret_key
   CLOUDINARY_NAME=your_cloudinary_name
   CLOUDINARY_KEY=your_cloudinary_api_key
   CLOUDINARY_SECRET=your_cloudinary_api_secret
   ```

4. **Initialize database with seed data (optional)**
   ```bash
   npm run init
   ```

5. **Start the application**
   ```bash
   npm start
   ```

   Or for development with auto-reload:
   ```bash
   npm run dev
   ```

6. **Open in browser**
   ```
   http://localhost:3000
   ```

## Configuration

### app.js
Main application file where Express server is configured with:
- Route definitions
- Middleware setup
- Error handling
- Server initialization

### cloudConfig.js
Cloud storage configuration for image uploads using Cloudinary API.

### middleware.js
Custom middleware functions for:
- Authentication verification
- Authorization checks
- Error handling
- Request logging

### schema.js
Data validation schemas using Joi for:
- Listing validation
- Review validation
- User input validation

## Usage

### Creating a Listing
1. Sign up or log in to your account
2. Navigate to "Create Listing"
3. Fill in listing details (title, description, price, location, images)
4. Submit the form

### Adding Reviews
1. View a listing
2. Scroll to the reviews section
3. Fill in your review and rating
4. Submit the review

### Editing/Deleting
- Edit or delete only your own listings and reviews
- Use the edit/delete buttons on the detail pages

## API Endpoints

### User Routes
- `GET /signup` - Signup page
- `POST /signup` - Create new user
- `GET /login` - Login page
- `POST /login` - Authenticate user
- `GET /logout` - Logout user

### Listing Routes
- `GET /listings` - View all listings
- `GET /listings/new` - New listing form
- `POST /listings` - Create listing
- `GET /listings/:id` - View listing details
- `GET /listings/:id/edit` - Edit listing form
- `PUT /listings/:id` - Update listing
- `DELETE /listings/:id` - Delete listing

### Review Routes
- `POST /listings/:id/reviews` - Add review
- `DELETE /listings/:id/reviews/:reviewId` - Delete review

## File Descriptions

### Controllers
- **listings.js** - Handles all listing operations (create, read, update, delete)
- **reviews.js** - Manages review operations and validations
- **users.js** - Manages user authentication and registration

### Models
- **listing.js** - Mongoose schema for listings with properties and validation
- **review.js** - Mongoose schema for reviews with ratings
- **user.js** - Mongoose schema for users with authentication methods

### Routes
- **listing.js** - Express routes for listing endpoints
- **review.js** - Express routes for review endpoints
- **user.js** - Express routes for user authentication

### Utilities
- **expressError.js** - Custom error class for consistent error handling
- **wrapAsync.js** - Wrapper for async route handlers to catch errors

### Views
- **boilerplate.ejs** - Main HTML layout used by all pages
- **navbar.ejs** - Navigation component
- **footer.ejs** - Footer component
- **flash.ejs** - Flash message display
- **listings/index.ejs** - Display all listings
- **listings/show.ejs** - Listing detail with reviews
- **listings/new.ejs** - Form to create new listing
- **listings/edit.ejs** - Form to edit listing
- **users/signup.ejs** - Registration form
- **users/login.ejs** - Login form

### Public Assets
- **style.css** - Global styles and layout
- **rating.css** - Star rating component styles
- **script.js** - Client-side JavaScript functionality
- **map.js** - Map initialization and functionality

### Initialization
- **index.js** - Database connection and initialization script
- **data.js** - Sample/seed data for development

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

**Last Updated:** February 2026

For issues and questions, please open an issue on the GitHub repository.
