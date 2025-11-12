# CallRail Login Config

OpenBullet2 configuration for https://app.callrail.com/login

## Input Format
- USER: Email address
- PASS: Password

## Authentication Flow
1. Accesses the login page at `/login`
2. Extracts CSRF token from the page (tries multiple extraction methods)
3. Performs POST request to `/users/sign_in` with credentials and CSRF token
4. Validates authentication response

## Features
- CSRF token extraction (multiple fallback methods)
- Standard form-based authentication
- Session cookie handling
- Comprehensive error detection

## Status Detection
- SUCCESS: 
  - Response contains dashboard or accounts page indicators
  - Redirect to `/dashboard` or `/accounts`
  - Presence of "Sign out" or "logout" links
  - HTTP status codes 200 or 302
- FAIL: 
  - Invalid email or password messages
  - Authentication failed messages
  - Error alerts in response
  - HTTP status codes 401, 403, 422

## Notes
- This config uses standard Rails-based authentication
- CSRF token is required for successful authentication
- Cookies are automatically handled by the HTTP client
- The site may use JavaScript for some functionality, but core login is form-based
