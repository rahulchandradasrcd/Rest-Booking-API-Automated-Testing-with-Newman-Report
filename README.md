# Rest-Booking-API-Automated-Testing-with-Newman-Report
This repository showcases API testing for booking functionalities using Postman and Newman. The focus is on creating, retrieving, updating, and deleting bookings through specific API endpoints.
## **Testing Tools:**
**Postman:** Used for sending API requests, managing test collections, and inspecting responses.

**Newman:**  Utilized for running tests from the command line and generating reports in different formats (e.g., HTML, JSON).
## **Testing Coverage:**

#### **CRUD Operations:** The project encompasses tests for the following functionalities-

Create Booking (POST)

Get Booking (GET)

Token (POST)

Update Booking (PUT)

Checking After Update(GET)

Delete Booking(DELETE)

Checking After Delete Booking (GET)

Handle array-based data (example)

**Booking_Id_api_tests:** This file describes the API testing project.

**Postman_Collections:** This folder holds Postman collections for different testing scenarios.

**Newman_Report:** This folder contains Newman-generated test reports.
## **Create_Booking**
Create Booking is typically used to send a POST request to a server to create a new booking or reservation. This POST request includes the necessary data (such as Guest details, Price, Dates, Needs etc.) in the request body, allowing the server to process and create a new booking entry in its database.
