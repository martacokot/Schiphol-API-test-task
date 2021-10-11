# Schiphol-API-test-task

**API Technical Test**

Using the following API https://developer.schiphol.nl/
1. Obtain an API Key to use in your code.
API key is stored as a collection variable api_key.
2. Access the API retrieve details of the following:
  a. All country / city combinations available as destinations from Schiphol. Sort by country ascending. Verify the results contain "city": "Sydney", "country":    "Australia"
    - Sorting is provided by passing the "+country" (%2Bcountry) parameter.
    - JavaScript test is added to verify if response contains city & country provided. 
  b. Get a list of all IATA codes for "country": "Australia" and return them with their destination city.
      i. If either an IATA code or Destination city is missing, report this as a failure.
3. Access the API and retrieve data for all flights leaving Schiphol today. Find and return
information about the IATA code for each flight, along with the destination and time of
departure. Verify there is an IATA code for each flight, if not return as a failure.
4. Attempt to call the API with an invalid API key – validate the response.
5. In each case ensure you are validating the responses returned from the APIs are correct.

Demonstrate test automation and the use of frameworks that will help with readability, maintainability, validation and reporting.

**Task Solution Overview**
---

To complete the described task I used [Postman App](https://postman.com/). Please import *SchipholTest.postman_collection.json* file into Postman for script analysis. Script is written in JavaScript.

**Task files include:**

*SchipholTest.postman_collection.json*

API key and App ID are stored as Collection Variables, therefore are available for all API requests within the collection. Tests script tab contains  response code validation test. In the Pre-request script tab are stored functions which are common for all API requests. Logic is required to collect and process data from paginated responses and use those in specific tests. Collection contains 3 API calls described in the task and tests for those. 
Each API request is being called using API Key Authorization, request params and headers are filled accordingly with Public Schiphol API Documentation. Tests and functions specific for each call to support test execution are kept in the Tests tab accordingly.


*Environment.postman_environment.json*

Environment file is empty but required for html report creation.


*SchipholTest.postman_test_run.json*

Contains test run results in json format


*HTML report*

File can be opened in a browser and will display results I got from local run. 

Report in html format can be produced using newman reporter. Please follow the steps:

Download NodeJS from the official site (https://nodejs.org/). 

check that NodeJS and npm were successfully installed by opening cmd and typing: 

node-v

npm -v

Newman is the collection runner that allows us to run and test a Postman Collection from the command line. To install type: 

npm install -g newman

Then install reporter:

npm install -g newman-reporter-html

npm install -g newman-reporter-htmlextra

Once the installation process is complete. Export the collection and environment from Postman and place it in the desired folder. 
Using Terminal, navigate to the folder containing exported files. Type:

*newman run SchipholTest.postman_collection.json -e Environment.postman_environment.json -n 1 -r htmlextra*

Keep in mind that -n 1 refers to the number of iterations you want.







