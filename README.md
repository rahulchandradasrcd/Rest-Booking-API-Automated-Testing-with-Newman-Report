# Rest Booking API Testing with Postman Newman
This project demonstrates API testing using Postman, providing a collection of tests to validate various endpoints of the API.

## Features
* Tests for GET, POST, PUT, DELETE requests
* Collection of tests covering different API endpoints
* Environment setup for easy switching between environments
* Pre-request scripts for data setup
* Test scripts for assertions and validations
## API Documentation:
https://documenter.getpostman.com/view/13082503/2sA2xmUAJ1
## Technology used:
- Postman
- Newman
## Prerequisite:
- Node Js
- Newman
- Newman Html Report Library
## Installation
1. Postman: If you haven't already, [download and install Postman](https://www.postman.com/downloads/).
2. Clone the repository:

```
git clone https://github.com/rahulchandradasrcd/Rest-Booking-API-Automated-Testing-with-Newman-Report.git
```

3. Import the Postman collection:
Open Postman.
Click on the Import button.
Select the file from the repository.
Import the Postman environment:
In Postman, click on the gear icon in the top right corner.
Select Import and choose the file.
Newman and Report Installation Process:
Newman Install Command:
 npm install -g newman
Newman Html Report Install Command:
 npm install -g newman-reporter-htmlextra
Usage
Select Environment:
In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
Run Collection:
Select the imported collection from the Collections sidebar.
Click on the Runner button to open the collection runner.
Select the desired environment.
Click Start Test to run the collection.
View Results:
Once the tests are complete, view the results in the Runner tab.
Detailed test results can be viewed for each request.
Testing
Test Case Scenarios:
1. Create New Booking
Request URL: https://restful-booker.herokuapp.com/booking/
Request Method: POST
Pre-request Script:
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    pm.environment.set("firstName", firstName)
    console.log("First Name Value "+firstName)
    
    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("lastName", lastName)
    console.log("Last Name Value "+lastName)
    
    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    pm.environment.set("totalPrice", totalPrice)
    console.log(totalPrice)
    
    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)
    console.log(depositPaid)
    
    //Date
    const moment = require('moment')
    const today = moment()
    pm.environment.set("checkin", today.add(1,'d').format("YYYY-MM-DD"))
    pm.environment.set("checkout",today.add(5,'d').format("YYYY-MM-DD") )
    
    var additionalNeeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", additionalNeeds)
Request Body:

 {
     "firstname" : "{{firstName}}",
     "lastname" : "{{lastName}}",
     "totalprice" : {{totalPrice}},
     "depositpaid" : {{depositPaid}},
     "bookingdates" : {
   	  "checkin" : "{{checkin}}",
   	  "checkout" : "{{checkout}}"
     },
     "additionalneeds" : "{{additionalNeeds}}"
 }
Response Body:

 {
     "bookingid": 4334,
     "booking": {
         "firstname": "Joelle",
         "lastname": "Krajcik",
         "totalprice": 266,
         "depositpaid": true,
         "bookingdates": {
             "checkin": "2024-03-15",
             "checkout": "2024-03-20"
         },
         "additionalneeds": "monitor"
     }
 }
2. Get Booking Details By ID
Request URL: https://restful-booker.herokuapp.com/booking/bookingid
Request Method: GET
Response Body:
{
   "firstname": "D'angelo",
   "lastname": "Feeney",
   "totalprice": 757,
   "depositpaid": true,
   "bookingdates": {
       "checkin": "2024-03-15",
       "checkout": "2024-03-20"
   },
   "additionalneeds": "hard drive"
}
3. Create A Token For Authentication.
Request URL: https://restful-booker.herokuapp.com/auth
Request Method: POST
Pre-request Script: None
Request Body:
{
   "username": "admin",
   "password": "password123"
}
Response Body:

{
   "token": "06eb798bf6f2caa"
}
4. Update the Booking Details
Request URL: https://restful-booker.herokuapp.com/booking/bookingid
Request Method: PUT
Pre-request Script:
    var firstName = pm.variables.replaceIn("{{$randomFirstName}}")
    pm.environment.set("firstName", firstName)
    console.log("First Name Value "+firstName)
    
    var lastName = pm.variables.replaceIn("{{$randomLastName}}")
    pm.environment.set("lastName", lastName)
    console.log("Last Name Value "+lastName)
    
    var totalPrice = pm.variables.replaceIn("{{$randomInt}}")
    pm.environment.set("totalPrice", totalPrice)
    console.log(totalPrice)
    
    var depositPaid = pm.variables.replaceIn("{{$randomBoolean}}")
    pm.environment.set("depositPaid", depositPaid)
    console.log(depositPaid)
    
    //Date
    const moment = require('moment')
    const today = moment()
    pm.environment.set("checkin", today.add(1,'d').format("YYYY-MM-DD"))
    pm.environment.set("checkout",today.add(5,'d').format("YYYY-MM-DD") )
    
    var additionalNeeds = pm.variables.replaceIn("{{$randomNoun}}")
    pm.environment.set("additionalNeeds", additionalNeeds)
Request Body:

 {
     "firstname" : "{{firstName}}",
     "lastname" : "{{lastName}}",
     "totalprice" : {{totalPrice}},
     "depositpaid" : {{depositPaid}},
     "bookingdates" : {
   	  "checkin" : "{{checkin}}",
   	  "checkout" : "{{checkout}}"
     },
     "additionalneeds" : "{{additionalNeeds}}"
 }
Response Body:

 {
     "bookingid": 4334,
     "booking": {
         "firstname": "Joelle",
         "lastname": "Krajcik",
         "totalprice": 266,
         "depositpaid": true,
         "bookingdates": {
             "checkin": "2024-03-15",
             "checkout": "2024-03-20"
         },
         "additionalneeds": "monitor"
     }
 }
5. Delete Booking Record
Request URL: https://restful-booker.herokuapp.com/booking/bookingid
Request Method: DELETE
Response Body: None
Run Command:
Run Command for Console:
newman run Ebrahim_Hossain_SQA.postman_collection.json -e Ebrahim_Hossain_SQA.postman_environment.json 
Run Command for Report:
newman run Ebrahim_Hossain_SQA.postman_collection.json -e Ebrahim_Hossain_SQA.postman_environment.json -r cli,htmlextra
Newman Report Summary:
![Screenshot 2024-09-16 220650](https://github.com/user-attachments/assets/a501774e-6add-46ea-9287-76941458df65)
