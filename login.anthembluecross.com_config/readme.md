# Anthem Blue Cross Login Config

OpenBullet2 configuration for https://login.anthembluecross.com/

## Input Format
- USER: Username/Email
- PASS: Password

## Authentication Flow
1. Accesses the login page at `https://login.anthembluecross.com/`
2. Extracts CSRF and state tokens from the login form
3. Performs authentication via Okta API (`/api/v1/authn`)
4. Extracts session token from successful authentication
5. Verifies authentication status from API response

## Features
- Direct Okta authentication flow
- CSRF and state token extraction
- Session token handling
- Comprehensive error detection

## Status Detection
- SUCCESS: 
  - Authentication response contains `"status":"SUCCESS"`
  - Session token present in response
  - HTTP status code 200
- FAIL: 
  - Error messages in response (`errorCauses`, `errorSummary`)
  - Authentication failed messages
  - Invalid credentials errors
  - HTTP status codes 400, 401, 403
  - Okta error codes (E0000004, E0000001)

## Notes
- This config uses Okta Identity Provider for authentication
- The site uses JavaScript-heavy authentication flows
- Proper user-agent headers are required for successful authentication
- Cookies are automatically handled by the HTTP client
- Session tokens are used for subsequent API calls
