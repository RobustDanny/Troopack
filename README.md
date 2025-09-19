Troopack
Troopack is a comprehensive subscription-based platform designed for managing customer relationships and support. It consists of a main website for user registration and subscription handling, a CRM system for managing records and operations, and integrated chat support. The system is built with a microservices-like architecture using Docker containers, sharing a common database, and leveraging WebSockets for real-time events.
Overview
The platform enables users to subscribe via the main website, after which their details are seamlessly integrated into the CRM system. Users receive credentials via email to access the CRM as owners, or they can be invited as operators/admins to specific projects. The entire codebase is written in English, ensuring clarity and maintainability.
Key components:

Main Website: Handles user registration, subscription payments, and initial record creation.
CRM System: Manages user records, projects, and access roles.
Chat Support: Provides real-time communication, integrated with the CRM server.

The system runs in three Docker containers:

Shared Database Container (for storing all records).
Main Website Container (Go backend + React Vite frontend).
CRM and Chat Support Container (Go backend + React TypeScript frontend for CRM, JavaScript for chat support).

Real-time events, such as updates and notifications, are handled via WebSockets.
Features

User Registration and Subscription:

Users register on the main website.
Upon successful subscription payment, a record is created in the shared database.
A password is generated and sent via email for CRM access.


CRM Access:

Owner Login: Users can log in to the CRM as owners via the "Go to CRM" button on the main website.
Invited Roles: Owners can generate invite links for operators or admins to join specific projects within the CRM.


Real-Time Functionality:

WebSockets enable live updates, chat support, and event notifications across the system.


Security and Integration:

Shared database ensures data consistency between the main site and CRM.
Role-based access control for different user types (owners, operators, admins).



Architecture

Containers:

Database Container: Hosts the shared database (e.g., PostgreSQL or similar) where all user and subscription records are stored.
Main Website Container:

Backend: Go server for handling API requests, payments, and database interactions.
Frontend: React with Vite for a fast, responsive user interface.


CRM Container:

Backend: Go server shared with chat support.
Frontend: React with TypeScript for type-safe development.
Chat Support: JavaScript-based, running on the same server for efficiency.




Data Flow:

User subscribes on the main website.
Go backend processes payment and creates a record in the shared DB.
Password is emailed to the user.
User logs into CRM:

Directly as owner from the main site.
As operator/admin via invite links.


Real-time events (e.g., chat messages, updates) are propagated via WebSockets.


Technologies:

Backend: Go (for both main site and CRM).
Frontend: React Vite (main site), React TypeScript (CRM).
Real-Time: WebSockets.
Database: Shared relational DB (containerized).
Deployment: Docker containers for modularity and scalability.
Other: Email integration for password delivery, payment gateway (e.g., Stripe or similar, not specified in core code).



How It Works

Registration on Main Website:

User visits https://troopack.com/ and registers.
Submits payment for subscription.


Post-Subscription Process:

Main Go server creates a CRM record in the shared DB.
Generates a secure password and sends it via email.


CRM Login:

As Owner: Click "Go to CRM" on the main site for seamless login.
As Operator/Admin: Use invite links provided by owners to access specific projects.


Operations in CRM:

Manage projects, users, and support via the React TypeScript interface.
Engage in real-time chat support using JavaScript components.
