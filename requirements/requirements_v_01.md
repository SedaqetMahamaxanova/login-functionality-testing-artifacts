# Login Functionality – Requirements

This document defines the requirements for the Login functionality of [SauceDemo v1](https://www.saucedemo.com/v1/index.html).

---

## 1. User Story
As a user, I want to log into the system with a valid username and password so that I can access the inventory page.

---

## 2. Accepted Credentials
- **Usernames:**
  - `standard_user`
  - `locked_out_user`
  - `problem_user`
  - `performance_glitch_user`

- **Password (for all users):**
  - `secret_sauce`

---

## 3. Functional Requirements
- **FR-01**: The login page must have input fields for `Username` and `Password`, and a `Login` button.
- **FR-02**: If username is empty, system must show error message: **"Username is required"**.
- **FR-03**: If password is empty, system must show error message: **"Password is required"**.
- **FR-04**: If username + password are valid:
  - User is redirected to the `inventory.html` page.
- **FR-05**: If credentials are invalid:
  - Show error message: **"Epic sadface: Username and password do not match any user in this service"**.
- **FR-06**: For `locked_out_user`, login must be blocked and error shown:  
  **"Epic sadface: Sorry, this user has been locked out."**
- **FR-07**: Password field must mask input characters (••••••).
- **FR-08**: Login form must be submitted with **Enter** key as well as `Login` button.
- **FR-09**: After successful login, user session must persist until logout or browser close.

---

## 4. Non-Functional Requirements
- **NFR-01**: Error messages must be clear, readable, and displayed near the login form.
- **NFR-02**: Response time for login attempt should be under 2 seconds (except `performance_glitch_user`, where delay may occur).
- **NFR-03**: The login functionality must work on at least Chrome and Firefox browsers.
- **NFR-04**: All error messages must be generic (no sensitive info like “wrong password for user X”).

---

## 5. Out of Scope
- Two-Factor Authentication (2FA)
- “Forgot Password” functionality
- Captcha / brute-force protection
- Mobile responsiveness (not part of this test scope)

---

## 6. Acceptance Criteria (Summary)
- AC1: Empty username → "Username is required"
- AC2: Empty password → "Password is required"
- AC3: Valid username/password → Redirect to inventory page
- AC4: Invalid credentials → Generic error message
- AC5: Locked out user → Locked error message
- AC6: Password field is masked
- AC7: Enter key submits form
- AC8: Session persists until logout
