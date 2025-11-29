# Negative Test Cases - TestProAI.com

## Test Case Summary
- **Module**: Cross-Module Negative Testing
- **Total Test Cases**: 8
- **Focus**: Error handling, edge cases, security, and boundary conditions

---

| Test Case ID | Module | Title | Preconditions | Steps | Test Data | Expected Result | Actual Result | Priority | Severity |
|--------------|--------|-------|---------------|-------|-----------|-----------------|---------------|----------|----------|
| TC_NEG_001 | Login | SQL Injection Attack Prevention | Login page is accessible | 1. Navigate to login page<br>2. Enter SQL injection payload in email field<br>3. Enter SQL injection payload in password field<br>4. Click Login button | Email: admin'--<br>Password: ' OR '1'='1'-- | System rejects malicious input, displays generic error message, no database access granted | | High | Critical |
| TC_NEG_002 | Signup | XSS Script Injection in Form Fields | Signup page is accessible | 1. Navigate to signup page<br>2. Enter XSS script in name fields<br>3. Enter XSS script in other text fields<br>4. Submit form | First Name: &lt;script&gt;alert('XSS')&lt;/script&gt;<br>Last Name: &lt;img src=x onerror=alert('XSS')&gt; | System sanitizes input, no script execution, appropriate error handling | | High | Critical |
| TC_NEG_003 | All Forms | Extremely Long Input Handling | Any form is accessible | 1. Navigate to any form<br>2. Enter extremely long strings in text fields<br>3. Submit form | Input: 10,000+ character string | System handles long input gracefully, appropriate validation messages, no system crash | | Medium | High |
| TC_NEG_004 | Navigation | Direct URL Access to Protected Pages | User is not logged in | 1. Attempt to access protected URLs directly<br>2. Try various protected endpoints<br>3. Verify access control | URLs: /dashboard, /profile, /admin, /settings | User redirected to login page, no unauthorized access granted | | High | High |
| TC_NEG_005 | All Modules | Session Timeout Handling | User is logged in, Session timeout configured | 1. Login to application<br>2. Leave application idle beyond timeout<br>3. Attempt to perform actions<br>4. Verify session handling | Idle time: Beyond configured timeout | Session expires appropriately, user redirected to login, data not lost unexpectedly | | Medium | Medium |
| TC_NEG_006 | File Upload | Malicious File Upload Prevention | File upload feature available | 1. Navigate to file upload section<br>2. Attempt to upload executable files<br>3. Try uploading files with malicious extensions<br>4. Test oversized files | Files: .exe, .bat, .php, .jsp, 100MB+ files | System rejects dangerous file types, enforces size limits, appropriate error messages | | High | High |
| TC_NEG_007 | All Forms | CSRF Attack Prevention | User is logged in, Forms available | 1. Create malicious form on external site<br>2. Attempt to submit cross-site requests<br>3. Verify CSRF protection | External malicious form targeting site endpoints | CSRF tokens prevent unauthorized requests, appropriate security headers present | | High | High |
| TC_NEG_008 | Network | Application Behavior During Network Issues | Application is running | 1. Disconnect internet connection<br>2. Attempt to use application features<br>3. Reconnect internet<br>4. Verify recovery behavior | Network: Disconnected/Poor connection | Graceful error handling, appropriate offline messages, smooth recovery when reconnected | | Medium | Medium |

---

## Detailed Test Case Descriptions

### TC_NEG_001: SQL Injection Attack Prevention
**Objective**: Verify application is protected against SQL injection attacks
**Attack Vectors to Test**:
- Classic SQL injection: `' OR '1'='1'--`
- Union-based injection: `' UNION SELECT * FROM users--`
- Boolean-based blind: `' AND 1=1--`
- Time-based blind: `'; WAITFOR DELAY '00:00:05'--`

**Expected Security Measures**:
- Input sanitization and validation
- Parameterized queries/prepared statements
- Generic error messages (no database details exposed)
- Logging of suspicious activities

### TC_NEG_002: XSS Script Injection Prevention
**Objective**: Verify application prevents cross-site scripting attacks
**XSS Payloads to Test**:
- Basic script: `<script>alert('XSS')</script>`
- Image-based: `<img src=x onerror=alert('XSS')>`
- Event handler: `<div onmouseover="alert('XSS')">Test</div>`
- Encoded payload: `%3Cscript%3Ealert('XSS')%3C/script%3E`

**Expected Security Measures**:
- Input encoding/escaping
- Content Security Policy (CSP) headers
- Output sanitization
- No script execution in user input

### TC_NEG_003: Extremely Long Input Handling
**Objective**: Verify application handles boundary conditions gracefully
**Test Scenarios**:
- 10,000+ character strings in text fields
- Maximum integer values in numeric fields
- Unicode characters and special symbols
- Buffer overflow attempts

**Expected Behavior**:
- Input length validation
- Graceful truncation or rejection
- No application crashes or memory issues
- Clear error messages about limits

### TC_NEG_004: Direct URL Access to Protected Pages
**Objective**: Verify proper access control and authentication
**URLs to Test**:
- `/dashboard` - User dashboard
- `/admin` - Administrative pages
- `/profile` - User profile pages
- `/api/users` - API endpoints
- `/settings` - Configuration pages

**Expected Behavior**:
- Redirect to login page for unauthenticated users
- Proper role-based access control
- No sensitive information exposure
- Consistent authentication checks

### TC_NEG_005: Session Timeout Handling
**Objective**: Verify proper session management and timeout behavior
**Test Scenarios**:
- Natural session expiration
- Forced session timeout
- Multiple tab session handling
- Session fixation attempts

**Expected Behavior**:
- Configurable session timeout
- Secure session invalidation
- Warning before timeout (optional)
- Proper cleanup of session data

### TC_NEG_006: Malicious File Upload Prevention
**Objective**: Verify file upload security measures
**Malicious Files to Test**:
- Executable files (.exe, .bat, .com)
- Script files (.php, .jsp, .asp)
- Archive bombs (zip files with huge expansion)
- Files with double extensions (.jpg.exe)

**Expected Security Measures**:
- File type validation (whitelist approach)
- File size limits enforcement
- Virus scanning (if implemented)
- Secure file storage location

### TC_NEG_007: CSRF Attack Prevention
**Objective**: Verify protection against cross-site request forgery
**Attack Scenarios**:
- External form submitting to application
- Malicious links triggering actions
- AJAX requests from external sites
- Image tags with action URLs

**Expected Security Measures**:
- CSRF tokens in forms
- SameSite cookie attributes
- Referer header validation
- Double-submit cookie pattern

### TC_NEG_008: Network Issues Handling
**Objective**: Verify application resilience during network problems
**Network Conditions to Test**:
- Complete network disconnection
- Slow/intermittent connection
- DNS resolution failures
- Server timeouts

**Expected Behavior**:
- Graceful degradation of features
- Appropriate error messages
- Retry mechanisms for failed requests
- Offline functionality (if applicable)

---

## Security Testing Checklist

### Input Validation
- [ ] SQL injection prevention
- [ ] XSS prevention
- [ ] Command injection prevention
- [ ] Path traversal prevention
- [ ] LDAP injection prevention

### Authentication & Authorization
- [ ] Brute force protection
- [ ] Account lockout mechanisms
- [ ] Password complexity enforcement
- [ ] Session management security
- [ ] Role-based access control

### Data Protection
- [ ] Sensitive data encryption
- [ ] Secure data transmission (HTTPS)
- [ ] Proper error handling (no info disclosure)
- [ ] Secure file upload handling
- [ ] Data sanitization

### Network Security
- [ ] CSRF protection
- [ ] Clickjacking prevention
- [ ] Security headers implementation
- [ ] SSL/TLS configuration
- [ ] Rate limiting

---

## Error Handling Standards

### User-Friendly Error Messages
- Clear, non-technical language
- Actionable guidance for users
- No sensitive system information
- Consistent error message format

### Security Considerations
- Generic error messages for security-related failures
- No database error details exposed
- No system path information revealed
- Proper logging of security events

### Recovery Mechanisms
- Clear instructions for error resolution
- Contact information for support
- Graceful fallback options
- Data preservation during errors

---

## Notes for Test Execution
- Use security testing tools (OWASP ZAP, Burp Suite) for comprehensive testing
- Test with different user roles and permissions
- Verify error logging and monitoring systems
- Document all security findings with appropriate severity levels
- Retest after security fixes are implemented