# Airbnb Clone - Backend System

## Project Overview

This project is a backend implementation of an Airbnb-like property rental platform. It provides secure user authentication, property management, booking system, and administrative functionalities.

## Features

### 1. User Authentication
- Secure registration and login system
- Email verification
- OAuth integration (Google, Facebook)
- Role-based access control (guest, host, admin)
- Password recovery

### 2. Property Management
- Property listing creation and management
- Property search and filtering
- Cloud storage for property images
- Admin approval workflow for new listings

### 3. Booking System
- Property reservation system
- Booking confirmation and cancellation
- Payment processing integration
- Booking history tracking
- Notification system

### 4. Admin Dashboard
- User and property management
- Booking monitoring
- System analytics

## Technical Requirements

### Backend
- **Language**: Node.js (or Python/Django)
- **Database**: PostgreSQL or MySQL
- **Authentication**: JWT (JSON Web Tokens)
- **API**: RESTful architecture with proper HTTP methods and status codes
- **File Storage**: AWS S3 or Cloudinary for images

### Core Features

#### User Management
- User registration and profile management
- Authentication via email/password and OAuth
- Role-based access control (guest, host, admin)

#### Property Management
- Property listing creation and management
- Property search with filters (location, price, amenities)
- Image upload and storage

#### Booking System
- Booking creation and management
- Payment processing integration
- Availability calendar
- Notification system

#### Payment Integration
- Secure payment gateway (Stripe, PayPal)
- Multiple currency support
- Automatic payouts to hosts

### Non-Functional Requirements
- **Security**: Data encryption, firewalls, rate limiting
- **Performance**: Response times < 1s for critical operations
- **Scalability**: Modular architecture with horizontal scaling capability
- **Testing**: Unit and integration tests

## API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/forgot-password` - Password recovery
- `POST /api/auth/oauth` - OAuth login

### Property Management
- `POST /api/properties` - Create property listing
- `PUT /api/properties/{id}` - Update property
- `DELETE /api/properties/{id}` - Delete property
- `GET /api/properties?host_id={id}` - View host's properties
- `GET /api/properties/search` - Search/filter properties

### Booking System
- `POST /api/bookings` - Create booking
- `DELETE /api/bookings/{id}` - Cancel booking
- `GET /api/bookings?user_id={id}` - View user's bookings

## Installation

### Prerequisites
- Node.js (v16+)
- PostgreSQL/MySQL
- AWS S3 or Cloudinary account for file storage

### Setup
1. Clone the repository
2. Install dependencies: `npm install`
3. Set up database connection in `.env` file
4. Run migrations: `npm run migrate`
5. Start the server: `npm start`

## Configuration

Create a `.env` file with the following variables:
