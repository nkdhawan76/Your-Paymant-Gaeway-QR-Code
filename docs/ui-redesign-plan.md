# UI/UX Redesign & Implementation Plan — YOUPI PG Sovereign Merchant Admin

## 1. Executive Summary & Audit Baseline

This document defines the comprehensive UI/UX overhaul of the **YOUPI PG / Your Paymant Gateway Merchant Operating System** (`http://localhost:6001`), elevating the interface to an institutional-grade, clean fintech dashboard standard (inspired by Stripe, Linear, and modern banking platforms) while strictly preserving all sovereign payment state machines, real-time SSE streaming, UPI single-use slot invariants, and verification guarantees.

### 1.1 Architecture & Stack Audit
- **Frontend Stack**: Native HTML5, Vanilla Modern CSS (Tailored Design Tokens), Vanilla Modern ES6+ JavaScript (Zero bloat, high responsiveness, zero third-party framework bundle overhead).
- **Icons**: Clean, inline, feather/lucide-style SVG icons (consistent 16px/18px stroke-width 2-2.2, crisp vectors).
- **Typography**: Inter / Plus Jakarta Sans (UI text) + JetBrains Mono (Order IDs, amounts, hashes, UTRs, code tokens).
- **Active Routes & Sub-views**:
  - `#/operations`:
    - Sub-view 1.1: Live Monitor & Slots (`#subViewOpsLive`)
    - Sub-view 1.2: Counter Desk POS Cashier (`#subViewOpsCounter`)
    - Sub-view 1.3: Transactions Ledger (`#subViewOpsTransactions`)
    - Sub-view 1.4: Payment Observers Status (`#subViewOpsObservers`)
  - `#/settings`:
    - Sub-view 2.1: Brand Identity & Live Mockup (`#subViewStoreBrand`)
    - Sub-view 2.2: Receiving Accounts / VPAs (`#subViewStoreVpa`)
    - Sub-view 2.3: Selling Modes & Modalities (`#subViewStoreModes`)
  - `#/developer`:
    - Sub-view 3.1: Payment Simulator (`#subViewDevSimulator`)
    - Sub-view 3.2: System Supervisor & Cluster Control (`#subViewDevSupervisor`)
    - Sub-view 3.3: Cloudflare Tunnel Orchestration (`#subViewDevCloudflare`)
    - Sub-view 3.4: Webhooks & Secrets (`#subViewDevWebhooks`)
    - Sub-view 3.5: Android SMS Gateway Companion Hub (`#subViewDevAndroid`)
    - Sub-view 3.6: Gmail & WhatsApp Direct Ingestion Protocols (`#subViewDevProtocols`)
  - `#/security`:
    - Sub-view 4.1: Banned Fraudsters & Device Fingerprints (`#subViewSecBanned`)
    - Sub-view 4.2: Security Events Stream (`#subViewSecEvents`)
    - Sub-view 4.3: Ban Audit History (`#subViewSecHistory`)

---

## 2. Standardized Design Tokens & Color Palette

All surfaces, borders, and typography derive from centralized CSS custom properties:

```css
:root {
  /* Surface & Canvas Tokens */
  --bg-app: #F5F8FC;               /* Canvas background */
  --bg-surface: #FFFFFF;           /* Card & panel surfaces */
  --bg-surface-subtle: #F8FAFC;    /* Table headers, code blocks, idle states */
  --border: #E2E8F0;               /* Primary subtle border */
  --border-focus: #2563EB;         /* Accessible focus ring */

  /* Text & Contrast Tokens */
  --text-primary: #0F172A;         /* Slate 900 high contrast */
  --text-secondary: #5B6B84;       /* Slate 600 secondary helper */
  --text-muted: #94A3B8;           /* Slate 400 captions & placeholders */

  /* Semantic Action & State Tokens */
  --primary: #2563EB;              /* Primary brand blue */
  --primary-hover: #1D4ED8;        /* Hover blue */
  --primary-light: #EFF6FF;        /* Soft blue badge / selection */
  --success: #059669;              /* Emerald green for verified/online */
  --success-light: #ECFDF5;
  --warning: #D97706;              /* Amber for queued/waiting */
  --warning-light: #FEF3C7;
  --danger: #DC2626;               /* Rose/Red for destructive/counter pending */
  --danger-light: #FEF2F2;
  --info: #0284C7;                 /* Sky blue for in-progress */
  --info-light: #F0F9FF;

  /* Typography & Elevation */
  --font-sans: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  --font-mono: 'JetBrains Mono', ui-monospace, SFMono-Regular, Menlo, monospace;
  --shadow-sm: 0 1px 2px 0 rgba(15, 23, 42, 0.05);
  --shadow-card: 0 1px 3px 0 rgba(15, 23, 42, 0.04), 0 1px 2px -1px rgba(15, 23, 42, 0.04);
  --radius-sm: 6px;
  --radius-md: 10px;
  --radius-lg: 14px;
}
```

---

## 3. Structural Layout & Component Hierarchy

### 3.1 Topbar
- **Left**: YOUPI PG / Your Paymant Gateway logo badge + title + `v2.4 Sovereign` chip.
- **Center**: Store Status indicator (`Port 5000: ONLINE`) + Receiving UPI VPA chip + Environment tag (`LOCALHOST`).
- **Right**: Light/Dark Theme toggle + Real-Time Syncing pulse indicator + Merchant Account indicator.

### 3.2 Primary & Sub-Navigation
- **Primary Tabs**: Segmented tab control with crisp icon + label (`Daily Merchant Operations`, `Store Settings`, `Developer & Infrastructure Hub`, `Security`).
- **Sub-Navigation**: Soft pill segmented control with active indicator and smooth section switching.

### 3.3 KPI Metric Cards
- 4 primary cards:
  1. **Today's Volume**: Live INR sum with Emerald icon tile & `0% Fee Direct Settlement` tag.
  2. **Successful Payments**: Count with Blue checkmark tile & `Real-Time Verified` tag.
  3. **In Waiting Queue**: Count with Amber users tile & `Deterministic FIFO` tag.
  4. **Pending Counter Payments**: Count with Rose cashier till tile & `POS Cashier Till` tag.
- 2 verification tier cards:
  1. **Single Verified (1 Source)**: Cellular SMS or Gmail parsing.
  2. **Dual Verified (2 Sources: SMS + Gmail)**: Independent channel corroboration with `Zero Mismatch Guarantee`.

### 3.4 UPI Dynamic Slot Ownership & Invariant Arbiter
- **Active Slot (5-Minute Window)**:
  - Display remaining countdown timer with visual progress bar.
  - Locked Order ID and Amount formatted in INR.
  - High-fidelity idle state when no customer is actively checking out.
- **Processing Slot (30s Verification Window)**:
  - Display countdown with Amber progress bar.
  - Active bank notification parsing indicator.
  - High-fidelity standby state when idle.
- **FIFO Waiting Customer Queue Table**:
  - Columns: `Queue #`, `Order`, `Amount`, `Status`, `Enqueued At`.
  - Empty state with clean vector icon and informative caption.
  - Confirm dialog for queue clearing action.

---

## 4. Verification & QA Matrix
1. **Visual Consistency**: Verified across Chrome, Edge, and responsive viewports (1920px desktop down to tablet).
2. **Data Invariants**: 100% real data from Payment Core REST API (`http://localhost:6100`) and WebSocket/SSE streams.
3. **Automated Integration Tests**: `apps/merchant-admin/src/__tests__/merchant-admin.test.js` passes 100%.
