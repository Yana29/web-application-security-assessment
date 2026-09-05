# Methodology

## Objective

The original thesis defines the objective as researching and performing active security scanning of a web application, demonstrating common vulnerabilities, analysing risk-identification approaches, and selecting effective protection measures.

## Test environment

The documented practical environment used:

- XAMPP
- Apache
- MySQL
- local bWAPP instance

The target was the intentionally vulnerable laboratory application running locally.

## Manual testing

The practical section documented testing of:

1. Broken Access Control — Restrict Folder Access
2. Broken Authentication and Session Management — Insecure Login Forms
3. Logout Management
4. Administrative Portals
5. HTML Injection — Reflected (GET)
6. HTML Injection — Reflected (POST)
7. XSS — Reflected (GET)

For each demonstrated weakness, the thesis describes the observed behaviour and discusses the security consequences and mitigation measures.

## Automated testing

OWASP ZAP was used for active scanning.

The thesis documents:

- scan configuration;
- included risk levels;
- confidence levels;
- scanner output;
- distribution of findings by risk;
- remediation recommendations.

The documented result contained 18 observations: 7 medium, 5 low, and 6 informational.

## Risk interpretation

The portfolio uses the same risk distribution documented in the thesis. It does not reinterpret the original findings as CVSS scores because the thesis does not provide a CVSS scoring table for these observations.
