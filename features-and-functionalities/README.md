Airbnb Clone
An Airbnb-like platform for property rentals, enabling users to browse, book, and manage properties seamlessly.

Features
1. User Authentication

User Registration: Sign up with email/password or OAuth (Google, Facebook).
User Login: Authenticate via email/password or OAuth.
Password Recovery: Reset forgotten passwords via email.
Role-Based Access Control: Differentiate permissions between guests, hosts, and admins.

2. Property Management

Add Property: Hosts can create new property listings with details and amenities.
Edit Property: Update property details.
Remove Property: Delete property listings.
View Listed Properties: Hosts can view their listed properties.
Property Search and Filtering: Users can search and filter properties by location, price range, number of guests, and amenities.

3. Booking System

Create Booking: Guests can book properties for specified dates.
Cancel Booking: Guests or hosts can cancel bookings based on the cancellation policy.
View Booking History: Users can view their past and current bookings.
Booking Notifications: Email and in-app notifications for booking confirmations, cancellations, and updates.
Prevent Double Bookings: Ensure properties are not double-booked.


Requirements
Functional Requirements
1. User Authentication

User Registration: Allow users to create accounts with email and password or via OAuth.
User Login: Authenticate users via email/password or OAuth.
Password Recovery: Allow users to reset forgotten passwords.
OAuth Integration: Support login via Google and Facebook.
Role-Based Access Control: Differentiate permissions between guests, hosts, and admins.

2. Property Management

Add Property: Hosts can create new property listings.
Edit Property: Hosts can update property details.
Remove Property: Hosts can delete property listings.
View Listed Properties: Hosts can view their listed properties.
Property Search and Filtering: Users can search and filter properties.

3. Booking System

Create Booking: Guests can book properties for specified dates.
Cancel Booking: Guests or hosts can cancel bookings.
View Booking History: Users can view their booking history.
Booking Notifications: Send notifications for booking confirmations, cancellations, and updates.
Prevent Double Bookings: Ensure properties are not double-booked.


API Endpoints
User Authentication

User Registration: POST /api/auth/register
User Login: POST /api/auth/login
Password Recovery: POST /api/auth/forgot-password
OAuth Login: POST /api/auth/oauth

Property Management

Add Property: POST /api/properties
Edit Property: PUT /api/properties/{property_id}
Remove Property: DELETE /api/properties/{property_id}
View Listed Properties: GET /api/properties?host_id={host_id}

Booking System

Create Booking: POST /api/bookings
Cancel Booking: DELETE /api/bookings/{booking_id}
View Booking History: GET /api/bookings?user_id={user_id}


Non-Functional Requirements

Security: Use HTTPS, JWT with expiration, and password hashing.
Performance: Authentication response time < 500ms, search response time < 1s, booking confirmation response time < 1s.
Availability: 99.9% uptime for authentication services.
Scalability: Support for large datasets with efficient querying.
Storage: Secure storage for property images (e.g., AWS S3).
Reliability: Ensure booking data integrity and consistency.


Installation


Clone the Repository:
bash Copygit clone <repository_url>
cd airbnb-clone


Install Dependencies:
bash Copynpm install


Configure Environment Variables:

Create a .env file and add the necessary environment variables.
Example:
env CopyDB_HOST=localhost
DB_USER=root
DB_PASSWORD=password
DB_NAME=airbnb_clone
JWT_SECRET=your_jwt_secret




Run the Application:
bash Copynpm start



Usage


Register a New User:
bash Copycurl -X POST /api/auth/register -d '{"email": "user@example.com", "password": "SecurePass123!", "full_name": "John Doe", "role": "guest"}'


Login:
bash Copycurl -X POST /api/auth/login -d '{"email": "user@example.com", "password": "SecurePass123!"}'


Add a Property:
bash Copycurl -X POST /api/properties -d '{"title": "Cozy Apartment", "description": "A cozy apartment in the city center", "address": "123 Main St", "city": "New York", "country": "USA", "price_per_night": 100.00, "amenities": ["Wi-Fi", "Kitchen", "TV"], "available_dates": ["2025-11-01", "2025-11-10"]}'


Book a Property:
bash Copycurl -X POST /api/bookings -d '{"property_id": 1, "check_in_date": "2025-11-01", "check_out_date": "2025-11-05", "number_of_guests": 2, "payment_method": "credit_card"}'

Contributing
Fork the repository.
Create a new branch: git checkout -b feature-branch.
Make your changes and commit them: git commit -m 'Add new feature'.
Push to the branch: git push origin feature-branch.
Submit a pull request.

