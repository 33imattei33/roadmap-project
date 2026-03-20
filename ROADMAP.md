# DecentralChain Ecosystem Roadmap

> Comprehensive development roadmap for the DecentralChain (DCC) blockchain ecosystem — SDK, wallets, DeFi, cross-chain bridges, CR Coin social economy, and web properties. Maintained by Blockchain Costa Rica / Decentral-America.

---

## Table of Contents

1. [Overview](#overview)
2. [Ecosystem Map](#ecosystem-map)
3. [Development Timeline](#development-timeline)
4. [Workstream Allocation](#workstream-allocation)
5. [Milestone Dependency Flow](#milestone-dependency-flow)
6. [Risk Assessment](#risk-assessment)
7. [Delivery Tracker](#delivery-tracker)
8. [Phase Details](#phase-details)
9. [Ecosystem Project Registry](#ecosystem-project-registry)
10. [Version History](#version-history)

---

## Overview

```mermaid
timeline
    title DecentralChain Ecosystem Roadmap
    section Phase 1 — SDK & Monorepo
        Feb-Mar 2026 : Fork 24 Waves packages ✅
                     : Rebrand to @decentralchain ✅
                     : Monorepo consolidation (Nx + pnpm) ✅
                     : 3,747 tests passing, 0 vulnerabilities ✅
    section Phase 2 — DeFi & Apps (90% Complete)
        Mar-Apr 2026 : AMM Swap — mainnet, testing/debug needed
                     : Staking — mainnet, testing/debug needed
                     : Liquidity Locker — mainnet, testing/debug needed
                     : Sol Gateway (ZK) — mainnet, testing/debug needed
    section Phase 3 — CR Coin Economy (90% Complete)
        Mar-Apr 2026 : CR Coin Website, Quests, Raffles — testing/debug
                     : CRC Marketplace, Casino 2.0 — testing/debug
                     : Airdrop Bot, Data Writer — testing/debug
    section Phase 4 — Wallets & QA
        Q2 2026 : DCW Mobile Wallets (Android + iOS)
                : DCW Browser Extension
                : Full QA pass on all 12 mainnet apps
                : Security audit across DeFi + CR Coin
    section Phase 5 — Ecosystem Growth
        Q3 2026 : Decentral Exchange production
                : DecentralScan v2
                : RWA tokenization platform
                : Docs relaunch, partner integrations
```

---

## Ecosystem Map

```mermaid
flowchart TB
    subgraph CORE["Core Protocol"]
        NODE["DCC Node<br/>(Waves fork — Scala/JVM)"]
        SDK["@decentralchain/* SDK<br/>22 libraries — TypeScript"]
    end

    subgraph WALLETS["Wallets"]
        DCW_A["DCW Android"]
        DCW_I["DCW iOS"]
        DCW_E["DCW Extension<br/>(Cubensis Connect)"]
    end

    subgraph DEFI["DeFi Infrastructure"]
        SWAP["DCC AMM Swap"]
        STAKE["DCC Staking"]
        LOCK["Liquidity Locker"]
        GATEWAY["Sol-to-DCC Gateway<br/>(ZK Proofs)"]
        RWA["RWA Tokenization"]
    end

    subgraph CRCOIN["CR Coin Social Economy"]
        CRC_WEB["CR Coin Website"]
        QUESTS["CR Coin Quests"]
        RAFFLES["CR Coin Raffles"]
        MARKET["CRC Marketplace"]
        CASINO["CRC Casino 2.0"]
        AIRDROP["DCC Airdrop Bot"]
    end

    subgraph WEB["Web Properties"]
        WEBSITE["decentralchain.io"]
        SCAN["DecentralScan"]
        EXCHANGE["decentral.exchange"]
        DOCS["docs.decentralchain.io"]
        DATA["Data Writer App"]
    end

    NODE --> SDK
    SDK --> WALLETS
    SDK --> DEFI
    SDK --> WEB
    WALLETS --> CRCOIN
    DEFI --> EXCHANGE
    SWAP --> EXCHANGE
```

---

## Development Timeline

```mermaid
gantt
    title DecentralChain Development Timeline
    dateFormat  YYYY-MM-DD
    axisFormat  %b %Y
    todayMarker stroke-width:3px,stroke:#ff0000

    section Phase 1 — SDK & Monorepo
    Waves Fork & Rebrand (24 pkgs)         :done, a1, 2026-02-27, 4d
    Security Fixes (signer, node-api-js)   :done, a2, 2025-07-01, 14d
    Modernize Toolchain (ESM, Biome, tsdown) :done, a3, 2026-03-05, 3d
    Cubensis Connect Rebrand               :done, a4, 2026-03-08, 2d
    Swap Client Fork & Migration           :done, a5, 2026-03-10, 1d
    Production Hardening (141 dead files)   :done, a6, 2026-03-11, 2d
    Monorepo Consolidation (Nx import)     :done, a7, 2026-03-13, 4d
    Resolve Cognito Pool Ownership (P0)    :crit, a8, 2026-03-19, 14d
    Replace @keeper-wallet/waves-crypto    :crit, a9, 2026-03-19, 21d
    SDK Phase 1 Complete                   :milestone, m1, 2026-04-15, 0d

    section Phase 2 — DeFi Testing & Debug (90% Built)
    AMM Swap — Testing & Debug             :active, b1, 2026-03-19, 28d
    Staking — Testing & Debug              :active, b2, 2026-03-19, 28d
    Liquidity Locker — Testing & Debug     :active, b3, 2026-03-19, 28d
    Sol Gateway (ZK) — Testing & Debug     :active, b4, 2026-03-19, 35d
    Data Writer — Testing & Debug          :active, b5, 2026-03-19, 21d
    DCC Website Redesign                   :b6, 2026-04-01, 30d
    DeFi QA Complete                       :milestone, m2, 2026-04-20, 0d

    section Phase 3 — CR Coin Testing & Debug (90% Built)
    CR Coin Website — Testing & Debug      :active, c1, 2026-03-19, 21d
    CR Coin Quests — Testing & Debug       :active, c2, 2026-03-19, 28d
    CR Coin Raffles — Testing & Debug      :active, c3, 2026-03-19, 28d
    CRC Marketplace — Testing & Debug      :active, c4, 2026-03-19, 35d
    CRC Casino 2.0 — Testing & Debug       :active, c5, 2026-03-19, 35d
    DCC Airdrop Bot — Testing & Debug      :active, c6, 2026-03-19, 21d
    CR Coin QA Complete                    :milestone, m3, 2026-04-25, 0d

    section Phase 4 — Wallets & Security
    DCW Android Development                :d1, 2026-04-01, 60d
    DCW iOS Development                    :d2, 2026-04-01, 60d
    DCW Browser Extension                  :d3, 2026-04-01, 45d
    Security Audit (DeFi + CR Coin)        :d4, 2026-04-20, 21d
    Exchange Security Hardening            :d5, 2026-04-20, 30d
    Wallet Beta Release                    :milestone, m4, 2026-06-01, 0d

    section Phase 5 — Ecosystem Growth
    Decentral Exchange Production          :e1, 2026-06-15, 45d
    DecentralScan v2                       :e2, 2026-06-15, 45d
    RWA Tokenization Platform              :e3, 2026-07-01, 60d
    Docs Portal Relaunch                   :e4, 2026-06-15, 30d
    Node Infrastructure Scaling            :e5, 2026-07-01, 35d
    Partner & Exchange Integrations        :e6, 2026-07-15, 45d
    Ecosystem v1.0 Complete                :milestone, m5, 2026-09-01, 0d
```

---

## Workstream Allocation

```mermaid
gantt
    title Team Workstream Breakdown
    dateFormat  YYYY-MM-DD
    axisFormat  %b %Y

    section SDK & Core
    Monorepo Stabilization       :s1, 2026-03-19, 28d
    Cognito Migration (P0)       :crit, s2, 2026-03-19, 14d
    waves-crypto Replacement     :s3, 2026-03-19, 21d
    SDK CI/CD in Nx              :s4, 2026-04-01, 14d
    Exchange Sec Hardening       :s5, 2026-04-20, 30d

    section DeFi QA (90% Built — on Mainnet)
    AMM Swap Testing             :active, df1, 2026-03-19, 28d
    Staking Testing              :active, df2, 2026-03-19, 28d
    Liquidity Locker Testing     :active, df3, 2026-03-19, 28d
    Sol Gateway Testing          :active, df4, 2026-03-19, 35d
    Data Writer Testing          :active, df5, 2026-03-19, 21d
    DeFi Security Audit          :df6, 2026-04-20, 21d

    section CR Coin QA (90% Built — on Mainnet)
    CR Coin Website QA           :active, cr1, 2026-03-19, 21d
    Quests App QA                :active, cr2, 2026-03-19, 28d
    Raffles App QA               :active, cr3, 2026-03-19, 28d
    Marketplace QA               :active, cr4, 2026-03-19, 35d
    Casino 2.0 QA                :active, cr5, 2026-03-19, 35d
    Airdrop Bot QA               :active, cr6, 2026-03-19, 21d

    section Mobile & Extension
    DCW Android                  :w1, 2026-04-01, 60d
    DCW iOS                      :w2, 2026-04-01, 60d
    DCW Extension                :w3, 2026-04-01, 45d
    Wallet Security Audit        :w4, 2026-05-15, 14d

    section Web & Explorer
    decentralchain.io Redesign   :wb1, 2026-04-01, 30d
    DecentralScan v2             :wb2, 2026-06-15, 45d
    docs.decentralchain.io       :wb3, 2026-06-15, 30d
    decentral.exchange Prod      :wb4, 2026-06-15, 45d
```

---

## Milestone Dependency Flow

```mermaid
flowchart LR
    A["SDK Fork & Rebrand<br/>✅ Done"] --> B["Monorepo Consolidation<br/>✅ Done"]
    B --> C["Cognito P0 Fix"]
    B --> D["waves-crypto Replacement"]

    C --> E["DCW Wallets<br/>(Android, iOS, Extension)"]
    D --> E

    B --> F["DCC AMM Swap<br/>🟡 90% — QA needed"]
    B --> G["DCC Staking<br/>🟡 90% — QA needed"]
    B --> H["Liquidity Locker<br/>🟡 90% — QA needed"]
    B --> I["Sol Gateway ZK<br/>🟡 90% — QA needed"]
    B --> J["Data Writer<br/>🟡 90% — QA needed"]

    B --> K["CR Coin Website<br/>🟡 90% — QA needed"]
    B --> L["CR Coin Quests<br/>🟡 90% — QA needed"]
    B --> M["CR Coin Raffles<br/>🟡 90% — QA needed"]
    B --> N["CRC Marketplace<br/>🟡 90% — QA needed"]
    B --> O["CRC Casino 2.0<br/>🟡 90% — QA needed"]
    B --> P["Airdrop Bot<br/>🟡 90% — QA needed"]

    F --> Q["Security Audit<br/>(DeFi + CR Coin)"]
    G --> Q
    H --> Q
    L --> Q
    N --> Q
    O --> Q

    Q --> R["Decentral Exchange"]
    F --> R
    G --> R

    E --> S["Ecosystem v1.0"]
    R --> S
    Q --> S
    I --> S

    B --> T["DecentralScan v2"]
    T --> S
    B --> U["RWA Platform"]
    U --> S
```

---

## Risk Assessment

```mermaid
quadrantChart
    title Risk Assessment — Impact vs Likelihood
    x-axis Low Likelihood --> High Likelihood
    y-axis Low Impact --> High Impact
    quadrant-1 Monitor Closely
    quadrant-2 Critical — Mitigate Now
    quadrant-3 Accept Risk
    quadrant-4 Contingency Plan
    Cognito Pool Ownership: [0.6, 0.95]
    Waves Supply Chain Deps: [0.5, 0.85]
    Exchange CORS Wildcard: [0.7, 0.75]
    Sol Gateway ZK Complexity: [0.55, 0.65]
    Key Person Dependency: [0.6, 0.7]
    Waves Upstream Divergence: [0.4, 0.5]
    ride-lang Unforked Dep: [0.3, 0.4]
    Chain ID Misconfiguration: [0.35, 0.8]
    Docker Root in Exchange: [0.65, 0.6]
    Mobile Store Rejection: [0.4, 0.55]
```

---

## Delivery Tracker

| Phase | Status | Target | Key Deliverables |
|-------|--------|--------|-----------------|
| **Phase 1** — SDK & Monorepo | 🟢 Complete | Mar 2026 | 22 SDK libs migrated, monorepo consolidated, 3,747 tests, 0 vulns |
| **Phase 1b** — Critical Fixes | 🔴 Blocked | Apr 2026 | Cognito P0 resolution, @keeper-wallet/waves-crypto removal |
| **Phase 2** — DeFi Testing & Debug | 🟡 In Progress (90%) | Apr 2026 | AMM Swap, Staking, Liquidity Locker, Sol Gateway, Data Writer — all on mainnet, QA needed |
| **Phase 3** — CR Coin Testing & Debug | 🟡 In Progress (90%) | Apr 2026 | CR Coin Website, Quests, Raffles, Marketplace, Casino 2.0, Airdrop Bot — all on mainnet, QA needed |
| **Phase 4** — Wallets & Security | 🟡 In Progress | Q2 2026 | DCW Android/iOS/Extension, security audit on all DeFi + CR Coin apps |
| **Phase 5** — Ecosystem Growth | ⚪ Not Started | Q3 2026 | decentral.exchange prod, DecentralScan v2, RWA, docs relaunch, partner integrations |

---

## Phase Details

### Phase 1 — SDK & Monorepo (Feb–Mar 2026) — COMPLETE

```mermaid
pie title Phase 1 Effort Distribution
    "Fork & Rebrand (24 packages)" : 25
    "Modernize Toolchain" : 20
    "Security Fixes & Hardening" : 20
    "Monorepo Consolidation" : 20
    "Governance Docs & Audit" : 15
```

**Completed:**
- Forked 24 Waves packages → `@decentralchain/*` with full git history
- Modernized beyond upstream: ESM-only, TypeScript 5.9 strict, Biome 2.x, Vitest 4.x, tsdown
- Monorepo consolidated with Nx 22.x + pnpm 10.x (workspace protocol, computation caching)
- 3,747+ tests passing, 0 npm audit vulnerabilities, 0 `Math.random()` / `eval()` in src
- Cubensis Connect wallet extension rebrand (10 locales, icons, network URLs)
- Swap client reverse-engineered from deleted `@keeper-wallet/swap-client`
- 141+ dead files removed, `exactOptionalPropertyTypes` enabled in 19/24 packages

**Open Critical Items (Phase 1b):**

| Priority | Issue | Impact |
|----------|-------|--------|
| **P0** | AWS Cognito pools (`eu-central-1_AXIpDLJQx`, `eu-central-1_6Bo3FEwt5`) — verify DCC ownership or migrate | Waves could revoke access to user seeds |
| **P1** | `@keeper-wallet/waves-crypto` used in 21 files of cubensis-connect | Supply-chain risk — fork as `@decentralchain/wallet-crypto` |
| **P1** | `keeper-wallet.app` domains in cubensis-connect whitelist | Waves-controlled domains |
| **Medium** | `chainId` defaults to `'L'` in transactions & node-api-js, not DCC mainnet `'?'` | Wrong chain targeted by default |

---

### Phase 2 — DeFi Testing & Debug (Mar–Apr 2026) — 90% COMPLETE

> All 5 DeFi projects are fully structured and running on mainnet. Remaining work is comprehensive testing, bug fixes, and hardening before public launch.

```mermaid
pie title Phase 2 Effort Distribution
    "Testing & Bug Fixes" : 45
    "Security Hardening" : 25
    "Performance Optimization" : 15
    "Documentation" : 15
```

**Current State:** All running on mainnet, 90% complete.

| Project | Repository | Mainnet | Remaining Work |
|---------|-----------|:-------:|----------------|
| DCC AMM Swap | `dylanpersonguy/dcc-amm-swap` | ✅ | Testing, edge-case debugging |
| DCC Staking | `dylanpersonguy/dcc-staking` | ✅ | Testing, edge-case debugging |
| Liquidity Locker | `dylanpersonguy/dcc-liquidity-locker` | ✅ | Testing, edge-case debugging |
| Sol-to-DCC Gateway | `dylanpersonguy/sol-gateway-dcc-zk-proof` | ✅ | Testing, ZK proof verification |
| Data Writer App | `dylanpersonguy/decentralchain-data-writer-app` | ✅ | Testing, edge-case debugging |

**Goals:**
- Comprehensive test suites for all 5 DeFi projects (unit, integration, mainnet e2e)
- Edge-case debugging: zero amounts, max values, concurrent transactions, network failures
- Security review of smart contract interactions and transaction signing flows
- Performance testing under load for AMM Swap and Staking
- ZK proof verification and bridge reliability for Sol Gateway

---

### Phase 3 — CR Coin Testing & Debug (Mar–Apr 2026) — 90% COMPLETE

> All 6 CR Coin economy projects are fully structured and running on mainnet. Remaining work is comprehensive testing, bug fixes, and UX polish before public launch.

```mermaid
pie title Phase 3 Effort Distribution
    "Testing & Bug Fixes" : 40
    "UX Polish" : 20
    "Security Review" : 20
    "Documentation" : 10
    "Airdrop Campaign Prep" : 10
```

**Current State:** All running on mainnet, 90% complete.

| Project | Repository | Mainnet | Remaining Work |
|---------|-----------|:-------:|----------------|
| CR Coin Website | `dylanpersonguy/cr-coin-website` | ✅ | Testing, content finalization |
| CR Coin Quests | `dylanpersonguy/cr-coin-quests-app` | ✅ | Testing, quest logic debugging |
| CR Coin Raffles | `dylanpersonguy/cr-coin-raffles-app` | ✅ | Testing, draw mechanism verification |
| CRC Marketplace | `dylanpersonguy/crc-marketplace-app` | ✅ | Testing, transaction flow debugging |
| CRC Casino 2.0 | `dylanpersonguy/crc-casino-2.0` | ✅ | Testing, provably fair verification |
| DCC Airdrop Bot | `dylanpersonguy/dcc-airdrop` | ✅ | Testing, distribution logic debugging |

**Goals:**
- Comprehensive test suites for all 6 CR Coin projects
- Verify on-chain raffle draw fairness and quest reward distribution
- Security review of marketplace transaction flows and casino game logic
- UX testing across all CR Coin apps for consistent user experience
- Prepare airdrop bot for community launch campaigns

---

### Phase 4 — Wallets & Security Audit (Q2 2026)

```mermaid
pie title Phase 4 Effort Distribution
    "DCW Mobile Wallets" : 35
    "DCW Browser Extension" : 15
    "Security Audit (DeFi + CR Coin)" : 25
    "Exchange Hardening" : 15
    "Website Redesign" : 10
```

**Goals:**
- Launch DCW (DecentralChain Wallet) on Android and iOS with seed management, transaction signing, and DCC token support
- Ship DCW browser extension (evolution of Cubensis Connect — webpack → Vite, Babel → native TS)
- Run security audit across all 12 mainnet apps (DeFi + CR Coin) before public launch announcements
- Harden decentral.exchange: fix CORS wildcard, add CSP headers, non-root Docker, IP spoofing fix
- Redesign decentralchain.io with ecosystem overview, wallet downloads, and developer onboarding

**Key Repositories:**
| Project | Repository | Target |
|---------|-----------|--------|
| DCW Android | `33imattei33/DCW-Android` | Jun 2026 |
| DCW iOS | `33imattei33/DCW-iOS` | Jun 2026 |
| DCW Extension | `33imattei33/DCW-Extension` | May 2026 |
| DCC Website | `dylanpersonguy/dcc-website` | May 2026 |

**Security Hardening for decentral.exchange:**

| Issue | Severity | Fix |
|-------|----------|-----|
| `Access-Control-Allow-Origin: *` | Critical | Restrict to `decentral.exchange` origin |
| No Content-Security-Policy | High | Add strict CSP headers |
| `set_real_ip_from 0.0.0.0/0` | High | Restrict to known proxy CIDRs |
| Docker runs as root | High | Switch to non-root user |
| 6 test files for 405 source files | Medium | Increase to 80%+ coverage |

---

### Phase 5 — Ecosystem Growth (Q3 2026)

```mermaid
pie title Phase 5 Effort Distribution
    "Decentral Exchange Prod" : 20
    "DecentralScan v2" : 15
    "RWA Tokenization" : 15
    "Node Infrastructure" : 15
    "Partner Integrations" : 15
    "Docs Portal" : 10
    "Marketing & Community" : 10
```

**Goals:**
- Launch decentral.exchange in production with full security hardening, order matching, and DCC/token trading pairs
- Ship DecentralScan v2 with improved block explorer, analytics, and transaction detail
- Launch RWA (Real World Asset) tokenization platform on DCC
- Relaunch docs.decentralchain.io with SDK reference, Ride tutorials, API docs, and developer guides
- Scale node infrastructure — additional mainnet/testnet/stagenet nodes, monitoring, and alerting
- Partner integrations — CEX listings, cross-chain bridges, DeFi protocol partnerships
- Community growth via marketing campaigns, developer grants, and hackathons

---

## Ecosystem Project Registry

### Core Infrastructure

| Project | Repository | Live URL | Status |
|---------|-----------|----------|--------|
| DCC Node | `wavesplatform/Waves` (upstream) | — | Running (Scala/JVM) |
| SDK Monorepo | `Decentral-America/*` | npm: `@decentralchain/*` | 22 libs published |
| Cubensis Connect | monorepo: `apps/cubensis-connect` | — | Rebranded, modernizing |
| Exchange | monorepo: `apps/exchange` | decentral.exchange | Security hardening needed |
| Explorer | monorepo: `apps/explorer` | — | Migrated |

### Wallets

| Project | Repository | Platform | Status |
|---------|-----------|----------|--------|
| DCW Android | `33imattei33/DCW-Android` | Android | In development |
| DCW iOS | `33imattei33/DCW-iOS` | iOS | In development |
| DCW Extension | `33imattei33/DCW-Extension` | Chrome/Firefox | In development |

### DeFi

| Project | Repository | Status |
|---------|-----------|--------|
| DCC AMM Swap | `dylanpersonguy/dcc-amm-swap` | 90% — Mainnet, QA needed |
| DCC Staking | `dylanpersonguy/dcc-staking` | 90% — Mainnet, QA needed |
| Liquidity Locker | `dylanpersonguy/dcc-liquidity-locker` | 90% — Mainnet, QA needed |
| Sol-to-DCC Gateway | `dylanpersonguy/sol-gateway-dcc-zk-proof` | 90% — Mainnet, QA needed |
| RWA Tokenization | `33imattei33/decentralchain-rwa` | In development |

### CR Coin Economy

| Project | Repository | Live URL | Status |
|---------|-----------|----------|--------|
| CR Coin Website | `dylanpersonguy/cr-coin-website` | crcoin.net | 90% — Mainnet, QA needed |
| CR Coin Quests | `dylanpersonguy/cr-coin-quests-app` | — | 90% — Mainnet, QA needed |
| CR Coin Raffles | `dylanpersonguy/cr-coin-raffles-app` | — | 90% — Mainnet, QA needed |
| CRC Marketplace | `dylanpersonguy/crc-marketplace-app` | — | 90% — Mainnet, QA needed |
| CRC Casino 2.0 | `dylanpersonguy/crc-casino-2.0` | — | 90% — Mainnet, QA needed |
| DCC Airdrop Bot | `dylanpersonguy/dcc-airdrop` | — | 90% — Mainnet, QA needed |

### Web Properties

| Property | URL | Status |
|----------|-----|--------|
| Main Website | decentralchain.io | Active |
| Block Explorer | decentralscan.com | Active |
| Explorer Beta | beta.decentralscan.com | Beta |
| DEX | decentral.exchange | Pre-production |
| Documentation | docs.decentralchain.io | Active |
| CR Coin | crcoin.net | Active |

### Utilities

| Project | Repository | Status |
|---------|-----------|--------|
| Data Writer App | `dylanpersonguy/decentralchain-data-writer-app` | 90% — Mainnet, QA needed |

---

## Network Infrastructure

| Service | Endpoint | Status |
|---------|----------|--------|
| Mainnet Node | `mainnet-node.decentralchain.io` | Live |
| Testnet Node | `testnet-node.decentralchain.io` | Live |
| Stagenet Node | `stagenet-node.decentralchain.io` | Live |
| Mainnet Matcher | `mainnet-matcher.decentralchain.io` | Live |
| Testnet Matcher | `matcher.decentralchain.io` | Live |
| Data Service API | `api.decentralchain.io` | Live |
| Swap API | `swap-api.decentralchain.io` | Live |
| Identity API | `id.decentralchain.io/api` | Live |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.1 | 2026-03-19 | Updated 12 projects to 90% complete (mainnet deployed, QA/debug phase). Restructured phases to reflect actual progress |
| 1.0 | 2026-03-19 | Complete roadmap with real ecosystem data — SDK status, wallets, DeFi, CR Coin, cross-chain, web properties |
| 0.1 | 2026-03-19 | Initial placeholder roadmap |

---

*Last updated: March 19, 2026*
