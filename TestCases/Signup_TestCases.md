# Signup Module Test Cases - TestProAI.com

## Test Case Summary
- **Module**: Signup/Registration
- **Total Test Cases**: 15
- **Priority Distribution**: High (10), Medium (4), Low (1)

---

| Test Case ID | Module | Title | Preconditions | Steps | Test Data | Expected Result | Actual Result | Priority | Severity |
|--------------|--------|-------|---------------|-------|-----------|-----------------|---------------|----------|----------|
| TC_SIGNUP_001 | Signup | Valid User Registration | Signup page is accessible, Email not already registered | 1. Navigate to signup page<br>2. Enter valid first name<br>3. Enter valid last name<br>4. Enter valid email<br>5. Enter valid password<br>6. Confirm password<br>7. Accept terms and conditions<br>8. Click Register button | First Name: John<br>Last Name: Doe<br>Email: john.doe@example.com<br>Password: SecurePass123!<br>Confirm Password: SecurePass123! | User successfully registered, confirmation email sent, redirected to verification page | | High | High |
| TC_SIGNUP_002 | Signup | Duplicate Email Registration | Signup page is accessible, Email already exists in system | 1. Navigate to signup page<br>2. Fill all required fields<br>3. Enter email that already exists<br>4. Click Register button | Email: existing@testproai.com<br>Other fields: Valid data | Error message: "Email already exists. Please use a different email or login." | | High | High |
| TC_SIGNUP_003 | Signup | Invalid Email Format Registration | Signup page is accessible | 1. Navigate to signup page<br>2. Fill all fields with valid data<br>3. Enter invalid email format<br>4. Click Register button | Email: invalid-email-format<br>Other fields: Valid data | Error message: "Please enter a valid email address" | | High | Medium |
| TC_SIGNUP_004 | Signup | Password Mismatch | Signup page is accessible | 1. Navigate to signup page<br>2. Fill all fields<br>3. Enter password<br>4. Enter different confirm password<br>5. Click Register button | Password: SecurePass123!<br>Confirm Password: DifferentPass456! | Error message: "Passwords do not match" | | High | Medium |
| TC_SIGNUP_005 | Signup | Weak Password Registration | Signup page is accessible | 1. Navigate to signup page<br>2. Fill all fields<br>3. Enter weak password<br>4. Click Register button | Password: 123<br>Other fields: Valid data | Error message indicating password requirements (length, complexity) | | High | Medium |
| TC_SIGNUP_006 | Signup | Empty Required Fields | Signup page is accessible | 1. Navigate to signup page<br>2. Leave required fields empty<br>3. Click Register button | All fields: (empty) | Error messages for all required fields displayed | | High | Medium |
| TC_SIGNUP_007 | Signup | First Name Validation | Signup page is accessible | 1. Navigate to signup page<br>2. Enter invalid first name (numbers/special chars)<br>3. Fill other fields with valid data<br>4. Click Register button | First Name: John123!@#<br>Other fields: Valid data | Error message: "First name should contain only letters" | | Medium | Low |
| TC_SIGNUP_008 | Signup | Last Name Validation | Signup page is accessible | 1. Navigate to signup page<br>2. Enter invalid last name<br>3. Fill other fields with valid data<br>4. Click Register button | Last Name: Doe456$%^<br>Other fields: Valid data | Error message: "Last name should contain only letters" | | Medium | Low |
| TC_SIGNUP_009 | Signup | Terms and Conditions Acceptance | Signup page is accessible | 1. Navigate to signup page<br>2. Fill all fields with valid data<br>3. Do not check terms and conditions<br>4. Click Register button | Terms Checkbox: Unchecked<br>Other fields: Valid data | Error message: "Please accept the terms and conditions" | | High | Medium |
| TC_SIGNUP_010 | Signup | Password Visibility Toggle | Signup page is accessible | 1. Navigate to signup page<br>2. Enter password<br>3. Click password visibility toggle<br>4. Verify password visibility<br>5. Click toggle again | Password: TestPassword123 | Password text becomes visible/hidden when toggled | | Low | Low |
| TC_SIGNUP_011 | Signup | Email Verification Process | User completed registration | 1. Complete valid registration<br>2. Check email inbox<br>3. Click verification link<br>4. Verify account activation | Valid registration data | Verification email received, link activates account successfully | | High | High |
| TC_SIGNUP_012 | Signup | Maximum Length Field Validation | Signup page is accessible | 1. Navigate to signup page<br>2. Enter very long strings in name fields<br>3. Enter very long email<br>4. Click Register button | First Name: 500+ characters<br>Last Name: 500+ characters<br>Email: 300+ characters | Appropriate field length validation and error messages | | Medium | Low |
| TC_SIGNUP_013 | Signup | Special Characters in Name Fields | Signup page is accessible | 1. Navigate to signup page<br>2. Enter names with special characters<br>3. Fill other fields validly<br>4. Click Register button | First Name: José<br>Last Name: O'Connor<br>Other fields: Valid | System accepts valid special characters in names (accents, apostrophes) | | Medium | Medium |
| TC_SIGNUP_014 | Signup | Password Strength Indicator | Signup page is accessible | 1. Navigate to signup page<br>2. Start typing password<br>3. Observe password strength indicator<br>4. Try different password complexities | Various passwords: weak, medium, strong | Password strength indicator updates in real-time showing strength level | | High | Low |
| TC_SIGNUP_015 | Signup | Registration Form Reset | Signup page is accessible, Form partially filled | 1. Navigate to signup page<br>2. Fill some fields<br>3. Click Reset/Clear button (if available)<br>4. Verify form state | Partial form data | All form fields cleared, form returns to initial state | | Low | Low |

---

## Test Case Details

### TC_SIGNUP_001: Valid User Registration
**Objective**: Verify complete user registration flow with valid data
**Test Data Requirements**: 
- Unique email address not in system
- Password meeting complexity requirements
- Valid name formats
**Expected Behavior**: 
- Form validation passes
- User account created in database
- Confirmation email triggered
- Appropriate success message/redirect

### TC_SIGNUP_002: Duplicate Email Registration
**Objective**: Verify system prevents duplicate email registration
**Test Data**: 
- Email address that already exists in the system
**Expected Behavior**: 
- System checks email uniqueness
- Clear error message displayed
- User guided to login or password reset

### TC_SIGNUP_005: Weak Password Registration
**Objective**: Verify password complexity requirements are enforced
**Test Data**: 
- Various weak passwords (short, no special chars, common passwords)
**Expected Behavior**: 
- Password validation rules clearly communicated
- Specific feedback on password requirements
- Registration blocked until requirements met

### TC_SIGNUP_009: Terms and Conditions Acceptance
**Objective**: Verify legal compliance for user agreement
**Expected Behavior**: 
- Terms checkbox is required field
- Clear error message if not accepted
- Terms document is accessible and readable

### TC_SIGNUP_011: Email Verification Process
**Objective**: Verify email verification workflow
**Expected Behavior**: 
- Verification email sent promptly
- Email contains valid verification link
- Link successfully activates account
- User can login after verification

### TC_SIGNUP_014: Password Strength Indicator
**Objective**: Verify real-time password strength feedback
**Test Data**: 
- Weak: "123"
- Medium: "password123"
- Strong: "SecureP@ss123!"
**Expected Behavior**: 
- Indicator updates as user types
- Clear visual feedback (colors, text)
- Helpful suggestions for improvement

---

## Password Complexity Requirements (Expected)
- Minimum 8 characters
- At least one uppercase letter
- At least one lowercase letter
- At least one number
- At least one special character
- No common dictionary words

## Notes
- Test with various email providers (Gmail, Yahoo, Outlook, etc.)
- Verify responsive design on mobile devices
- Test browser autofill compatibility
- Capture screenshots for any validation failures
- Verify accessibility compliance for form elements