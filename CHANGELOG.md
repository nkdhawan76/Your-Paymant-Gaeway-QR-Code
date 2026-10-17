# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Standardized open-source contribution guidelines (`CONTRIBUTING.md`).
- Contributor Covenant Code of Conduct (`CODE_OF_CONDUCT.md`).
- Private vulnerability reporting policy (`SECURITY.md`).
- GitHub Actions automated CI workflow for multi-node test and typecheck verification.
- GitHub Issue & Pull Request templates.

## [1.0.0] - 2026-10-18

### Added

- **Core Payment Engine**: Sovereign, self-hosted UPI payment gateway engine supporting sub-second dynamic QR generation and deep linking.
- **Universal One-Script Integration**: `[data-youpi-pay]` declarative button auto-binding and programmatic `Youpi.pay()` modal API.
- **Dual Observation Mesh**: Bank SMS observer and Gmail notification listener for zero-fee, direct-to-bank P2P payment credit verification.
- **Counter Payment Modes**: Support for Cash on Counter, Card on Counter, and Cash on Delivery (COD) workflows.
- **WhatsApp Pre-Checkout OTP**: Real-time 6-digit phone number authentication before session generation.
- **Cryptographic Security**: HMAC-SHA256 authoritative server-to-server webhook delivery, AES-256 encrypted token storage, and strict raw-body signature validation.
- **Control Center & Merchant Admin**: Web dashboards for managing active receiving VPAs, devices, transaction queues, and live audit logs.
- **Regression Test Suite**: 31 end-to-end and unit test suites covering the state machine, webhook retries, device binding, and security pipelines.
- **Clean Persistence Architecture**: SQLite Native WAL mode support with zero-dependency standalone setup and PostgreSQL multi-instance readiness.
