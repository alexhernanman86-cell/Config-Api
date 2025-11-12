# CallRail Login Config

OpenBullet2 configuration for https://app.callrail.com/login

## Input Format
- USER: Email address
- PASS: Password

## Authentication Flow
1. Accesses the login page at `/login`
2. Extracts CSRF token (authenticity_token) from the page
3. Performs POST request to `/users/sign_in` with credentials
4. Validates authentication response

## Features
- CSRF token extraction
- Standard form-based authentication
- Comprehensive error detection
- Success detection based on redirects and page content

## Status Detection
- SUCCESS: 
  - Response contains "dashboard" or "accounts"
  - Redirect to dashboard or accounts page
  - HTTP status codes 200 or 302
  - Page contains "CallRail" branding
- FAIL: 
  - Error messages in response ("Invalid email or password", "incorrect email or password")
  - Login page still present after request
  - HTTP status codes 401, 403, 422

## Notes
- This config uses standard Rails form authentication
- CSRF token is required for successful authentication
- Cookies are automatically handled by the HTTP client
- User-agent headers are set to mimic a modern browser
