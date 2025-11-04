# Empire Blue Cross Login Config

OpenBullet2 configuration for https://ebc.empireblue.com/

## Input Format
- USER: Username
- PASS: Password

## Features
- Extracts CSRF token from login page
- Performs login with username and password
- Detects successful login vs failed login

## Status Detection
- SUCCESS: Login successful (redirects to dashboard or contains welcome message)
- FAIL: Login failed (contains error messages or submission error page)
