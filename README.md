# medx-pharmacy
💊 MedixCare-Pharmacy – Intelligent Digital Pharmacy Platform

A microservices-based full-stack pharmacy ordering system built using Spring Boot (Microservices) and React + Redux, designed to provide secure, compliant, and intelligent medicine ordering.

This platform goes beyond traditional e-pharmacy systems by integrating:
- 🧠 Smart Prescription Risk Checker
- 🚑 Emergency Priority Mode
- 📊 Real-time Inventory & Analytics
- 🔐 Secure JWT-based Authentication

--------------------------------------------------------
🚀 Problem Statement

Enable customers to:
- Browse medicines and healthcare products
- Upload prescriptions where required
- Place secure and efficient medicine orders
- Ensure prescription validation before order placement
- Automatically update inventory on confirmed orders
- Generate summaries and insights for operations

--------------------------------------------------------
🏗 High-Level Architecture

🔷 Frontend
- React
- Redux Toolkit
- Axios
- Role-based UI (User / Admin)

🔷 Backend (Spring Boot Microservices)

Service             | Responsibility
------------------ | ----------------
API Gateway         | Routing, Rate Limiting, JWT Validation
Auth Service        | Registration, Login, JWT, Role Management
Medicine Service    | Medicine catalog, stock management
Order Service       | Order placement, Risk Engine, Emergency Mode
(Optional) Analytics| Revenue & summary reporting

Communication:
- REST APIs
- JWT-based authentication
- Service-to-service REST calls

--------------------------------------------------------
🧠 Unique Selling Propositions (USP)

1️⃣ Smart Prescription Risk Checker
- Detects overdose risk (quantity > max daily dose)
- Drug interaction conflicts
- Allergy conflicts
- Duplicate medication detection
- If risk detected: risk_flag = true, Admin review required, Order blocked if severe
Benefits:
✔ Patient Safety
✔ Regulatory Compliance
✔ Reduced Medication Errors

2️⃣ Emergency Priority Mode
- Users can mark an order as Emergency
- Priority level set to HIGH
- Admin dashboard highlights emergency orders
- Faster processing simulation
Benefits:
✔ Faster response to urgent medical needs
✔ Operational prioritization

--------------------------------------------------------
🗄 Database Design

Auth Service (`users`)
Field          | Type
-------------- | ----------------
id             | BIGINT
name           | VARCHAR
email          | VARCHAR (unique)
password       | VARCHAR
role           | ENUM(USER, ADMIN)
allergies      | VARCHAR
created_at     | TIMESTAMP

Medicine Service (`medicines`)
Field               | Type
------------------ | ----------------
id                  | BIGINT
name                | VARCHAR
category            | VARCHAR
dosage              | VARCHAR
packaging           | VARCHAR
price               | DECIMAL
stock               | INT
prescription_required| BOOLEAN
max_daily_dose      | INT
risky_with          | VARCHAR
allergy_trigger     | VARCHAR
created_at          | TIMESTAMP

Order Service (`orders`)
Field           | Type
--------------- | ----------------
id              | BIGINT
user_id         | BIGINT
total_amount    | DECIMAL
status          | ENUM(PENDING, APPROVED, REJECTED, DELIVERED, CANCELLED)
emergency       | BOOLEAN
priority_level  | ENUM(NORMAL, HIGH)
risk_flag       | BOOLEAN
risk_message    | VARCHAR
created_at      | TIMESTAMP

Order Items (`order_items`)
Field       | Type
------------| ----------------
id          | BIGINT
order_id    | BIGINT
medicine_id | BIGINT
quantity    | INT
price       | DECIMAL

Prescriptions (`prescriptions`)
Field       | Type
------------| ----------------
id          | BIGINT
order_id    | BIGINT
image_path  | VARCHAR
status      | ENUM(PENDING, APPROVED, REJECTED)

--------------------------------------------------------
🔐 Security
- JWT Authentication
- Role-Based Authorization (USER / ADMIN)
- API Gateway routing
- Rate limiting
- Swagger-secured endpoints

--------------------------------------------------------
📦 Core Features
✔ Browse medicines
✔ Category filtering
✔ Prescription upload & validation
✔ Smart risk detection
✔ Emergency prioritization
✔ Automatic inventory deduction
✔ Admin approval dashboard
✔ Order status tracking
✔ Revenue & order summary APIs
✔ Swagger API documentation
✔ Postman-tested endpoints

--------------------------------------------------------
📊 Admin Dashboard Capabilities
- View all orders
- Highlight emergency orders
- View risk-flagged prescriptions
- Approve / Reject prescriptions
- Low-stock alerts
- Daily revenue summary

--------------------------------------------------------
🛠 Technology Stack

Backend:
- Java 17, Spring Boot, Spring Security
- Spring Cloud Gateway
- JPA / Hibernate, MySQL / H2
- Swagger (OpenAPI)

Frontend:
- React, Redux Toolkit, Axios
- Tailwind / MUI (optional)

DevOps:
- GitHub (Version Control)
- Postman (API Testing)

--------------------------------------------------------
🔁 Order Processing Flow
1. User logs in (JWT issued)
2. User browses medicines
3. Adds items to cart
4. Uploads prescription (if required)
5. Selects emergency mode (optional)

Order Service:
- Validates stock
- Runs Risk Checker
- Flags if conflict found
- Admin reviews (if required)
- On approval: Inventory auto-updated, status updated, order summary recorded

--------------------------------------------------------
📈 Stretch Features (Optional)
- Email confirmation (Spring Mail)
- Order history & quick reorder
- Loyalty points
- Health packages
- Seasonal wellness offers

--------------------------------------------------------
🏆 Why MedixCare Stands Out
- Proactive prescription intelligence
- Emergency prioritization
- Safety-first order validation
- Operational analytics

Result: scalable, secure, and healthcare-compliant system

--------------------------------------------------------
👥 Team Contribution
Role                  | Responsibility
-------------------- | ----------------
Backend Developer     | Microservices & Business Logic
Security Engineer     | JWT & Gateway
Frontend Developer    | React UI & Redux
Analytics/Admin       | Dashboard & Reporting

--------------------------------------------------------
📂 Repository Structure
/api-gateway
/auth-service
/medicine-service
/order-service
/frontend

--------------------------------------------------------
📌 Future Enhancements
- AI-based prescription OCR
- Real-time delivery tracking
- Cloud storage integration
- CI/CD pipeline
