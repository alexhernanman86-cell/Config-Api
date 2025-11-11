# NY.gov Login Config

OpenBullet2 configuration for https://my.ny.gov/LoginV4/login.xhtml

## Input Format
- USER: Username/Email
- PASS: Password

## Authentication Flow
1. Accesses the login page at `/LoginV4/login.xhtml`
2. Extracts JSF ViewState token from the login form
3. Extracts form ID for proper form submission
4. Submits login credentials via POST request with ViewState
5. Handles JSF/AJAX form submission pattern

## Features
- JSF (JavaServer Faces) ViewState token extraction
- Proper form ID handling for dynamic form names
- AJAX-compatible request headers
- Comprehensive error detection
- Success pattern matching

## Status Detection
- SUCCESS: 
  - Response contains "Welcome", "Dashboard", "My Account", or "Logout"
  - Redirect to /home, /dashboard, or /account
  - HTTP status codes 200 or 302
- FAIL: 
  - Error messages in response (Invalid username/password, Login failed, etc.)
  - Account locked or disabled messages
  - HTTP status codes 400, 401, 403

## Notes
- This config handles JSF-based authentication common in government portals
- ViewState token is required for form submission
- The site may use AJAX for form submission (x-requested-with header included)
- Cookies are automatically handled by the HTTP client
- Form ID may vary, so the config includes fallback logic
