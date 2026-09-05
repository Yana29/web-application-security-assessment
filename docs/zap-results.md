# OWASP ZAP Scan Results

## Documented result

Target: local bWAPP instance (`http://localhost` in the original lab report)

Total observations: **18**

| Risk | Count | Percentage |
|---|---:|---:|
| High | 0 | 0.0% |
| Medium | 7 | 38.9% |
| Low | 5 | 27.8% |
| Informational | 6 | 33.3% |

## Medium-risk observations

The thesis identifies examples including:

- missing anti-clickjacking protection;
- missing Anti-CSRF tokens;
- missing Content Security Policy (CSP);
- directory browsing.

## Low-risk observations

Examples include:

- missing `X-Content-Type-Options`;
- missing `HttpOnly` cookie attribute;
- information disclosure through HTTP headers.

## Interpretation

The automated scan did not report a High-risk observation in the documented context. The largest group was Medium risk, so remediation should begin with those findings.

Scanner output should be reviewed manually: automated results are findings to validate, not a substitute for human security analysis.
