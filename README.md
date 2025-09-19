`<img width="500" height="500" alt="troopackLogo" src="https://github.com/user-attachments/assets/9334b678-a810-4615-a528-1ed058f839ce" />`

Troopack is a comprehensive subscription-based platform designed for managing customer relationships and support operations. It consists of a main website for user registration and subscription handling, integrated with a CRM system and real-time chat support. The platform enables users to subscribe, manage their CRM instances as owners, and invite operators or admins to collaborate on projects. Built with modern technologies, it emphasizes scalability, real-time interactions, and secure data management using containerized architecture.
Overview
Troopack provides a seamless experience for users to:

Register and activate subscriptions on the main website.
Access a dedicated CRM instance upon subscription activation.
Use real-time chat support for immediate assistance.
Invite team members (operators/admins) to specific projects via shareable links.

The system is architected around three Docker containers:

Main Website Container: Handles user registration, subscription payments, and initial CRM record creation.
CRM Container: Manages CRM functionalities, including user authentication, project management, and admin/operator roles.
Shared Database Container: Stores all data, ensuring consistency across the main website and CRM.

Real-time events, such as notifications and chat updates, are powered by WebSockets for efficient, low-latency communication.
All code in this repository is written in English for clarity and maintainability.
Tech Stack

Backend: Go (Golang) for both the main website server and CRM server. Go is chosen for its performance, concurrency support, and simplicity in handling HTTP requests, WebSockets, and database interactions.
Frontend:

Main Website: React with Vite for fast development and optimized builds.
CRM: React with TypeScript for type-safe development and enhanced code quality.


Chat Support: Implemented in JavaScript, running on the same server as the CRM for integrated real-time functionality.
Database: Shared database (e.g., PostgreSQL or similar, containerized) to store user records, subscriptions, CRM data, and project details.
Real-Time Communication: WebSockets for handling live events like chat messages, notifications, and updates.
Containerization: Docker with three containers for isolation, scalability, and easy deployment.
Other: Email integration for sending generated passwords and notifications.

How It Works
User Registration and Subscription

Users visit the main website at https://troopack.com/ and register an account.
Upon successful subscription payment (handled securely on the Go backend), the server creates a new record in the shared database container.
A unique password is generated for the user's CRM access and sent via email.
This record is referenced by the CRM container, enabling the user to log in and manage their CRM instance.

CRM Access and Roles

Owner Access: If a user navigates to the CRM via the "Go to CRM" button on the main website, they are authenticated as the owner of their CRM instance. Owners have full control, including creating projects, managing data, and inviting team members.
Operator/Admin Access: Owners can generate invitation links for specific projects. When users access the CRM through these links, they log in with operator or admin privileges limited to the invited projects. This supports collaborative workflows, such as team-based support or project management.

Real-Time Features

Chat support is integrated into the CRM, allowing users (owners, operators, admins) to communicate in real-time.
WebSockets ensure that events like new messages, status updates, or subscription changes are propagated instantly without polling.

Security and Data Flow

Authentication is handled via generated passwords and session management on the Go servers.
Data consistency is maintained through the shared database, with containers communicating via internal networking.
Email notifications use secure protocols to deliver sensitive information like passwords.

<img width="682" height="448" alt="image" src="https://github.com/user-attachments/assets/708fd413-30d1-4b08-8f31-222c3d2bbcb2" />


Arrows represent data flow: Subscription creates DB record; CRM references DB for operations.
