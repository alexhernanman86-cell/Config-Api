# BlueBetz Login Config

OpenBullet2 configuration for https://bluebetz.net/home

## Input Format
- USER: Email/Username
- PASS: Password

## Authentication Flow
1. Accesses the home page at `/home` to retrieve the login form
2. Extracts CSRF token from the page (if present)
3. Extracts login form action URL
4. Performs POST request to login endpoint with credentials
5. Validates response for success/failure indicators

## Features
- CSRF token extraction and handling
- Dynamic login URL detection
- Form-based authentication
- Comprehensive error detection
- Success indicators for dashboard/account pages

## Status Detection
- SUCCESS: 
  - Response contains dashboard, account, balance, or deposit keywords
  - Redirect to `/dashboard` or `/home` after login
  - HTTP status codes 200 or 302
  - Logout button present (indicates authenticated state)
- FAIL: 
  - Error messages in response (Invalid credentials, authentication failed, etc.)
  - HTTP status codes 400, 401, 403, 422
  - Generic error keywords

## Notes
- This config assumes standard form-based authentication
- CSRF token handling is included for Laravel/PHP-based sites
- The config will automatically detect the login endpoint from the form action
- Cookies are automatically handled by the HTTP client
- Adjust the success/fail keywords based on actual site responses
