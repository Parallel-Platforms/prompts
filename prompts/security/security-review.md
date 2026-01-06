# Security Review

Perform a comprehensive security review of the provided code.

## Input Validation & Sanitization

### User Input
- **Validation**: Is all user input validated before use?
- **Sanitization**: Is input sanitized to prevent injection attacks?
- **Type Checking**: Are input types verified?
- **Range Checking**: Are numeric inputs checked for valid ranges?
- **Length Limits**: Are string lengths limited appropriately?

### Common Vulnerabilities
- **SQL Injection**: Are parameterized queries or ORMs used?
- **XSS (Cross-Site Scripting)**: Is output properly encoded?
- **Command Injection**: Are system commands avoided or properly sanitized?
- **Path Traversal**: Are file paths validated and restricted?
- **LDAP Injection**: If applicable, is LDAP input sanitized?

## Authentication & Authorization

### Authentication
- **Password Security**: Are passwords hashed with strong algorithms (bcrypt, Argon2)?
- **Password Policies**: Are strong password requirements enforced?
- **Multi-Factor Auth**: Is MFA supported or recommended?
- **Session Management**: Are sessions properly managed and secured?
- **Token Security**: Are tokens generated securely and validated properly?
- **Brute Force Protection**: Are login attempts rate-limited?

### Authorization
- **Access Control**: Are permissions checked before sensitive operations?
- **Principle of Least Privilege**: Do users have minimal necessary permissions?
- **RBAC/ABAC**: Is role-based or attribute-based access control implemented?
- **Horizontal Privilege Escalation**: Can users access other users' data?
- **Vertical Privilege Escalation**: Can users elevate their privileges?
- **Direct Object References**: Are object references properly authorized?

## Data Protection

### Sensitive Data
- **Encryption at Rest**: Is sensitive data encrypted in storage?
- **Encryption in Transit**: Is HTTPS/TLS used for all sensitive communication?
- **Secrets Management**: Are API keys, tokens, and passwords stored securely?
- **PII Protection**: Is personally identifiable information properly protected?
- **Data Masking**: Is sensitive data masked in logs and UI?
- **Secure Deletion**: Is data securely deleted when no longer needed?

### Cryptography
- **Strong Algorithms**: Are modern, secure cryptographic algorithms used?
- **Key Management**: Are encryption keys properly managed and rotated?
- **Random Number Generation**: Is cryptographically secure RNG used?
- **No Custom Crypto**: Are standard libraries used instead of custom implementations?

## API Security

### Request Security
- **HTTPS Only**: Are all API endpoints HTTPS-only?
- **CORS Configuration**: Is CORS properly configured?
- **CSRF Protection**: Are CSRF tokens implemented for state-changing operations?
- **Rate Limiting**: Are API endpoints rate-limited?
- **Request Size Limits**: Are request payloads size-limited?

### Response Security
- **Information Disclosure**: Do error messages avoid revealing sensitive information?
- **Security Headers**: Are appropriate security headers set (CSP, HSTS, etc.)?
- **Data Exposure**: Is only necessary data returned in responses?

## Common Security Issues

### Injection Vulnerabilities
- SQL injection prevention
- NoSQL injection prevention
- Command injection prevention
- LDAP injection prevention
- XML/XXE injection prevention

### Broken Authentication
- Weak password requirements
- Insecure password storage
- Session fixation
- Insecure session handling

### Sensitive Data Exposure
- Unencrypted data transmission
- Weak encryption algorithms
- Exposed secrets in code/logs
- Insufficient data protection

### XML External Entities (XXE)
- Disabled external entity processing
- Secure XML parser configuration

### Broken Access Control
- Missing authorization checks
- Insecure direct object references
- Path traversal vulnerabilities

### Security Misconfiguration
- Default credentials
- Unnecessary features enabled
- Outdated components
- Verbose error messages

### Cross-Site Scripting (XSS)
- Reflected XSS
- Stored XSS
- DOM-based XSS

### Insecure Deserialization
- Untrusted data deserialization
- Type validation before deserialization

### Using Components with Known Vulnerabilities
- Outdated dependencies
- Unpatched security vulnerabilities

### Insufficient Logging & Monitoring
- Security event logging
- Monitoring for suspicious activity
- Alert mechanisms

## Mobile-Specific Security (if applicable)
- **Secure Storage**: Using keychain/keystore for sensitive data
- **Certificate Pinning**: Implementing SSL pinning
- **Jailbreak/Root Detection**: Detecting compromised devices
- **Code Obfuscation**: Protecting intellectual property
- **Reverse Engineering Protection**: Anti-tampering measures

## Web-Specific Security (if applicable)
- **Content Security Policy**: Properly configured CSP
- **X-Frame-Options**: Clickjacking protection
- **X-Content-Type-Options**: MIME type sniffing prevention
- **Referrer Policy**: Controlling referrer information
- **Subresource Integrity**: SRI for external resources

## Compliance
- **GDPR**: Data protection and privacy requirements
- **HIPAA**: Healthcare data protection (if applicable)
- **PCI DSS**: Payment card data security (if applicable)
- **SOC 2**: Security, availability, and confidentiality

## Recommendations
Provide:
1. Severity rating for each issue (Critical, High, Medium, Low)
2. Specific vulnerable code locations
3. Remediation steps with code examples
4. References to security standards (OWASP, CWE, etc.)
5. Priority order for fixes

Please conduct a thorough security review and identify all potential vulnerabilities.
