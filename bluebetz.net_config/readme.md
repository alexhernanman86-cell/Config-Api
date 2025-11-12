# Bluebetz Login Config

OpenBullet2 configuration for https://bluebetz.net/home

## Input Format
- USER: Username/Email
- PASS: Password

## Authentication Flow
1. Accesses the home page at `/home` to establish session
2. Performs login POST request to `/auth/login?return=home`
3. Sends username and password as form data

## Features
- Standard form-based authentication
- Session cookie handling
- Proper referer headers for CSRF protection

## Status Detection
- SUCCESS: 
  - Response contains success indicators
  - User logged in messages
  - Dashboard or balance references
  - HTTP status codes 200 or 302
  - Redirect to `/home` or `/dashboard`
- FAIL: 
  - Error messages in response
  - Invalid credentials messages
  - Login failed messages
  - HTTP status codes 400, 401, 403

## Notes
- The site uses Cloudflare protection
- reCAPTCHA may be present (may require browser automation for full functionality)
- Proper user-agent headers are required
- Cookies are automatically handled by the HTTP client
- Site may require JavaScript execution for full functionality
