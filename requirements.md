# 📘 Backend Feature Requirements – Airbnb Clone

This document outlines the technical and functional requirements for three core backend features:

- User Authentication
- Property Management
- Booking System

---

## 🔐 1. User Authentication

### Functional Requirements:
- Users (Guests and Hosts) can register and log in.
- Role-based access control: Guest, Host, Admin.
- Secure password hashing and JWT-based session management.

### API Endpoints:

| Method | Endpoint         | Description          |
|--------|------------------|----------------------|
| POST   | /auth/register   | Register a new user  |
| POST   | /auth/login      | Log in a user        |
| GET    | /auth/me         | Get current user info (authenticated) |

### Input Example:
```json
{
  "name": "Alice",
  "email": "alice@example.com",
  "password": "SecurePass123"
}
```

### Output Example:
```json
{
  "userId": "u123456",
  "token": "jwt.token.here"
}
```

### Validation Rules:
- Email must follow valid format
- Password must be at least 8 characters
- Email must be unique

### Performance Criteria:
- Login should respond within 500ms
- Tokens expire in 24 hours by default

---

## 🏠 2. Property Management

### Functional Requirements:
- Hosts can create, edit, and delete property listings.
- Properties have: title, description, location, price, availability, and images.
- Guests can browse all available properties.

### API Endpoints:

| Method | Endpoint           | Description          |
|--------|--------------------|----------------------|
| POST   | /properties        | Add new property     |
| PUT    | /properties/:id    | Update a property    |
| DELETE | /properties/:id    | Delete a property    |
| GET    | /properties        | View all properties  |

### Input Example:
```json
{
  "title": "Beachfront Bungalow",
  "description": "A peaceful retreat with ocean views",
  "price": 120,
  "hostId": "h001"
}
```

### Output Example:
```json
{
  "propertyId": "p001",
  "status": "created"
}
```

### Validation Rules:
- Title and description must not be empty
- Price must be a number > 0
- Host ID must be valid and linked to an authenticated user

### Performance Criteria:
- Should support filtering by price, location, and availability
- Listing fetch time ≤ 800ms

---

## 📅 3. Booking System

### Functional Requirements:
- Guests can book properties for specific dates.
- Prevent double booking by validating date overlap.
- Bookings can be pending, confirmed, canceled, or completed.

### API Endpoints:

| Method | Endpoint         | Description             |
|--------|------------------|-------------------------|
| POST   | /bookings        | Create a new booking    |
| GET    | /bookings/:id    | Get booking information |
| DELETE | /bookings/:id    | Cancel a booking        |

### Input Example:
```json
{
  "guestId": "g001",
  "propertyId": "p001",
  "startDate": "2025-08-01",
  "endDate": "2025-08-05"
}
```

### Output Example:
```json
{
  "bookingId": "b1001",
  "status": "confirmed"
}
```

### Validation Rules:
- Dates must be in the future
- Property must be available for selected range
- User must be authenticated as guest

### Performance Criteria:
- Conflict checks must complete within 300ms
- Bookings should update availability in real time

---

## 📦 Notes

- All endpoints require appropriate authentication and authorization middleware.
- JSON is used for all API payloads.
- Errors must follow a standard format with appropriate HTTP status codes.
