# User Authentication

## Objective
Provide both new and existing users with secure and seamless user authentication for guests and hosts, supporting email/password login and OAuth integration.

---

## Functional Requirements

### 1.1 User Registration

Endpoint: `POST /api/auth/register`

Description: Allow users to create accounts with email and password or via OAuth (Google, Facebook).

Inputs:
- Email address
- Password (min. 8 characters, with complexity requirements)
- Full name
- Phone number (optional)
- Role selection (guest/host)

Backend Process:
- Validate email format and uniqueness.
- Hash and store passwords securely (e.g., bcrypt).
- Generate and send a verification email with a unique link.

Outputs:
- Successful registration will result in:
  - User account creation in the database.
  - Email verification link sent to the user.

---

### 1.2 User Login

Endpoint: `POST /api/auth/login`

Description: Authenticate users via email/password or OAuth.

Inputs:
- Email and password, or OAuth token.

Backend Process:
- Validate credentials against stored data.
- Generate a JSON Web Token (JWT) upon successful authentication.
- Return the JWT for session management.

Outputs:
- Authenticated user session with JWT.
- Error message for invalid credentials.

---

### 1.3 Password Recovery

Endpoint: `POST /api/auth/forgot-password`

Description: Allow users to reset forgotten passwords.

Inputs:
- Email address.

Backend Process:
- Send a password reset link to the user’s email.
- Validate the reset link and update the password.

Outputs**:
- Password reset confirmation.

---

### 1.4 OAuth Integration

Endpoint: `POST /api/auth/oauth`

Description: Support login via Google and Facebook.

Inputs:
- OAuth token from the provider.

Backend Process:
- Validate the OAuth token with the provider.
- Create or link a user account.

Outputs:
- Authenticated user session with JWT.

---

### 1.5 Role-Based Access Control (RBAC)

Description: Differentiate permissions between guests, hosts, and admins.

Backend Process:
- Assign roles to users (guest, host, admin).
- Restrict access to features based on roles.

Outputs:
- Role-specific access to features.

---

## Non-Functional Requirements

- Security: Use HTTPS, JWT with expiration, and password hashing.
- Performance: Authentication response time < 500ms.
- Availability: 99.9% uptime for authentication services.

---

# Property Management

## Objective
Enable hosts to manage property listings, including adding, editing, and removing properties.

---

## Functional Requirements

### 2.1 Add Property

Endpoint: `POST /api/properties`

Description: Hosts can create new property listings.

Inputs:
- Property title
- Description
- Location (address, city, country)
- Price per night
- Amenities (e.g., Wi-Fi, pool)
- Availability calendar
- Property photos (uploaded to cloud storage)

Backend Process:
- Validate and store property details in the database.
- Store images in cloud storage (e.g., AWS S3).
- Mark the property as "pending" for admin approval (if required).

Outputs:
- Property listing created in the database.
- Confirmation message to the host.

---

### 2.2 Edit Property

Endpoint: `PUT /api/properties/{property_id}`

Description: Hosts can update property details.

Inputs:
- Updated property details (title, description, price, etc.).

Backend Process:
- Validate and update property details in the database.

Outputs:
- Updated property listing.
- Confirmation message to the host.

---

### 2.3 Remove Property

Endpoint: `DELETE /api/properties/{property_id}`

Description: Hosts can delete property listings.

Inputs:
- Property ID.

Backend Process:
- Remove property from the database and associated images from storage.

Outputs:
- Property listing removed.
- Confirmation message to the host.

---

### 2.4 View Listed Properties

Endpoint: `GET /api/properties?host_id={host_id}`

Description: Hosts can view their listed properties.

Inputs:
- Host ID.

Backend Process:
- Retrieve and display all properties associated with the host.

Outputs:
- List of properties with details.

---

### 2.5 Property Search and Filtering

Description: Users can search and filter properties.

Inputs:
- Location
- Price range
- Number of guests
- Amenities

Backend Process:
- Query the database for matching properties.
- Return paginated results.

Outputs:
- List of properties matching search criteria.

---

## Non-Functional Requirements

- Scalability: Support for large datasets with efficient querying.
- Storage: Secure storage for property images (e.g., AWS S3).
- Performance: Search response time < 1s.

---

# Booking System

## Objective
Enable guests to book properties and manage their bookings.

---

## Functional Requirements

### 3.1 Create Booking

Endpoint: `POST /api/bookings`

Description: Guests can book a property for specified dates.

Inputs:
- Property ID
- Check-in and check-out dates
- Number of guests
- Payment method

Backend Process:
- Check property availability for the selected dates.
- Process payment via the payment gateway (e.g., Stripe).
- Update property availability and create a booking record.

Outputs:
- Booking confirmation.
- Payment receipt.

---

### 3.2 Cancel Booking

Description: Guests or hosts can cancel bookings based on the cancellation policy.

Inputs:
- Booking ID
- Cancellation reason (optional)

Backend Process:
- Validate cancellation policy (e.g., refund rules).
- Update booking status and property availability.
- Process refunds if applicable.

Outputs:
- Booking cancellation confirmation.
- Refund details (if applicable).

---

### 3.3 View Booking History

Description: Users can view their past and current bookings.

Inputs:
- User ID.

Backend Process:
- Retrieve all bookings associated with the user.

Outputs:
- List of bookings with details.

---

### 3.4 Booking Notifications

Description: Send notifications for booking confirmations, cancellations, and updates.

Inputs:
- Booking details.

Backend Process:
- Send email and in-app notifications to the user and host.

Outputs:
- Email and in-app notifications.

---

### 3.5 Prevent Double Bookings

Description: Ensure properties are not double-booked.

Backend Process:
- Validate date availability before confirming a booking.

Outputs:
- Error message if property is unavailable.

---

## Non-Functional Requirements

- Reliability: Ensure booking data integrity and consistency.
- Performance: Booking confirmation response time < 1s.
- Security: Encrypt sensitive booking and payment data.

---

