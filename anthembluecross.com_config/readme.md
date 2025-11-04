# Anthem Blue Cross Login Config

OpenBullet2 configuration for https://www.anthembluecross.com/account-login/

## Input Format
- USER: Username/Email
- PASS: Password

## Authentication Flow
1. Accesses the initial login page at `/account-login/`
2. Follows redirect to `/login/`
3. Extracts OAuth parameters from the login form
4. Navigates to Okta OAuth authorization page
5. Extracts CSRF and state tokens
6. Performs authentication via Okta API (`/api/v1/authn`)
7. Extracts session token from successful authentication
8. Completes OAuth flow with session token

## Features
- Full Okta OAuth2 authentication flow
- CSRF and state token extraction
- Session token handling
- Proper OAuth callback completion
- Comprehensive error detection

## Status Detection
- SUCCESS: 
  - Authentication response contains `"status":"SUCCESS"`
  - Session token present in response
  - OAuth callback redirect received
  - Authorization code present in redirect URL
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
