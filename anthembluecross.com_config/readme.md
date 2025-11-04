# Anthem Blue Cross Login Config

OpenBullet2 configuration for https://www.anthembluecross.com/account-login/

## Input Format
- USER: Username/Email
- PASS: Password

## Features
- Accesses the login page
- Extracts any CSRF tokens or session cookies
- Performs login with username and password
- Detects successful login vs failed login

## Status Detection
- SUCCESS: Login successful (redirects to dashboard or contains welcome message)
- FAIL: Login failed (contains error messages or submission error page)

## Notes
This config targets the member login portal. The site uses JavaScript-heavy authentication, so ensure proper user-agent headers are set.
