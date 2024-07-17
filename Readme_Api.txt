# **API Testing Project: Booking ID**

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

<img width="675" alt="Create Body" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Create_Booking.png">

<img width="675" alt="Create_prerequest script" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Pre_Request.png">

<img width="675" alt="Create_postrequest script" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Post_Request.png">

## **Get_Booking**
In Postman, a GET method is used to retrieve data from a server or API endpoint. It fetches information from the server without modifying anything, allowing users to view or read data such as user profiles, product listings, or any other resource available on the server.

<img width="675" alt="Get" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Get_Booking.png">

## **User_Auth(Token)**
In Postman, an Auth method is used to authenticate and authorize access to protected resources on a server or API endpoint. It allows users to include authentication tokens, API keys, or credentials in the request headers to verify their identity and gain access to restricted data or operations.

<img width="675" alt="Auth" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/User_Auth.png">

## **Update_Booking**
 Update method is used to send a PUT or PATCH request to a server to modify existing data or resources. It allows users to update specific fields or properties of a resource without replacing the entire resource, ensuring efficient and targeted updates to the server's data.
 
 <img width="675" alt="Updatebooking" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Update_Booking.png">

## **Verify_Update**
verify update request API" is used to confirm the successful update of a resource. It involves sending a PUT or PATCH request to modify the resource and then sending a subsequent GET request to ensure that the changes have been applied correctly on the server. This verification step helps ensure the accuracy and completion of the update process.

 <img width="675" alt="Verifyupdate" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Verify_Update.png">

## **Delete_Booking**
Delete method is used to send a request to a server or API endpoint to remove a specific resource. It allows users to delete data entries, records, or other resources from the server's database or storage, effectively removing them from the system.

<img width="675" alt="Delete" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Delete_Booking.png">

## **Verify_Delete**
Verify delete method" is typically used to confirm the successful deletion of a resource. It involves sending a DELETE request to remove the resource and then sending a subsequent GET request to ensure that the resource has been properly deleted from the server. This verification step helps ensure the accuracy and completion of the deletion process.

<img width="675" alt="Verifydelete" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Verify_Delete.png">

## **Postman_Environment**
Environment is used to store and manage variables that can be used across requests in a collection. It allows users to define values such as URLs, API keys, and authentication tokens once and use them dynamically in multiple requests, making it easier to manage and maintain API tests and configurations.

<img width="675" alt="Environment" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Postman_Environment.png">

## **Newman_Report**
Newman report" feature is used to generate detailed test reports for API collections run using the Newman command-line tool. It provides a summary of test results, including pass/fail statuses, response times, and error details, allowing users to analyze and share test results with team members or stakeholders.

<img width="675" alt="Newman_Report" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Newman_Summery_Report.png">

<img width="675" alt="Newman_Report2" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Postman_Report.png">

## **Newman_RunCommand**
Newman Run Command is used to execute API collections from the command line using the Newman tool. It allows users to automate the execution of tests, run them in CMD pipelines, and generate detailed reports, enhancing the efficiency and scalability of API testing processes.

<img width="675" alt="Newman_RunComand" src="https://github.com/Anik16298/Booking_API/blob/907ced4acdaad7f80325023b7fceaf143cec5c98/Screen_Shot/Newman_Command.png">