# Findings Summary

This document converts the practical findings from the thesis into a concise security-report format.

## F-01 — Broken Access Control

**Category:** Access Control  
**Environment:** local bWAPP lab  
**Severity in thesis:** security weakness demonstrated; no CVSS score assigned.

### Observation
A directory intended to be accessible only to authorized users could be reached without completing the required authorization flow.

### Impact
An unauthorized user may access resources that should be protected, resulting in information disclosure.

### Remediation
Enforce authorization server-side for every protected resource and verify access using the user's authenticated identity and permissions.

---

## F-02 — Insecure Login Form

**Category:** Authentication

### Observation
The practical test demonstrated weaknesses in the login implementation, including exposure of authentication information through the application's source.

### Impact
Exposure of authentication information can enable unauthorized account access.

### Remediation
Keep credentials and authentication decisions server-side; use secure password storage and robust authentication controls.

---

## F-03 — Logout / Session Management

**Category:** Session Management

### Observation
The thesis examined the risk of session information remaining usable after logout.

### Impact
Residual session state can support unauthorized reuse of an authenticated session.

### Remediation
Invalidate sessions on logout and apply secure session-management practices.

---

## F-04 — Administrative Portal Access Control

**Category:** Access Control / Authorization

### Observation
The lab application allowed administrative functionality to become accessible through manipulation of a client-controlled URL parameter.

### Impact
Privilege-boundary bypass can expose administrative functionality and sensitive operations.

### Remediation
Make authorization decisions exclusively on the server side and enforce role/permission checks for every administrative endpoint.

---

## F-05 — Reflected HTML Injection

**Category:** Input Validation / Output Encoding

### Observation
User-controlled HTML was reflected into the generated page.

### Impact
An attacker may manipulate page content and create misleading content or support social-engineering scenarios.

### Remediation
Validate input and contextually encode output; do not render untrusted input as HTML.

---

## F-06 — Reflected XSS

**Category:** Cross-Site Scripting

### Observation
The lab application reflected attacker-controlled content into a browser-executed context.

### Impact
Client-side script execution can compromise the security context of users interacting with the vulnerable page.

### Remediation
Use contextual output encoding, server-side validation, CSP, and secure cookie attributes such as `HttpOnly` where appropriate.

---

## F-07 — OWASP ZAP findings

**Category:** Automated vulnerability assessment

The documented ZAP scan reported 18 observations:

- 7 Medium
- 5 Low
- 6 Informational
- 0 High

Notable observations included:
- missing clickjacking protection headers;
- missing Anti-CSRF tokens;
- missing CSP;
- directory browsing;
- missing `X-Content-Type-Options`;
- missing `HttpOnly`;
- information disclosure through HTTP headers.

The thesis recommends addressing the medium-risk findings first, followed by lower-risk hardening and informational review.
