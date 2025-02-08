# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the code attempts to parse a user ID from the request parameters as an integer without checking if it's a valid number. This can lead to unexpected errors and application crashes.

## Bug Description
The `bug.js` file contains an Express.js route handler that fetches a user based on their ID.  The handler attempts to parse the ID from the request parameters using `parseInt()`, but it doesn't handle cases where the ID is not a valid integer.  If the ID is not a number (e.g., a string or null), `parseInt()` will return `NaN`, causing the subsequent `find()` operation to fail silently or throw an error, depending on the specific implementation of the `users` array.

## Bug Solution
The `bugSolution.js` file demonstrates the corrected route handler.  It adds input validation to ensure that the user ID is a valid integer before attempting to fetch the user.  This prevents unexpected errors and makes the application more robust.

## How to reproduce

1. Clone this repository.
2. Install dependencies: `npm install express`
3. Run `bug.js` and send a request with an invalid user ID (e.g., a string or null) to the `/users/:id` route.  Observe the error.
4. Run `bugSolution.js` and send the same request.  Observe that the application correctly handles the invalid input.