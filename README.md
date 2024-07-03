# Assessment
Task 1: Discover Lendsqr Adjutor APIs and document detailed test scripts to be executed for the following functionalities:
Signup
Login
Retrieving your API keys

1. Test Case Signup: Successful Signup
Title: Successful Signup
Description:
Verify that a user can successfully sign up on the adjutor web application.
Pre-conditions
The adjutor web API should be up and running.
The email address to be used for registration should not already be associated with an existing account.
Test Data
Username: newuser@example.com
Password: Welcome@223
Full Name: Maureen Gbefa
Phone Number: +2347087922995
Test Steps
Open the adjutor web app.
Navigate to the signup screen.
Enter full name
Enter work email address in the email field.
Enter mobile number
Enter business name
Enter RC number 
Enter password
Click the "Continue" button.
Click on validate your account email
Click on setup your account
Expected Result
The system creates a new user account.
The user receives a Confirm your email address message.
Actual Result : User is redirected to login on the web app. Status: (Pass)
2. Test Case Signup: Unsuccessful Signup 
Title: Unsuccessful Signup
Description:
Verify that a user cannot create a new account on the adjutor web application with an already existing email address.
Pre-conditions
The adjutor web API should be up and running.
The email address to be used for registration should not already be associated with an existing account.
Test Data
Username: existinguser@example.com
Password: weak
Full Name: (empty)
Phone Number: invalidnumber
Test Steps
Open the Capital Cash app.
Navigate to the signup/registration screen.
Perform the following scenarios:
Scenario 1: Duplicate Email
Enter existinguser@test.com in the email field.
Enter ValidPass@1234 in the password field.
Enter Existing User in the full name field.
Enter +2347012345678 in the phone number field.
Click the "Signup" button.
Scenario 2: Weak Password
Enter newuser2@test.com in the email field.
Enter weak in the password field.
Enter New User in the full name field.
Enter +2347012345678 in the phone number field.
Click the "Signup" button.
Scenario 3: Missing Full Name
Enter newuser3@test.com in the email field.
Enter ValidPass@1234 in the password field.
Leave the full name field empty.
Enter +2347012345678 in the phone number field.
Click the "Signup" button.
Scenario 4: Invalid Phone Number
Enter newuser4@test.com in the email field.
Enter ValidPass@1234 in the password field.
Enter New User in the full name field.
Enter invalidnumber in the phone number field.
Click the "Signup" button.
Expected Result
Scenario 1: The system rejects the signup attempt and displays an error message indicating the email is already in use.
Scenario 2: The system rejects the signup attempt and displays an error message indicating the password is too weak.
Scenario 3: The system rejects the signup attempt and displays an error message indicating the full name is required.
Scenario 4: The system rejects the signup attempt and displays an error message indicating the phone number format is invalid.
No account is created in any scenario.
No authentication token is generated.
Actual Result: (Scenarios failed as expected)
Status: (Fail)















Test Case Login: Successful Login
Title: Successful Login
Description:
Verify that a user with valid credentials can successfully log into the adjutor web application.
Pre-conditions:
The user must be registered in the system with valid credentials.
The Authentication API should be up and running.
The user has access to the adjutor web application
Test Data:
Username: testuser@test.com
Password: Test@1234
Test Steps:
Open the Capital Cash app.
Navigate to the login screen.
Enter the username maureenutem@gmail.com in the username/email field.
Enter the password Welcome@223 in  the password field.
Click the "Login" button.
Enter the OTP sent to your email or the token from your authenticator app to validate your login.
User is redirected to the dashboard.
Expected Result:
The user is successfully logged into the app.
The user is redirected to the dashboard/home screen of the app.
Actual Result: The user is successfully logged into the app.
Status: (Pass)






Test Case: Failed Login
Title: Failed Login
Description:
Verify that a user with invalid credentials cannot log into the Capital Cash app using the Lendsqr Authentication API.

Pre-conditions:
The user must be registered in the system with valid credentials.
The Authentication API should be up and running.
The user has access to the Capital Cash app.

Test Data:
Username: maureenutem@gmail.com
Password: welcome@123

Test Steps:
Open the Capital Cash app.
Navigate to the login screen.
Enter the username maureenutem@gmail.com in the username/email field.
Enter the password “welcome@123” in the password field.
Click the "Login" button.
Expected Result:
The system does not authenticate the user.
An error message is displayed indicating that the login attempt was unsuccessful (“Incorrect login credentials").
The user remains on the login screen.
Actual Result: An error message is displayed indicating that the login attempt was unsuccessful (“Incorrect login credentials").
Status: (Fail)


Test Case: Retrieving API Keys
Title: Retrieving API Keys
Description:
Verify that an authenticated user can successfully retrieve API keys from the Lendsqr API platform.
Pre-conditions:
The user must be authenticated and authorized to access API keys.
The API endpoint for retrieving API keys should be up and running.
The user must have a valid access token.

Test Data:
Access Token: ValidAccessToken123
Test Steps:
On the dashboard, click on apps
Click on get started
Enter app name, description, webhook url and select services.
Click on create app.
App created successfully is displayed.
Expected Result:
The system returns a list of API keys associated with the authenticated user.
Actual Result: (Test failed)
Status: (Fail)

Screenshoot: https://monosnap.com/file/GXGnt0rJBgp0F7AtDAQyYqRySDmujn 

Title: Invalid Access Token and Unauthorized Access
Description:
Verify that the system correctly handles requests with an invalid access token and unauthorized access attempts when retrieving API keys.
Pre-conditions:
The API endpoint for retrieving API keys should be up and running.
The user attempting access should have an invalid or expired access token.
There should be scenarios where the user is authenticated but not authorized to access API keys.
Test Data:
Invalid Access Token: InvalidAccessToken123
Expired Access Token: ExpiredAccessToken123
Unauthorized User's Access Token: UnauthorizedUserToken123

Test Steps:
Scenario 1: Invalid Access Token
Send a GET request to the API endpoint for retrieving API keys.
Include the invalid access token in the request headers.
Scenario 2: Expired Access Token
Send a GET request to the API endpoint for retrieving API keys.
Include the expired access token in the request headers.
Scenario 3: Unauthorized Access
Send a GET request to the API endpoint for retrieving API keys.
Include the unauthorized user's access token in the request headers.

Expected Result:
Scenario 1: Invalid Access Token
The system returns a 401 Unauthorized status code.
An error message is displayed indicating the token is invalid or expired.
Scenario 2: Expired Access Token
The system returns a 401 Unauthorized status code.
An error message is displayed indicating the token is expired.
Scenario 3: Unauthorized Access
The system returns a 403 Forbidden status code.
An error message is displayed indicating the user does not have permission to access the API keys.
Actual Result: (Scenarios failed as expected)  
Status: (Fail)















Task 2
Authentication API Tests
Login API Test
Request:
Method: POST
URL: /api/auth/login
Headers: Content-Type: application/json
Body:
{
  "username": "testuser@test.com",
  "password": "Test@1234"
}
Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response has token", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("token");
});

Password Reset API Test
Request:
Method: POST
URL: /api/auth/reset-password
Headers: Content-Type: application/json
Body:
{
  "email": "testuser@test.com"
}
Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response message is correct", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.message).to.eql("Password reset link sent to email.");
});

Loan Application API Tests
Submit Loan Application API Test
Request:
Method: POST
URL: /api/loans/apply
Headers: Content-Type: application/json, Authorization: Bearer {{token}}
Body:
{
  "amount": 1000,
  "term": 12,
  "purpose": "Business Expansion"
}


Tests:
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});
pm.test("Response contains loan ID", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("loanId");
});

Check Loan Status API Test
Request:
Method: GET
URL: /api/loans/status/{{loanId}}
Headers: Authorization: Bearer {{token}} 
Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response contains loan status", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("status");
});

Payment Processing API Tests
Initiate Payment API Test
Request:
Method: POST
URL: /api/payments/initiate
Headers: Content-Type: application/json, Authorization: Bearer {{token}}
Body:
{
  "loanId": "{{loanId}}",
  "amount": 100
}

Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response contains payment ID", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("paymentId");
});

Verify Payment Status API Test
Request:
Method: GET
URL: /api/payments/status/{{paymentId}}
Headers: Authorization: Bearer {{token}} 
Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response contains payment status", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("status");
});




User Management API Tests
Register User API Test
Request:
Method: POST
URL: /api/auth/signup
Headers: Content-Type: application/json
Body:
{
  "username": "newuser@example.com",
  "password": "NewUser@1234",
  "fullName": "New User",
  "phoneNumber": "+1234567890"
}
Tests:
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});
pm.test("Response contains token", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData).to.have.property("token");
});






Update User Profile API Test
Request:
Method: PUT
URL: /api/user/profile
Headers: Content-Type: application/json, Authorization: Bearer {{token}}
Body:
{
  "fullName": "Updated User",
  "phoneNumber": "+0987654321"
}
Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response contains updated profile", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.fullName).to.eql("Updated User");
    pm.expect(jsonData.phoneNumber).to.eql("+0987654321");
});
















