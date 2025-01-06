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
