# Security Policy

## Supported Versions

We recommend running the latest release on the `main` branch with Node.js `>= 20.0.0` LTS.

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |
| < 1.0.0 | :x:                |

---

## Reporting a Vulnerability

Security is a primary concern for payment infrastructure. If you discover a security vulnerability or potential threat in **Your Paymant Gateway**, please report it responsibly:

1. **GitHub Security Advisories (Preferred)**:
   Navigate to the repository's **Security** tab and click **Report a vulnerability** to privately submit details to the maintainers.
2. **Do Not Open Public Issues**:
   Please do not report vulnerabilities through public GitHub issues, discussions, or social channels until an official fix has been published.

### What to Include in Your Report

- A description of the vulnerability and its potential impact.
- Clear steps to reproduce (proof of concept, code snippet, or HTTP request trace).
- Affected components or versions.
- Any suggested remediations or mitigations.

### Response Timeline

- **Acknowledgment**: Within 48 hours of initial report.
- **Assessment**: Maintainers will confirm the validity and severity.
- **Remediation**: A patched release will be prepared and published alongside a coordinated security advisory.

---

## Operational Security Responsibilities

- **Merchant Credentials**: Users and merchants must generate and configure their own encryption keys (`ENCRYPTION_MASTER_KEY`), JWT secrets (`JWT_SECRET`), webhook signing secrets, and OAuth credentials.
- **Never Commit Secrets**: Ensure `.env` and SQLite databases remain in `.gitignore`.
- **Authoritative Verification**: Always verify webhook signatures via HMAC-SHA256 using raw request bytes before fulfilling orders. Never rely exclusively on client-side browser events.
