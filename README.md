# 🛡️ API Testing - Cypress Heroes Case Study

This repository contains the API testing suite developed for the **Cypress Heroes** application. The primary goal was to isolate the backend layer (NestJS + Prisma) and validate business logic, JWT authentication flows, and data persistence independently of the frontend UI.

## 🧠 Technical Challenges & Troubleshooting

This project highlights deep-dive analysis and resolution of common API integration hurdles:

### 1. JWT Authentication & Payload Mismatch (401 Unauthorized)
While attempting to log in, I identified a discrepancy between the frontend label ("Email") and the backend's expected Data Transfer Object (DTO).
- **Discovery:** Through network traffic inspection, I validated that the server required the `username` key for authentication.
- **Solution:** Configured a `Post-response` script in Postman to automatically capture the `access_token` and update environment variables for seamless testing.

### 2. Handling 500 Internal Server Errors (Logic Layer)
Identified a processing failure when attempting to create new resources.
- **Debugging:** Inspected the NestJS server logs and identified a `TypeError` related to an undefined `.map()` function.
- **Action:** Refactored the JSON payload from a simple String to an **Array of Objects**, satisfying the service-level logic.

### 3. Data Integrity & Schema Validation (Prisma ORM)
Encountered a strict type validation error (`Provided String, expected Int`).
- **Analysis:** The API utilizes strong typing for database relationships (Prisma). Sending a power's name caused a schema mismatch.
- **Resolution:** Performed a `GET /powers` request to map the correct Integer IDs and updated the POST payload accordingly, resulting in a successful **201 Created** status.

## 🛠️ Tech Stack
* **Testing Tool:** Postman (Manual & Automated Scripts)
* **Backend Framework:** NestJS (Node.js)
* **ORM:** Prisma
* **Authentication:** JWT (Bearer Token)

## 🚀 How to Run These Tests
1. Import `test Heroes API.postman_collection.json` and `test Herores.postman_environment.json` into Postman.
2. Ensure the local backend server is running at `http://localhost:3001`.
3. Execute the **Login** request first; the `access_token` will be automatically updated via script.
4. Proceed to test the **Create** and **Delete** hero flows to validate the full CRUD cycle.
