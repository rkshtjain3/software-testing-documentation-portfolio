# Sample Bug Reports - TestProAI.com

## Sample Bug Report #1

### Bug Report Information
**Bug ID**: BUG-001  
**Date Reported**: 15/12/2024  
**Reported By**: QA Tester  
**Assigned To**: Frontend Development Team  
**Module**: Login  
**Priority**: High  
**Severity**: High  
**Status**: New  

---

### Bug Summary
**Title**: Login button remains disabled after entering valid credentials

**Description**: 
When users enter valid email and password credentials in the login form, the login button remains disabled and cannot be clicked. This prevents users from logging into their accounts even with correct credentials.

---

### Environment Details
**URL**: https://testproai.com/login  
**Browser**: Chrome 120.0.6099.109  
**Operating System**: Windows 11  
**Device**: Desktop  
**Screen Resolution**: 1920x1080  
**Network**: WiFi  

---

### Steps to Reproduce
1. Navigate to https://testproai.com/login
2. Enter valid email address: "testuser@testproai.com"
3. Enter valid password: "ValidPassword123!"
4. Observe the login button state
5. Attempt to click the login button

**Test Data Used**:
- Email: testuser@testproai.com
- Password: ValidPassword123!

---

### Expected Result
Login button should become enabled (clickable) when both email and password fields contain valid data, allowing user to submit the login form.

---

### Actual Result
Login button remains disabled (grayed out) even after entering valid credentials. Button cannot be clicked and form cannot be submitted.

---

### Screenshots/Evidence
**Screenshot 1**: Login form with valid credentials and disabled button
- File: `screenshot_001_BUG-001.png`
- Location: `/Screenshots/BugReports/`

**Console Logs**:
```
No JavaScript errors found in console
```

---

### Additional Information
**Frequency**: Always  
**Workaround Available**: No  
**Related Bugs**: None  
**Regression**: Unknown - needs verification with previous version  

**Impact Assessment**:
- **User Impact**: Users cannot log into their accounts
- **Business Impact**: Prevents user access to platform features
- **Technical Impact**: Login functionality completely broken

---

## Sample Bug Report #2

### Bug Report Information
**Bug ID**: BUG-002  
**Date Reported**: 15/12/2024  
**Reported By**: QA Tester  
**Assigned To**: Backend Development Team  
**Module**: Signup  
**Priority**: Medium  
**Severity**: Medium  
**Status**: New  

---

### Bug Summary
**Title**: Email verification link expires immediately after registration

**Description**: 
After completing user registration, the email verification link sent to users expires immediately or within a very short time frame, preventing users from activating their accounts.

---

### Environment Details
**URL**: https://testproai.com/signup  
**Browser**: Firefox 121.0  
**Operating System**: macOS Sonoma 14.2  
**Device**: MacBook Pro  
**Screen Resolution**: 1440x900  
**Network**: Ethernet  

---

### Steps to Reproduce
1. Navigate to https://testproai.com/signup
2. Fill registration form with valid data
3. Submit registration form
4. Check email inbox for verification email
5. Click verification link in email (within 2-3 minutes)
6. Observe error message about expired link

**Test Data Used**:
- Name: John Doe
- Email: john.doe.test@gmail.com
- Password: SecurePass123!

---

### Expected Result
Email verification link should remain valid for at least 24 hours, allowing users sufficient time to verify their email address and activate their account.

---

### Actual Result
Email verification link shows "Link expired" error message when clicked, even within minutes of receiving the email.

---

### Screenshots/Evidence
**Screenshot 1**: Registration success message
- File: `screenshot_001_BUG-002.png`

**Screenshot 2**: Email verification link expired error
- File: `screenshot_002_BUG-002.png`

---

### Additional Information
**Frequency**: Always  
**Workaround Available**: Yes - Request new verification email  
**Related Bugs**: None  
**Regression**: No - new functionality  

**Impact Assessment**:
- **User Impact**: Users cannot complete account activation
- **Business Impact**: Reduces successful user registrations
- **Technical Impact**: Email verification system configuration issue

---

## Sample Bug Report #3

### Bug Report Information
**Bug ID**: BUG-003  
**Date Reported**: 15/12/2024  
**Reported By**: QA Tester  
**Assigned To**: Frontend Development Team  
**Module**: Homepage  
**Priority**: Low  
**Severity**: Low  
**Status**: New  

---

### Bug Summary
**Title**: Footer social media icons misaligned on mobile devices

**Description**: 
On mobile devices, the social media icons in the footer section are not properly aligned and appear scattered instead of being in a neat row.

---

### Environment Details
**URL**: https://testproai.com  
**Browser**: Safari Mobile (iOS 17.2)  
**Operating System**: iOS 17.2  
**Device**: iPhone 14  
**Screen Resolution**: 390x844  
**Network**: Mobile 4G  

---

### Steps to Reproduce
1. Open https://testproai.com on mobile device
2. Scroll down to footer section
3. Observe social media icons alignment
4. Compare with desktop version

**Test Data Used**:
- N/A (Visual layout issue)

---

### Expected Result
Social media icons should be properly aligned in a horizontal row, evenly spaced, and visually appealing on mobile devices.

---

### Actual Result
Social media icons appear misaligned, with uneven spacing and some icons appearing on different lines.

---

### Screenshots/Evidence
**Screenshot 1**: Mobile footer with misaligned icons
- File: `screenshot_001_BUG-003.png`

**Screenshot 2**: Desktop footer for comparison
- File: `screenshot_002_BUG-003.png`

---

### Additional Information
**Frequency**: Always on mobile  
**Workaround Available**: No  
**Related Bugs**: None  
**Regression**: Unknown  

**Impact Assessment**:
- **User Impact**: Minor visual inconsistency
- **Business Impact**: Minimal - cosmetic issue only
- **Technical Impact**: CSS responsive design issue

---

## Sample Bug Report #4

### Bug Report Information
**Bug ID**: BUG-004  
**Date Reported**: 15/12/2024  
**Reported By**: Security Tester  
**Assigned To**: Security Team  
**Module**: Login  
**Priority**: Critical  
**Severity**: Critical  
**Status**: New  

---

### Bug Summary
**Title**: SQL injection vulnerability in login form

**Description**: 
The login form is vulnerable to SQL injection attacks through the email field, potentially allowing unauthorized access to the database and user accounts.

---

### Environment Details
**URL**: https://testproai.com/login  
**Browser**: Chrome 120.0.6099.109  
**Operating System**: Windows 11  
**Device**: Desktop  
**Screen Resolution**: 1920x1080  
**Network**: WiFi  

---

### Steps to Reproduce
1. Navigate to https://testproai.com/login
2. Enter SQL injection payload in email field: `admin'--`
3. Enter any password
4. Click login button
5. Observe system response

**Test Data Used**:
- Email: admin'--
- Password: anypassword

---

### Expected Result
System should reject the malicious input, display a generic error message, and prevent any database access or authentication bypass.

---

### Actual Result
System appears to process the SQL injection payload without proper sanitization, potentially exposing the application to security vulnerabilities.

---

### Screenshots/Evidence
**Screenshot 1**: SQL injection payload in login form
- File: `screenshot_001_BUG-004.png`

**Network Logs**:
```
POST /api/login
Request payload contains unsanitized SQL characters
```

---

### Additional Information
**Frequency**: Always  
**Workaround Available**: No  
**Related Bugs**: Potential XSS vulnerabilities in other forms  
**Regression**: No - security vulnerability  

**Impact Assessment**:
- **User Impact**: Potential unauthorized access to accounts
- **Business Impact**: Critical security risk, data breach potential
- **Technical Impact**: Database security compromise

---

## Sample Bug Report #5

### Bug Report Information
**Bug ID**: BUG-005  
**Date Reported**: 15/12/2024  
**Reported By**: Performance Tester  
**Assigned To**: Performance Team  
**Module**: Homepage  
**Priority**: Medium  
**Severity**: Medium  
**Status**: New  

---

### Bug Summary
**Title**: Homepage loading time exceeds 10 seconds on slow connections

**Description**: 
The homepage takes an excessive amount of time to load completely on slower internet connections, significantly impacting user experience and potentially causing users to abandon the site.

---

### Environment Details
**URL**: https://testproai.com  
**Browser**: Chrome 120.0.6099.109  
**Operating System**: Windows 11  
**Device**: Desktop  
**Screen Resolution**: 1920x1080  
**Network**: 3G Simulation (1.6 Mbps)  

---

### Steps to Reproduce
1. Set browser to simulate 3G connection speed
2. Clear browser cache and cookies
3. Navigate to https://testproai.com
4. Measure page load time using browser dev tools
5. Observe user experience during loading

**Test Data Used**:
- Network throttling: 3G (1.6 Mbps down, 750 Kbps up)

---

### Expected Result
Homepage should load completely within 5 seconds even on slower connections, with progressive loading of content to maintain user engagement.

---

### Actual Result
Homepage takes 12-15 seconds to load completely on 3G connection, with long periods of blank screen and no loading indicators.

---

### Screenshots/Evidence
**Screenshot 1**: Network performance timeline
- File: `screenshot_001_BUG-005.png`

**Performance Metrics**:
```
First Contentful Paint: 8.2s
Largest Contentful Paint: 12.4s
Total Load Time: 15.1s
```

---

### Additional Information
**Frequency**: Always on slow connections  
**Workaround Available**: No  
**Related Bugs**: None  
**Regression**: Unknown - needs baseline comparison  

**Impact Assessment**:
- **User Impact**: Poor user experience, potential site abandonment
- **Business Impact**: Reduced conversion rates, SEO impact
- **Technical Impact**: Performance optimization needed

---

## Bug Report Categories

### Functional Bugs
- Features not working as designed
- Incorrect calculations or logic
- Missing functionality
- Integration failures

### UI/UX Bugs
- Layout and alignment issues
- Color and styling problems
- Responsive design failures
- Accessibility issues

### Performance Bugs
- Slow loading times
- Memory leaks
- Resource optimization issues
- Scalability problems

### Security Bugs
- Input validation failures
- Authentication bypasses
- Data exposure vulnerabilities
- Cross-site scripting (XSS)

### Compatibility Bugs
- Browser-specific issues
- Device-specific problems
- Operating system conflicts
- Version compatibility issues

---

## Bug Triage Guidelines

### Critical Priority
- System crashes or data loss
- Security vulnerabilities
- Complete feature failures
- Blocks other testing activities

### High Priority
- Major functionality affected
- Significant user impact
- No reasonable workaround
- Affects core business processes

### Medium Priority
- Minor functionality affected
- Workaround available
- Limited user impact
- Non-critical features

### Low Priority
- Cosmetic issues
- Minor inconveniences
- Enhancement requests
- Documentation errors