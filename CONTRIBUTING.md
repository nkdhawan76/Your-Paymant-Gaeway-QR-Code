# Contributing to Your Paymant Gateway

Thank you for your interest in contributing to **Your Paymant Gateway**! As a sovereign, self-hosted UPI payment gateway, we welcome contributions that improve stability, security, observer accuracy, and developer ergonomics.

---

## Code of Conduct

All contributors and maintainers are expected to abide by our [Code of Conduct](CODE_OF_CONDUCT.md). Please read it to understand our community standards.

---

## Development Workflow

### 1. Prerequisites

- **Node.js**: `>= 20.0.0` (LTS recommended)
- **npm**: `>= 10.0.0`
- **Git**
- Optional: Android Studio for native Android Kotlin Observer testing.

### 2. Fork and Clone

```bash
git clone https://github.com/nkdhawan76/Your-Paymant-Gaeway-QR-Code.git
cd Your-Paymant-Gaeway-QR-Code
```

### 3. Install Dependencies

```bash
npm install
```

This configures npm workspaces across `packages/*` and `apps/*`.

### 4. Setup Environment

Copy the example environment template:

```bash
cp .env.example .env
```

> **Security Notice**: Never commit `.env` or any file containing live API keys, tokens, or bank credentials.

### 5. Running Quality Checks Locally

Before submitting a pull request, ensure all local validation commands pass:

```bash
# Typecheck
npm run typecheck

# Build
npm run build

# Run all 31 regression test suites
npm test

# Dependency security audit
npm audit
```

---

## Branching & Commit Conventions

### Branch Naming

- Features: `feature/description-of-feature`
- Fixes: `fix/issue-description`
- Docs: `docs/what-changed`
- Refactor: `refactor/scope`

### Commit Messages

We follow [Conventional Commits](https://www.conventionalcommits.org/):

- `feat: add CRED deep-link intent handling`
- `fix: resolve race condition in SMS parser timestamp attribution`
- `docs: update webhook verification examples`
- `test: add unit tests for observer heartbeat monitor`

---

## Pull Request Guidelines

1. **One Focus Per PR**: Keep pull requests focused on a single change or fix.
2. **Add Tests**: If you fix a bug or add functionality, include unit or integration tests in the corresponding `__tests__/` directory.
3. **No Hard-Coded Credentials**: Never introduce hardcoded credentials, live phone numbers, bank accounts, or tokens.
4. **Pass CI**: Ensure the GitHub Actions CI workflow succeeds on all checks.
5. **Self-Review**: Review your own `git diff` before opening the pull request.

---

## Reporting Security Issues

Please **do not** open public GitHub issues for security vulnerabilities. Review our [Security Policy](SECURITY.md) for disclosure guidelines.
