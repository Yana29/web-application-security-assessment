# Web Application Security Assessment — bWAPP

**Author:** Yana Tymoshenko  
**Project type:** Master's thesis / academic security assessment  
**Year:** 2023  
**Focus:** Web Application Security, Penetration Testing, Vulnerability Assessment, Risk Analysis

## Overview

This repository presents a portfolio version of practical work performed as part of my Master's thesis in Cybersecurity.

The assessment used the intentionally vulnerable **bWAPP (buggy web application)** in a local test environment. The work combined manual security testing with automated vulnerability scanning and documented the observed weaknesses, their security impact, and recommended remediation measures.

The original thesis describes the objective as identifying web-application weaknesses, analysing associated risks, demonstrating vulnerabilities, and deriving effective protection measures.

## Scope and ethics

- Target: local, intentionally vulnerable bWAPP lab environment.
- No production systems were tested.
- Evidence is limited to the laboratory work documented in the thesis.
- Sensitive-looking values from the original screenshots are not reproduced in this repository.
- This repository is a portfolio presentation of academic/project work, **not commercial penetration-testing employment**.

## What I worked on

### 1. Broken Access Control

I tested access restrictions for a protected `documents` directory. The assessment demonstrated that a resource intended for authenticated users could be accessed without the required authorization.

**Security impact:** unauthorized access to resources and potential information disclosure.

**Recommended controls:**
- enforce authorization server-side for every protected resource;
- deny direct unauthenticated access to protected directories;
- apply least-privilege access rules;
- test authorization boundaries with both authenticated and unauthenticated users.

### 2. Authentication weaknesses

The thesis examined an insecure login form and demonstrated that authentication data could be exposed through the application's page/source structure.

**Security impact:** possible unauthorized account access and confidentiality loss.

**Recommended controls:**
- never expose credentials in client-side source;
- store passwords securely using appropriate password hashing;
- implement robust authentication controls;
- add MFA where appropriate;
- review authentication and session-management logic.

### 3. Session / Logout Management

The assessment considered weaknesses in session handling after logout, including the risk that session information may remain usable.

**Recommended controls:**
- invalidate server-side sessions on logout;
- rotate session identifiers where appropriate;
- configure secure cookie attributes;
- test session reuse after logout.

### 4. Administrative Portal Access Control

The lab demonstrated an administrative portal whose access control could be bypassed through URL manipulation in the intentionally vulnerable application.

**Security impact:** unauthorized access to administrative functionality.

**Recommended controls:**
- enforce authorization on the server side;
- never rely on client-controlled URL parameters for privilege decisions;
- apply role-based authorization;
- test privilege boundaries systematically.

### 5. HTML Injection

The thesis demonstrated reflected HTML injection through user-controlled input.

**Security impact:** manipulation of rendered content and potential support for social-engineering scenarios.

**Recommended controls:**
- validate input;
- contextually encode output;
- use allowlists where appropriate;
- avoid rendering untrusted input as HTML.

### 6. Reflected XSS

The practical work demonstrated reflected XSS and showed that injected client-side code could access browser cookie information in the vulnerable lab application.

**Recommended controls:**
- context-aware output encoding;
- server-side input validation;
- Content Security Policy (CSP);
- secure cookie configuration, including `HttpOnly` where applicable;
- systematic XSS testing during development.

## Automated scanning with OWASP ZAP

The thesis also used **OWASP ZAP** for active scanning of the local web application.

The documented scan produced **18 observations**:

| Risk level | Count | Share |
|---|---:|---:|
| High | 0 | 0% |
| Medium | 7 | 38.9% |
| Low | 5 | 27.8% |
| Informational | 6 | 33.3% |
| **Total** | **18** | **100%** |

Examples of observations included missing anti-clickjacking protection, missing Anti-CSRF tokens, missing Content Security Policy, directory browsing, missing `X-Content-Type-Options`, missing `HttpOnly`, and information disclosure through HTTP headers.

## Assessment workflow

```text
Local lab setup
      ↓
bWAPP authentication / reconnaissance
      ↓
Manual vulnerability testing
      ↓
Impact and risk analysis
      ↓
OWASP ZAP active scan
      ↓
Review of scanner findings
      ↓
Remediation recommendations
```

## Tools and technologies

- bWAPP
- XAMPP / Apache / MySQL
- OWASP ZAP
- Web security testing concepts
- HTTP / web application behaviour
- Authentication and session management
- Access control
- XSS / HTML Injection
- Vulnerability assessment
- Risk analysis
- Security remediation

> **Note about Burp Suite:** the original thesis discusses Burp Suite as a web-security testing tool, but the documented practical test section specifically names bWAPP, vulnerability scanning, and OWASP ZAP. Therefore this repository does not claim that Burp Suite was used for the documented practical findings.

## Evidence

The `evidence/` directory contains selected figures extracted from the original thesis and focused on the practical testing and ZAP results.

See [`docs/evidence-map.md`](docs/evidence-map.md) for context.

## Why this project matters

This project demonstrates that I can:

- approach a web application from a security-testing perspective;
- identify authentication and authorization weaknesses;
- reproduce vulnerabilities in an intentionally vulnerable environment;
- analyse security impact rather than only identify technical defects;
- use an automated scanner and interpret its findings;
- translate findings into concrete remediation recommendations;
- document security work in a structured way.

## Academic source

Original thesis:

**“Тестування на безпеку веб-сайтів, ідентифікація ризиків та застосування ефективних методів захисту”**

Master's qualification work, Cybersecurity, V. N. Karazin Kharkiv National University, 2023.
