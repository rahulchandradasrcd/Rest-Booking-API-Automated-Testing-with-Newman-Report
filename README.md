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
     * Open Postman.
     * Click on the Import button.
     * Select the file from the repository.
4. Import the Postman environment:
     * In Postman, click on the gear icon in the top right corner.
     * Select Import and choose the file.
5. Newman and Report Installation Process:
     * Newman Install Command:
     ```
     npm install -g newman
     ```
    
     * Newman Html Report Install Command:
 
     ```
     npm install -g newman-reporter-htmlextra
     ```
## Usage
1. Select Environment:
     * In Postman, select the appropriate environment (e.g., Development, Production) from the top-right dropdown.
2. Run Collection:
     * Select the imported collection from the Collections sidebar.
     * Click on the Runner button to open the collection runner.
     * Select the desired environment.
     * Click Start Test to run the collection.
3. View Results:
     * Once the tests are complete, view the results in the Runner tab.
     * Detailed test results can be viewed for each request.
## Testing
### Test Case Scenarios:
####  1. Create New Booking
##### Request URL: https://restful-booker.herokuapp.com/booking/
##### Request Method: POST
##### Pre-request Script:
    
```
var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
pm.environment.set("firstname", firstname)
//console.log(firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
pm.environment.set("lastname", lastname)

var totalprice = pm.variables.replaceIn("{{$randomInt}}")
pm.environment.set("totalprice", totalprice)

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
pm.environment.set("depositpaid", depositpaid)

const moment = require("moment")
const today = moment()

pm.environment.set("checkin", today.format("YYYY-MM-DD"))
//pm.environment.set("checkin", today.subtract(5, 'd').format("YYYY-MM-DD"))
pm.environment.set("checkout", today.add(7, 'd').format("YYYY-MM-DD"))

var additionalneeds = pm.variables.replaceIn("{{$randomProduct}}")
pm.environment.set("additionalneeds", additionalneeds)
```
##### Post-response Script:

```
//----------save bookingid an environment--------------------
var jsonData = pm.response.json()
pm.environment.set("id", jsonData.bookingid)

//---------------Status Code------------------
var status = pm.response.code
if(status == 200){
    pm.test("status code is 200 successfully Booked", function(){
        pm.response.to.have.status(200);
    });
}else if(status == 400){
    pm.test("Status code is 400 bad request", function(){
        pm.response.to.have.status(400);
    });
}else if (status == 401){
    pm.test("status code is 401 unauthorized", function(){
        pm.response.to.have.status(401);
    });
}else if (status == 403){
    pm.test("status code is 403 Forbidden", function(){
        pm.response.to.have.status(403);
    });
}else if (status == 404){
    pm.test("status code is 404 Not Found", function(){
        pm.response.to.have.status(404);
    });
}else if (status == 405){
    pm.test("status code is 405 Method not Allowed", function(){
        pm.response.to.have.status(405);
    });
}else if (status == 500){
    pm.test("status code is 500 Internal Server Error", function(){
        pm.response.to.have.status(500);
    });
}else if (status == 501){
    pm.test("status code is 501 Not Implemented", function(){
        pm.response.to.have.status(501);
    });
}else if (status == 502){
    pm.test("status code is 502 Bad Gateway", function(){
        pm.response.to.have.status(502);
    });
}else if (status == 503){
    pm.test("status code is 503 Service unavailable", function(){
        pm.response.to.have.status(503);
    });
}else{
    pm.test("Something Went Wrong.....")
}
```

##### Request Body:

 ```
{
	"firstname" : "{{firstname}}",
	"lastname" : "{{lastname}}",
	"totalprice" : "{{totalprice}}",
	"depositpaid" : "{{depositpaid}}",
	"bookingdates" : {
    	"checkin" : "{{checkin}}",
    	"checkout" : "{{checkout}}"
	},
	"additionalneeds" : "{{additionalneeds}}"
}
```
##### Response Body:

 ```
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
```
##### 2. Get Booking Details By ID
##### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
##### Request Method: GET
##### Response Body:
```
{
    "firstname": "Mozelle",
    "lastname": "Wilderman",
    "totalprice": 533,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2024-09-17",
        "checkout": "2024-09-24"
    },
    "additionalneeds": "Chips"
}
```
##### Post-response Script: 

```
var getdata = pm.response.json()

var status = pm.response.code
if(status == 200){
    pm.test("booking id validation", function(){
    pm.expect(getdata.bookingid).to.eql(pm.environment.get("bookingid"))
} )

pm.test("firstname validation", function(){
    pm.expect(getdata.firstname).to.eql(pm.environment.get("firstname"))
})

pm.test("lastname validation", function(){
    pm.expect(getdata.lastname).to.eql(pm.environment.get("lastname"))
})

pm.test("totalprice validation", function(){
    pm.expect(getdata.totalprice.toString()).to.eql(pm.environment.get("totalprice"))
})

pm.test("depositpaid validation", function(){
    pm.expect(getdata.depositpaid.toString()).to.eql(pm.environment.get("depositpaid"))
})

pm.test("checkin validation", function(){
    pm.expect(getdata.bookingdates.checkin).to.eql(pm.environment.get("checkin"))
})

pm.test("checkout validation", function(){
    pm.expect(getdata.bookingdates.checkout).to.eql(pm.environment.get("checkout"))
})

pm.test("additionalneeds validation", function(){
    pm.expect(getdata.additionalneeds).to.eql(pm.environment.get("additionalneeds"))
})

}else if(status == 400){
    pm.test("Status code is 400 bad request", function(){
        pm.response.to.have.status(400);
    });
}else if (status == 401){
    pm.test("status code is 401 unauthorized", function(){
        pm.response.to.have.status(401);
    });
}else if (status == 403){
    pm.test("status code is 403 Forbidden", function(){
        pm.response.to.have.status(403);
    });
}else if (status == 404){
    pm.test("status code is 404 Not Found", function(){
        pm.response.to.have.status(404);
    });
}else if (status == 405){
    pm.test("status code is 405 Method not Allowed", function(){
        pm.response.to.have.status(405);
    });
}else if (status == 500){
    pm.test("status code is 500 Internal Server Error", function(){
        pm.response.to.have.status(500);
    });
}else if (status == 501){
    pm.test("status code is 501 Not Implemented", function(){
        pm.response.to.have.status(501);
    });
}else if (status == 502){
    pm.test("status code is 502 Bad Gateway", function(){
        pm.response.to.have.status(502);
    });
}else if (status == 503){
    pm.test("status code is 503 Service unavailable", function(){
        pm.response.to.have.status(503);
    });
}else{
    pm.test("Something Went Wrong.....")
}
```

##### 3. Create A Token For Authentication.
##### Request URL: https://restful-booker.herokuapp.com/auth
##### Request Method: POST
##### Pre-request Script: None
##### Request Body:
```
{
   "username": "admin",
   "password": "password123"
}
```
##### Response Body:

```
{
   "token": "06eb798bf6f2caa"
}
```
##### Post-response Script: 
```
var token = pm.response.json()
pm.environment.set("token", token.token)

var status = pm.response.code
if(status == 200){
    pm.test("Status code is 200 token created", function(){
        pm.response.to.have.status(200);
    });
}else if(status == 400){
    pm.test("Status code is 400 bad request", function(){
        pm.response.to.have.status(400);
    });
}else if (status == 401){
    pm.test("status code is 401 unauthorized", function(){
        pm.response.to.have.status(401);
    });
}else if (status == 403){
    pm.test("status code is 403 Forbidden", function(){
        pm.response.to.have.status(403);
    });
}else if (status == 404){
    pm.test("status code is 404 Not Found", function(){
        pm.response.to.have.status(404);
    });
}else if (status == 405){
    pm.test("status code is 405 Method not Allowed", function(){
        pm.response.to.have.status(405);
    });
}else if (status == 500){
    pm.test("status code is 500 Internal Server Error", function(){
        pm.response.to.have.status(500);
    });
}else if (status == 501){
    pm.test("status code is 501 Not Implemented", function(){
        pm.response.to.have.status(501);
    });
}else if (status == 502){
    pm.test("status code is 502 Bad Gateway", function(){
        pm.response.to.have.status(502);
    });
}else if (status == 503){
    pm.test("status code is 503 Service unavailable", function(){
        pm.response.to.have.status(503);
    });
}else{
    pm.test("Something Went Wrong.....")
}
```

##### 4. Update the Booking Details
##### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
##### Request Method: PUT
##### Pre-request Script:
```
var firstname = pm.variables.replaceIn("{{$randomFirstName}}")
pm.environment.set("firstname", firstname)
//console.log(firstname)

var lastname = pm.variables.replaceIn("{{$randomLastName}}")
pm.environment.set("lastname", lastname)

var totalprice = pm.variables.replaceIn("{{$randomInt}}")
pm.environment.set("totalprice", totalprice)

var depositpaid = pm.variables.replaceIn("{{$randomBoolean}}")
pm.environment.set("depositpaid", depositpaid)

const moment = require("moment")
const today = moment()

pm.environment.set("checkin", today.format("YYYY-MM-DD"))
//pm.environment.set("checkin", today.subtract(5, 'd').format("YYYY-MM-DD"))
pm.environment.set("checkout", today.add(7, 'd').format("YYYY-MM-DD"))

var additionalneeds = pm.variables.replaceIn("{{$randomProduct}}")
pm.environment.set("additionalneeds", additionalneeds)
```
##### Post-response Script:

```
var status = pm.response.code
if(status == 200){
    pm.test("status code is 200 successfully Updated", function(){
        pm.response.to.have.status(200);
    });
}else if(status == 400){
    pm.test("Status code is 400 bad request", function(){
        pm.response.to.have.status(400);
    });
}else if (status == 401){
    pm.test("status code is 401 unauthorized", function(){
        pm.response.to.have.status(401);
    });
}else if (status == 403){
    pm.test("status code is 403 Forbidden", function(){
        pm.response.to.have.status(403);
    });
}else if (status == 404){
    pm.test("status code is 404 Not Found", function(){
        pm.response.to.have.status(404);
    });
}else if (status == 405){
    pm.test("status code is 405 Method not Allowed", function(){
        pm.response.to.have.status(405);
    });
}else if (status == 500){
    pm.test("status code is 500 Internal Server Error", function(){
        pm.response.to.have.status(500);
    });
}else if (status == 501){
    pm.test("status code is 501 Not Implemented", function(){
        pm.response.to.have.status(501);
    });
}else if (status == 502){
    pm.test("status code is 502 Bad Gateway", function(){
        pm.response.to.have.status(502);
    });
}else if (status == 503){
    pm.test("status code is 503 Service unavailable", function(){
        pm.response.to.have.status(503);
    });
}else{
    pm.test("Something Went Wrong.....")
}
```
##### Request Body:

 ```
{
	"firstname" : "{{firstname}}",
	"lastname" : "{{lastname}}",
	"totalprice" : "{{totalprice}}",
	"depositpaid" : "{{depositpaid}}",
	"bookingdates" : {
    	"checkin" : "{{checkin}}",
    	"checkout" : "{{checkout}}"
	},
	"additionalneeds" : "{{additionalneeds}}"
}
```
##### Response Body:

 ```
{
	"firstname" : "{{firstname}}",
	"lastname" : "{{lastname}}",
	"totalprice" : "{{totalprice}}",
	"depositpaid" : "{{depositpaid}}",
	"bookingdates" : {
    	"checkin" : "{{checkin}}",
    	"checkout" : "{{checkout}}"
	},
	"additionalneeds" : "{{additionalneeds}}"
}
```
##### 5. Delete Booking Record
##### Request URL: https://restful-booker.herokuapp.com/booking/bookingid
##### Request Method: DELETE
##### Response Body: None
##### Post-response Script:

```
var status = pm.response.code
if(status == 200){
    pm.test("Status code is 200 Booking cannot delete successfully", function(){
        pm.response.to.have.status(200);
    });
}else if(status == 201){
    pm.test("Status code is 201 Booking Deleted successfully", function(){
        pm.response.to.have.status(201);
    });
}else if(status == 400){
    pm.test("Status code is 400 bad request", function(){
        pm.response.to.have.status(400);
    });
}else if (status == 401){
    pm.test("status code is 401 unauthorized", function(){
        pm.response.to.have.status(401);
    });
}else if (status == 403){
    pm.test("status code is 403 Forbidden", function(){
        pm.response.to.have.status(403);
    });
}else if (status == 404){
    pm.test("status code is 404 Not Found", function(){
        pm.response.to.have.status(404);
    });
}else if (status == 405){
    pm.test("status code is 405 Method not Allowed", function(){
        pm.response.to.have.status(405);
    });
}else if (status == 500){
    pm.test("status code is 500 Internal Server Error", function(){
        pm.response.to.have.status(500);
    });
}else if (status == 501){
    pm.test("status code is 501 Not Implemented", function(){
        pm.response.to.have.status(501);
    });
}else if (status == 502){
    pm.test("status code is 502 Bad Gateway", function(){
        pm.response.to.have.status(502);
    });
}else if (status == 503){
    pm.test("status code is 503 Service unavailable", function(){
        pm.response.to.have.status(503);
    });
}else{
    pm.test("Something Went Wrong.....")
}
```

## Run Command:
##### Run Command for Console:
```
newman run Ebrahim_Hossain_SQA.postman_collection.json -e Ebrahim_Hossain_SQA.postman_environment.json
``` 
##### Run Command for Report:
```
newman run Ebrahim_Hossain_SQA.postman_collection.json -e Ebrahim_Hossain_SQA.postman_environment.json -r cli,htmlextra
```
##### Newman Report Summary:
Note: 1 Failed Test for postman random variable error where depositpaid varriable some times it work properly and some time it's get error.
![Screenshot 2024-09-17 123118](https://github.com/user-attachments/assets/45b3ccbe-019c-4982-963e-06cd99210571)
![Screenshot 2024-09-17 123136](https://github.com/user-attachments/assets/a4ceffca-ddfa-4f7a-9f0e-ce44bb342140)
![Screenshot 2024-09-17 123156](https://github.com/user-attachments/assets/0d890604-90b3-4dd4-a21c-6aedb5dcbd18)
![Screenshot 2024-09-17 123215](https://github.com/user-attachments/assets/a7a00615-4992-43d2-a752-741fa72d52c0)







