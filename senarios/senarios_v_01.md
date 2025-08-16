# High-Level Test Scenarios — SauceDemo v1 (Login)

**Scope:** Functional and UX scenarios for the login flow based on the approved requirements and acceptance criteria.

---

## HS-01 · Successful login with valid credentials
**Goal:** Verify redirect to inventory page and session start.  
**AC:** AC3, AC8  

**Given** the login page is open  
**When** `standard_user` and `secret_sauce` are provided  
**Then** the app redirects to `inventory.html` and a session is active  

---

## HS-02 · Warning message for empty username
**Goal:** Validate error when username is missing.  
**AC:** AC1  

**Given** the login page is open  
**When** the username field is empty and a password is entered  
**Then** the message **"Username is required"** is displayed  

---

## HS-03 · Warning message for empty password
**Goal:** Validate error when password is missing.  
**AC:** AC2  

**Given** the login page is open  
**When** a valid username is entered and the password field is empty  
**Then** the message **"Password is required"** is displayed  

---

## HS-04 · Generic error for invalid credentials
**Goal:** Ensure generic message for any invalid combination.  
**AC:** AC4  

**Given** the login page is open  
**When** an incorrect username and/or password is entered  
**Then** the message  
**"Epic sadface: Username and password do not match any user in this service"** is displayed  

---

## HS-05 · Login blocked for locked out user
**Goal:** Confirm access is denied for `locked_out_user`.  
**AC:** AC5  

**Given** the login page is open  
**When** `locked_out_user` and `secret_sauce` are provided  
**Then** the message  
**"Epic sadface: Sorry, this user has been locked out."** is displayed and no redirect occurs  

---

## HS-06 · Password masking in the input field
**Goal:** Verify password characters are hidden.  
**AC:** AC6  

**Given** the login page is open  
**When** characters are typed into the password field  
**Then** the input displays masked characters (e.g., ••••••)  

---

## HS-07 · Form submission via Enter key
**Goal:** Confirm Enter submits equivalent to clicking Login.  
**AC:** AC7  

**Given** valid credentials are present  
**When** the Enter key is pressed  
**Then** login succeeds and the user is redirected to `inventory.html`  

---

## HS-08 · Session persistence after successful login
**Goal:** Validate session continuity without re-login.  
**AC:** AC8  

**Given** the user is logged in  
**When** the page is refreshed or `inventory.html` is opened in a new tab  
**Then** the user remains authenticated  

---

## HS-09 · Redirect target verification after success
**Goal:** Ensure the exact target URL is correct.  
**AC:** AC3  

**Given** valid credentials are submitted  
**When** login completes  
**Then** the browser URL ends with `/inventory.html`  

---

## HS-10 · Problem user post-login UI behavior
**Goal:** Observe potential UI anomalies with `problem_user`.  
**AC:** (NFR observation), AC3  

**Given** the login page is open  
**When** `problem_user` logs in  
**Then** login completes; any visual or logical anomalies on the inventory page are noted  

---

## HS-11 · Performance glitch user response time
**Goal:** Record expected delay for `performance_glitch_user`.  
**AC:** NFR-02 exception  

**Given** the login page is open  
**When** `performance_glitch_user` logs in  
**Then** login eventually succeeds; measured response time may exceed 2 seconds and is recorded  

---

## HS-12 · Keyboard focus and tab order
**Goal:** Validate accessibility and smooth keyboard navigation.  
**AC:** NFR-01 (clarity/UX)  

**Given** the login page is open  
**When** Tab and Shift+Tab are used  
**Then** focus order follows Username → Password → Login button  

---

## HS-13 · Case sensitivity handling for credentials
**Goal:** Verify that username/password matching respects case rules.  
**AC:** AC4 (generic error)  

**Given** the login page is open  
**When** the username or password is entered with different casing than expected  
**Then** login fails with the generic error message  

---

## HS-14 · Error message placement and readability
**Goal:** Validate error visibility near the form and readability.  
**AC:** NFR-01  

**Given** any error state is triggered  
**When** the page displays the message  
**Then** the message is clearly readable and positioned near the login form  

---

## HS-15 · Multiple sequential failed attempts do not leak info
**Goal:** Ensure no sensitive info is exposed across retries.  
**AC:** NFR-04  

**Given** the login page is open  
**When** multiple invalid attempts are made  
**Then** only generic error messages appear; no user-specific details are revealed  
