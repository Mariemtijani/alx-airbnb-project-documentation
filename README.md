# 📘 Backend Features and Functionalities – Airbnb Clone

This document provides a visual and technical overview of the **backend architecture and key functionalities** of the Airbnb Clone project. It has been created using **Draw.io**, as required.

## 📊 Diagram Overview

The included diagram (`backend-architecture.png`) illustrates the major backend modules, their responsibilities, and how they interact. The structure follows a modular and RESTful design.

### ✅ Included Features and Services

- **Authentication & Authorization**
  - Register/Login
  - JWT-based sessions
  - Role-Based Access Control (Guest, Host, Admin)

- **Property Management**
  - CRUD operations for property listings
  - Linked to host accounts

- **Booking System**
  - Book/cancel properties with date validation
  - Booking status tracking (Pending, Confirmed, Canceled)

- **Payment Integration**
  - Handles guest payments via Stripe/PayPal
  - Supports payout to hosts
  - Multi-currency support

- **Reviews & Ratings**
  - Guests can rate properties
  - Hosts can respond
  - Reviews linked to bookings

- **Notification System**
  - Email & in-app alerts for booking confirmations, cancellations, payment updates

- **Admin Panel**
  - Admin access to users, properties, bookings, and payment records

- **Database Layer**
  - Tables: Users, Properties, Bookings, Payments, Reviews
  - Relational structure (PostgreSQL/MySQL)

## 🛠️ Technologies Represented

- **Database**: PostgreSQL or MySQL
- **API**: RESTful endpoints
- **Auth**: JWT
- **Storage**: AWS S3 or Cloudinary (for images)
- **Emails**: SendGrid or Mailgun
- **Optional**: Redis caching, GraphQL (for flexible querying)

## 📁 Location

This file and the diagram are located inside:

