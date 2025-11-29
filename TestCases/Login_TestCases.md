# Login Module Test Cases - TestProAI.com

## Test Case Summary
- **Module**: Login
- **Total Test Cases**: 12
- **Priority Distribution**: High (8), Medium (3), Low (1)

---

| Test Case ID | Module | Title | Preconditions | Steps | Test Data | Expected Result | Actual Result | Priority | Severity |
|--------------|--------|-------|---------------|-------|-----------|-----------------|---------------|----------|----------|
| TC_LOGIN_001 | Login | Valid Login with Email and Password | User has valid account, Login page is accessible | 1. Navigate to login page<br>2. Enter valid email<br>3. Enter valid password<br>4. Click Login button | Email: test@testproai.com<br>Password: ValidPass123! | User successfully logged in and redirected to dashboard/homepage | | High | High |
| TC_LOGIN_002 | Login | Invalid Email Format Login | Login page is accessible | 1. Navigate to login page<br>2. Enter invalid email format<br>3. Enter valid password<br>4. Click Login button | Email: invalid-email<br>Password: ValidPass123! | Error message displayed: "Please enter a valid email address" | | High | Medium |
| TC_LOGIN_003 | Login | Invalid Password Login | User has valid account, Login page is accessible | 1. Navigate to login page<br>2. Enter valid email<br>3. Enter incorrect password<br>4. Click Login button | Email: test@testproai.com<br>Password: WrongPassword | Error message displayed: "Invalid email or password" | | High | High |
| TC_LOGIN_004 | Login | Empty Email Field Login | Login page is accessible | 1. Navigate to login page<br>2. Leave email field empty<br>3. Enter valid password<br>4. Click Login button | Email: (empty)<br>Password: ValidPass123! | Error message displayed: "Email is required" | | High | Medium |
| TC_LOGIN_005 | Login | Empty Password Field Login | Login page is accessible | 1. Navigate to login page<br>2. Enter valid email<br>3. Leave password field empty<br>4. Click Login button | Email: test@testproai.com<br>Password: (empty) | Error message displayed: "Password is required" | | High | Medium |
| TC_LOGIN_006 | Login | Both Fields Empty Login | Login page is accessible | 1. Navigate to login page<br>2. Leave both fields empty<br>3. Click Login button | Email: (empty)<br>Password: (empty) | Error messages displayed for both fields | | Medium | Medium |
| TC_LOGIN_007 | Login | Remember Me Functionality | User has valid account, Login page is accessible | 1. Navigate to login page<br>2. Enter valid credentials<br>3. Check "Remember Me" checkbox<br>4. Click Login button<br>5. Close browser<br>6. Reopen and navigate to site | Email: test@testproai.com<br>Password: ValidPass123!<br>Remember Me: Checked | User remains logged in after browser restart | | Medium | Low |
| TC_LOGIN_008 | Login | Forgot Password Link | Login page is accessible | 1. Navigate to login page<br>2. Click "Forgot Password" link | N/A | User redirected to password reset page | | High | Medium |
| TC_LOGIN_009 | Login | Password Visibility Toggle | Login page is accessible | 1. Navigate to login page<br>2. Enter password<br>3. Click password visibility icon | Password: TestPassword123 | Password text becomes visible/hidden when toggled | | Low | Low |
| TC_LOGIN_010 | Login | Login with Special Characters in Password | User has account with special character password | 1. Navigate to login page<br>2. Enter valid email<br>3. Enter password with special characters<br>4. Click Login button | Email: test@testproai.com<br>Password: Pass@#$123! | User successfully logged in | | High | Medium |
| TC_LOGIN_011 | Login | Case Sensitive Email Login | User has account with specific email case | 1. Navigate to login page<br>2. Enter email in different case<br>3. Enter valid password<br>4. Click Login button | Email: TEST@TESTPROAI.COM<br>Password: ValidPass123! | Login should work (emails typically case-insensitive) | | Medium | Low |
| TC_LOGIN_012 | Login | SQL Injection in Login Fields | Login page is accessible | 1. Navigate to login page<br>2. Enter SQL injection payload in email<br>3. Enter SQL injection payload in password<br>4. Click Login button | Email: admin'--<br>Password: ' OR '1'='1 | System should reject input and show error message, no SQL injection occurs | | High | High |

---

## Test Case Details

### TC_LOGIN_001: Valid Login with Email and Password
**Objective**: Verify that user can successfully log in with valid credentials
**Test Data**: 
- Valid registered email address
- Correct password matching the email account
**Expected Behavior**: 
- Successful authentication
- Redirect to user dashboard or homepage
- User session established

### TC_LOGIN_002: Invalid Email Format Login
**Objective**: Verify system validates email format before processing login
**Test Data**: 
- Various invalid email formats (missing @, missing domain, etc.)
**Expected Behavior**: 
- Client-side validation prevents form submission
- Clear error message indicating email format issue

### TC_LOGIN_003: Invalid Password Login
**Objective**: Verify system handles incorrect password appropriately
**Test Data**: 
- Valid email with incorrect password
**Expected Behavior**: 
- Authentication fails securely
- Generic error message (don't reveal if email exists)
- No sensitive information leaked

### TC_LOGIN_008: Forgot Password Link
**Objective**: Verify forgot password functionality is accessible and working
**Expected Behavior**: 
- Link is visible and clickable
- Redirects to password reset page
- Password reset form is functional

### TC_LOGIN_012: SQL Injection in Login Fields
**Objective**: Verify system is protected against SQL injection attacks
**Test Data**: 
- Common SQL injection payloads
**Expected Behavior**: 
- Input sanitization prevents SQL injection
- Appropriate error handling
- No database errors exposed to user

---

## Notes
- All test cases should be executed on multiple browsers (Chrome, Firefox, Safari, Edge)
- Test cases should be validated on both desktop and mobile viewports
- Screenshots should be captured for any failed test cases
- Actual results should be documented during test execution