# NY.gov Login Config

OpenBullet2 configuration for https://my.ny.gov/LoginV4/login.xhtml

## Input Format
- USER: Username/Email
- PASS: Password

## Authentication Flow
1. Accesses the login page at `https://my.ny.gov/LoginV4/login.xhtml`
2. Extracts JSF ViewState token from the login form (required for JSF-based forms)
3. Extracts form ID if needed
4. Submits login credentials via POST request with JSF form parameters
5. Verifies authentication status from response

## Features
- JSF (JavaServer Faces) form handling
- ViewState token extraction and submission
- Comprehensive error detection
- Success pattern matching

## Status Detection
- SUCCESS: 
  - Response contains welcome/dashboard/account indicators
  - Logout option present (indicates successful login)
  - Redirect detected
  - HTTP status code 200
- FAIL: 
  - Error messages in response
  - "Invalid username or password" messages
  - "Login failed" or "Authentication failed" messages
  - Still on login page (login.xhtml in response)
  - HTTP status codes 400, 401, 403

## Notes
- This config handles JSF-based authentication forms
- ViewState token is required for form submission
- The site uses JavaServer Faces framework
- Proper user-agent and headers are required
- Cookies are automatically handled by the HTTP client
- May require additional adjustments based on actual form field names
