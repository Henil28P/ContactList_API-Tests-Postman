# ContactList_API-Tests-Postman

A Postman-based API Automation Software Testing project for To-Do List Node.js Web Application to test its functionalities of features and user interaction components on the web of managing contact list.

# Resources and tools used for this project:

1. Postman: https://postman.com/downloads (free version)
2. Check to see if Node is installed: `$ node --version`
3. Node.js and npm: download Node.js from `https://nodejs.org/` and check npm installatino by `$ npm --version`
4. Newman: `$ npm install -g newman` --> Newman is a command-line runner that runs the Postman tests.

# Application under API Tests:

- Contact List API: https://thinking-tester-contact-list.herokuapp.com/
- Allows users to add, edit, and deletee contacts, like they would in an address book.

# Postman Terminology

1. Collections - all the requests and assertions for an API; the top-level folder
2. Folders - a group of requests and assertions that reside in a collection. It's even possible to create nested folders.
3. Bearer Token (Auth type) -

# JSON Web Tokens (JWTs)

- APIs allow us to make requests directly to a server or a data store without having to go through UI. But software creators need to make sure that those APIs are secure.
- The most common way to secure APIs is through a JSON Web Tokens (JWTs) this token is generated through a POST request.
- When a valid username and password are sent in the request, a JWT is generated.
- The JWT can then be used in all requests to the API to interact with the app.

# Requests to the Contact List API

1. `GET` request: returns list of all contacts
2. `GET/{contactId}` request: returns 1 specific contact
3. `POST` request: adds a new contact
4. `PUT/{contactId}` request: updates the data for an existing specific contact
5. `DELETE/{contactId}` request: deletes a specific contact

- Postman documentation: https://documenter.getpostman.com/view/4012288/2s8YRiKDbu

# 5 negative testing scenarios

1. A request is sent with a missing authentication token

- We can generate a 401 response by using an invalid token or no token at all.

2. A record is not found

- `404 Not Found` response from server means that the contact that we're looking for (specified by the unique ID in the API URL), does not exist.
- Example: doing a `GET` request on a contact that does not exist results in a 404 error.
- A 404 is a "Not Found" error, so trying to GET a contact that does not exist would return the 404 status code.

3. A request is sent with missing required information

- Leave mandatory firstName field empty in the raw JSON-formatted Request Body of POST and server will give 400 Bad Request response with the error message "firstName is required".

4. A value is sent with too many characters
5. A value is sent that is not in the correct format

# Environments and Environment variables

- Environment: A group of variables in Postman
- Initial Value: The variable value that is saved in the environment file.
- Current Value: A temporary variable value.
- Note: To use Environment variables in the request bodies in Postman, use `{{variable_name}}`

# Saving Environment Variables

- Variables can be programmatically saved using the `Tests` tab of the Postman request (can use Javascript to save a value that was returned). Once the variable has been saved, it can be used in all other requests.
- Suggestions:

1. Save contactId for reuse
2. Save token for reuse

- The contactId variable can also be used in the Update Contact request and the Delete Contact request.

Other variables that could be used in the add contact request are:

- firstName
- lastName
- birthdate
- email
- phone
- country
- stateProvince
- postalCode
- city

# Turning Postman requests into actual tests

- Turn Postman requests into actual tests by adding assertion scripts to the requests.

# Type 1 - Status Type Assertions

- This type of assertion validates that the status code we receive as a response to a request is the one we are expecting.
- Typical status type assertions

1. `200`: The request was completed as expected.
2. `201`: A new resource was created.
3. `401`: The user is not authenticated.
4. `404`: The resource was not found.

# Type 2 - Body Assertions

- A body assertion verifies that the body of the response contains the text that we were expecting.

1. `Response body: Contains string`: The text is in the body of the response, but may not be the entire response. This assertion uses "to include".
2. `Response body: Is equal to a string`: The text matches the entire body of the response. This assertion uses "to have".

- Often use portion assertions when you are asserting on an error message. However, if a response body is very short, just a few words, then usually assert on the whole body.

# Type 3 - Header and Response Time Assertion

- Helpful for security and performance testing
- Add an assertion to test the header values in our response - `Response Headers`: Information passed with an API response that includes additional information about the response, such as the format of the response or any security controls.
- For this Postman project, an assertion that will be added will verify that we are getting JSON back in the response and not some other Content-Type.
- Some security headers assertions for API include: X-XSS to protect against cross-side scripting attacks.

2. Add an assertion to make sure that responses are coming back within a reasonable time - `Response Time`: The time it takes for a request to reach the server and return a response.

- You can also add a common assertion test scripts in Postman for all requests in a specific collection or folder by going into Edit and selecting any performance related test such as `Response Time is less than 200ms` and this assertion test will be applicable for all requests under that collection or folder.

# Debugging with the Postman Console

- Postman console can be helpful in debugging our test assertions and see why certain tests are failing.
- Whenever you have requests not working as you expect them to or your assertions are failing, use the Postman console to help you debug.
- Some things to look for in the Postman console:

1. Check that your HTTP verb is correct (GET, POST, PUT, DELETE)
2. Check that the authentication token is sent
3. Check that the URL of the request is correct
4. Check that all variables have populated correctly in the request (those variables could be in the URL or the body of the request).
