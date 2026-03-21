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
        Feb-Mar 2026 : Monorepo consolidation (Nx + pnpm) ✅
                     : 3,747 tests passing, 0 vulnerabilities ✅
    section Phase 2 — DeFi & Apps
        Mar-Apr 2026 : Sol Gateway (ZK) — mainnet, testing/debug needed (Mar 25)
                     : AMM Swap — mainnet, testing/debug needed (Mar 30)
                     : Liquidity Locker — mainnet, testing/debug needed (Mar 31)
                     : DCC Token Distribution via Liq Locker (Apr 1)
                     : Liquid Staking — mainnet, testing/debug needed (Apr 1)
                     : Deploy DecentralChain.io website (Apr 2)
                     : Airdrop Bot & Eligibility Tracker (Apr 5)
                     : Full Decentral.Exchange launch (Apr 5)
                     : DCC DeFi Ecosystem & Public Sale (Apr 10)
    section Phase 3 — CR Coin Economy
        Apr 2026     : CR Coin Website, Quests, Raffles — testing/debug (Apr 15)
                     : CRC Marketplace, Casino 2.0 — testing/debug (Apr 20)
    section Phase 4 — Wallets & QA
        Q2 2026 : DCW Mobile Wallets (Android + iOS)
                : DCW Browser Extension
                : Full QA pass on all mainnet apps
                : Security audit across DeFi + CR Coin
    section Phase 5 — Ecosystem Growth
        Q3 2026 : DecentralScan v2
                : RWA tokenization platform
                : Docs relaunch, partner integrations
```

---

## Ecosystem Map

```mermaid
flowchart TB
    subgraph CORE["Core Protocol"]
        NODE["DCC Node<br/>(Scala/JVM)"]
        SDK["@decentralchain/* SDK<br/>22 libraries — TypeScript"]
    end

    subgraph WALLETS["Wallets"]
        DCW_A["DCW Android"]
        DCW_I["DCW iOS"]
        DCW_E["DCW Extension<br/>(Cubensis Connect)"]
    end

    subgraph DEFI["DeFi Infrastructure"]
        SWAP["DCC AMM Swap"]
        STAKE["DCC Liquid Staking"]
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
    Security Fixes (signer, node-api-js)   :done, a2, 2025-07-01, 14d
    Modernize Toolchain (ESM, Biome, tsdown) :done, a3, 2026-03-05, 3d
    Cubensis Connect Rebrand               :done, a4, 2026-03-08, 2d
    Swap Client Migration                  :done, a5, 2026-03-10, 1d
    Production Hardening (141 dead files)  :done, a6, 2026-03-11, 2d
    Monorepo Consolidation (Nx import)     :done, a7, 2026-03-13, 4d
    Resolve Cognito Pool Ownership (P0)    :crit, a8, 2026-03-19, 14d
    SDK Phase 1 Complete                   :milestone, m1, 2026-04-02, 0d

    section Phase 2 — DeFi & Apps
    Sol Gateway (ZK) — Testing & Debug     :active, b1, 2026-03-19, 6d
    Add Gateway Interface to Decentral.Exchange :active, b1b, 2026-03-21, 4d
    AMM Swap — Testing & Debug             :active, b2, 2026-03-19, 11d
    Add Swap Interface to Decentral.Exchange :active, b2b, 2026-03-25, 5d
    Liquidity Locker — Testing & Debug     :active, b3, 2026-03-19, 12d
    DCC Token Distribution (Liq Locker)    :b3b, 2026-03-31, 1d
    Liquid Staking — Testing & Debug       :active, b4, 2026-03-19, 13d
    Add Liquid Staking to Decentral.Exchange :active, b4b, 2026-03-25, 7d
    Deploy DecentralChain.io Website       :b5, 2026-03-28, 5d
    Deploy Airdrop Bot & Eligibility Tracker :b6, 2026-04-01, 4d
    Full Decentral.Exchange Launch         :crit, b7, 2026-04-01, 4d
    DCC DeFi Ecosystem & Public Sale Launch :crit, b8, 2026-04-06, 4d
    DeFi Phase Complete                    :milestone, m2, 2026-04-10, 0d

    section Phase 3 — CR Coin Economy
    CR Coin Website — Testing & Debug      :active, c1, 2026-03-21, 25d
    CR Coin Quests — Testing & Debug       :active, c2, 2026-03-21, 25d
    CR Coin Raffles — Testing & Debug      :active, c3, 2026-03-21, 25d
    CRC Marketplace — Testing & Debug      :c4, 2026-04-01, 19d
    CRC Casino 2.0 — Testing & Debug       :c5, 2026-04-01, 19d
    CR Coin QA Complete                    :milestone, m3, 2026-04-20, 0d

    section Phase 4 — Wallets & Security
    DCW Android Development                :d1, 2026-04-20, 60d
    DCW iOS Development                    :d2, 2026-04-20, 60d
    DCW Browser Extension                  :d3, 2026-04-20, 45d
    Security Audit (DeFi + CR Coin)        :d4, 2026-04-20, 21d
    Exchange Security Hardening            :d5, 2026-04-20, 30d
    Wallet Beta Release                    :milestone, m4, 2026-06-20, 0d

    section Phase 5 — Ecosystem Growth
    DecentralScan v2                       :e2, 2026-06-20, 45d
    RWA Tokenization Platform              :e3, 2026-07-01, 60d
    Docs Portal Relaunch                   :e4, 2026-06-20, 30d
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
    Monorepo Stabilization       :s1, 2026-03-19, 14d
    Cognito Migration (P0)       :crit, s2, 2026-03-19, 14d
    SDK CI/CD in Nx              :s4, 2026-04-01, 14d
    Exchange Sec Hardening       :s5, 2026-04-20, 30d

    section DeFi & Apps (Deadlines)
    Sol Gateway (ZK) — Mar 25          :active, df1, 2026-03-19, 6d
    AMM Swap — Mar 30                  :active, df2, 2026-03-19, 11d
    Liquidity Locker — Mar 31          :active, df3, 2026-03-19, 12d
    DCC Token Distribution — Apr 1     :df3b, 2026-03-31, 1d
    Liquid Staking — Apr 1             :active, df4, 2026-03-19, 13d
    DecentralChain.io Website — Apr 2  :df5, 2026-03-28, 5d
    Airdrop Bot & Tracker — Apr 5      :df6, 2026-04-01, 4d
    Decentral.Exchange Launch — Apr 5  :crit, df7, 2026-04-01, 4d
    DeFi Ecosystem & Public Sale — Apr 10 :crit, df8, 2026-04-06, 4d

    section CR Coin (Deadlines)
    CR Coin Website QA — Apr 15        :active, cr1, 2026-03-21, 25d
    Quests App QA — Apr 15             :active, cr2, 2026-03-21, 25d
    Raffles App QA — Apr 15            :active, cr3, 2026-03-21, 25d
    Marketplace QA — Apr 20            :cr4, 2026-04-01, 19d
    Casino 2.0 QA — Apr 20             :cr5, 2026-04-01, 19d

    section Mobile & Extension
    DCW Android                  :w1, 2026-04-20, 60d
    DCW iOS                      :w2, 2026-04-20, 60d
    DCW Extension                :w3, 2026-04-20, 45d
    Wallet Security Audit        :w4, 2026-05-15, 14d

    section Web & Explorer
    DecentralScan v2             :wb2, 2026-06-20, 45d
    docs.decentralchain.io       :wb3, 2026-06-20, 30d
```

---

## Milestone Dependency Flow

```mermaid
flowchart LR
    A["SDK & Monorepo<br/>✅ Done"] --> B["Monorepo Consolidation<br/>✅ Done"]
    B --> C["Cognito P0 Fix"]

    C --> E["DCW Wallets<br/>(Android, iOS, Extension)"]

    B --> F["Sol Gateway (ZK)<br/>🟡 Mar 25"]
    B --> G["AMM Swap<br/>🟡 Mar 30"]
    B --> H["Liquidity Locker<br/>🟡 Mar 31"]
    B --> I["DCC Token Distribution<br/>📅 Apr 1"]
    B --> J["Liquid Staking<br/>🟡 Apr 1"]
    B --> K["DecentralChain.io<br/>📅 Apr 2"]
    B --> L["Airdrop Bot & Tracker<br/>📅 Apr 5"]

    F --> M["Decentral.Exchange<br/>Full Launch 📅 Apr 5"]
    G --> M
    H --> M
    J --> M

    M --> N["DCC DeFi Ecosystem &<br/>Public Sale 📅 Apr 10"]
    I --> N
    L --> N

    B --> O["CR Coin Website, Quests, Raffles<br/>🟡 Apr 15"]
    B --> P["CRC Marketplace, Casino 2.0<br/>🟡 Apr 20"]

    N --> Q["Security Audit<br/>(DeFi + CR Coin)"]
    O --> Q
    P --> Q

    Q --> R["Ecosystem v1.0"]
    E --> R
    Q --> R
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
    Exchange CORS Wildcard: [0.7, 0.75]
    Sol Gateway ZK Complexity: [0.55, 0.65]
    Key Person Dependency: [0.6, 0.7]
    Chain ID Misconfiguration: [0.35, 0.8]
    Docker Root in Exchange: [0.65, 0.6]
    Mobile Store Rejection: [0.4, 0.55]
```

---

## Delivery Tracker

| Phase | Status | Target | Key Deliverables |
|-------|--------|--------|-----------------|
| **Phase 1** — SDK & Monorepo | 🟢 Complete | Mar 2026 | 22 SDK libs migrated, monorepo consolidated, 3,747 tests, 0 vulns |
| **Phase 1b** — Critical Fixes | 🔴 Blocked | Apr 2026 | Cognito P0 resolution |
| **Phase 2** — DeFi & Apps | 🟡 In Progress | Mar 25 – Apr 10 | Sol Gateway, AMM Swap, Liq Locker, Token Distro, Liquid Staking, DecentralChain.io, Airdrop Bot, Decentral.Exchange Launch, DCC Public Sale |
| **Phase 3** — CR Coin Economy | 🟡 In Progress | Apr 15 – Apr 20 | CR Coin Website, Quests, Raffles, CRC Marketplace, Casino 2.0 |
| **Phase 4** — Wallets & Security | ⚪ Not Started | Q2 2026 | DCW Android/iOS/Extension, security audit on all DeFi + CR Coin apps |
| **Phase 5** — Ecosystem Growth | ⚪ Not Started | Q3 2026 | DecentralScan v2, RWA, docs relaunch, partner integrations |

---

## Phase Details

### Phase 1 — SDK & Monorepo (Feb–Mar 2026) — COMPLETE

```mermaid
pie title Phase 1 Effort Distribution
    "SDK Development (22 packages)" : 25
    "Modernize Toolchain" : 20
    "Security Fixes & Hardening" : 20
    "Monorepo Consolidation" : 20
    "Governance Docs & Audit" : 15
```

**Completed:**
- Built and published 22 `@decentralchain/*` SDK packages with full git history
- Modernized toolchain: ESM-only, TypeScript 5.9 strict, Biome 2.x, Vitest 4.x, tsdown
- Monorepo consolidated with Nx 22.x + pnpm 10.x (workspace protocol, computation caching)
- 3,747+ tests passing, 0 npm audit vulnerabilities, 0 `Math.random()` / `eval()` in src
- Cubensis Connect wallet extension rebrand (10 locales, icons, network URLs)
- Swap client reverse-engineered and migrated
- 141+ dead files removed, `exactOptionalPropertyTypes` enabled in 19/24 packages

**Open Critical Items (Phase 1b):**

| Priority | Issue | Impact |
|----------|-------|--------|
| **P0** | AWS Cognito pools (`eu-central-1_AXIpDLJQx`, `eu-central-1_6Bo3FEwt5`) — verify DCC ownership or migrate | Could lose access to user seeds |
| **Medium** | `chainId` defaults to `'L'` in transactions & node-api-js, not DCC mainnet `'?'` | Wrong chain targeted by default |

---

### Phase 2 — DeFi & Apps (Mar–Apr 2026) — IN PROGRESS

> Priority phase with hard deadlines. All DeFi projects are on mainnet. Focus is on testing, debugging, integrating into Decentral.Exchange, launching the DCC ecosystem, and running the public sale.

```mermaid
pie title Phase 2 Effort Distribution
    "Testing & Bug Fixes" : 30
    "Exchange Integration" : 25
    "Website & Airdrop Deployment" : 20
    "Token Distribution & Public Sale" : 15
    "Security Hardening" : 10
```

**Deadlines:**

| # | Deliverable | Status | Deadline |
|---|-------------|--------|----------|
| 1 | **Sol Gateway (ZK)** — mainnet, testing/debug needed. Add gateway interface to Decentral.Exchange | 🟡 In Progress | **Mar 25** |
| 2 | **AMM Swap** — mainnet, testing/debug needed. Add Swap interface to Decentral.Exchange | 🟡 In Progress | **Mar 30** |
| 3 | **Liquidity Locker** — mainnet, testing/debug needed | 🟡 In Progress | **Mar 31** |
| 4 | **Organize DCC Token Distribution** — Lock DCC coins using Liquidity Locker | 📅 Scheduled | **Apr 1** |
| 5 | **Liquid Staking** — mainnet, testing/debug needed. Add liquid staking interface to Decentral.Exchange | 🟡 In Progress | **Apr 1** |
| 6 | **Deploy new DecentralChain.io website** — with roadmap, token distribution, etc. | 📅 Scheduled | **Apr 2** |
| 7 | **Deploy Airdrop Bot and Eligibility Tracker** | 📅 Scheduled | **Apr 5** |
| 8 | **Fully Launched NEW Decentral.Exchange** — all new features: Liq Lock, Gateway, Swap, Liq Staking, etc. | 📅 Scheduled | **Apr 5** |
| 9 | **Full Launch of DCC DeFi Ecosystem & DCC Public Sale** | 📅 Scheduled | **Apr 10** |

**Key Repositories:**

| Project | Repository | Mainnet |
|---------|-----------|:-------:|
| Sol-to-DCC Gateway | `dylanpersonguy/sol-gateway-dcc-zk-proof` | ✅ |
| DCC AMM Swap | `dylanpersonguy/dcc-amm-swap` | ✅ |
| Liquidity Locker | `dylanpersonguy/dcc-liquidity-locker` | ✅ |
| DCC Liquid Staking | `dylanpersonguy/dcc-staking` | ✅ |
| Data Writer App | `dylanpersonguy/decentralchain-data-writer-app` | ✅ |
| DCC Airdrop Bot | `dylanpersonguy/dcc-airdrop` | ✅ |

**Goals:**
- Complete testing & debugging on all DeFi contracts (Sol Gateway, AMM Swap, Liquidity Locker, Liquid Staking)
- Integrate Gateway, Swap, and Liquid Staking interfaces into Decentral.Exchange
- Lock DCC coins via Liquidity Locker for organized token distribution
- Deploy the new DecentralChain.io website with roadmap, token distribution info, and ecosystem overview
- Launch Airdrop Bot with eligibility tracking
- Ship the fully featured Decentral.Exchange with all DeFi features
- Execute full DCC DeFi ecosystem launch and public sale

---

### Phase 3 — CR Coin Economy (Apr 2026) — IN PROGRESS

> CR Coin social economy projects are on mainnet. Focus is testing, bug fixes, and UX polish.

```mermaid
pie title Phase 3 Effort Distribution
    "Testing & Bug Fixes" : 40
    "UX Polish" : 25
    "Security Review" : 20
    "Documentation" : 15
```

**Deadlines:**

| # | Deliverable | Status | Deadline |
|---|-------------|--------|----------|
| 1 | **CR Coin Website, Quests, Raffles** — testing/debug | 🟡 In Progress | **Apr 15** |
| 2 | **CRC Marketplace, Casino 2.0** — testing/debug | 🟡 In Progress | **Apr 20** |

**Key Repositories:**

| Project | Repository | Mainnet |
|---------|-----------|:-------:|
| CR Coin Website | `dylanpersonguy/cr-coin-website` | ✅ |
| CR Coin Quests | `dylanpersonguy/cr-coin-quests-app` | ✅ |
| CR Coin Raffles | `dylanpersonguy/cr-coin-raffles-app` | ✅ |
| CRC Marketplace | `dylanpersonguy/crc-marketplace-app` | ✅ |
| CRC Casino 2.0 | `dylanpersonguy/crc-casino-2.0` | ✅ |

**Goals:**
- Comprehensive test suites for all CR Coin projects
- Verify on-chain raffle draw fairness and quest reward distribution
- Security review of marketplace transaction flows and casino game logic
- UX testing across all CR Coin apps for consistent user experience

---

### Phase 4 — Wallets & Security Audit (Q2 2026)

```mermaid
pie title Phase 4 Effort Distribution
    "DCW Mobile Wallets" : 35
    "DCW Browser Extension" : 15
    "Security Audit (DeFi + CR Coin)" : 25
    "Exchange Hardening" : 15
    "Website Maintenance" : 10
```

**Goals:**
- Launch DCW (DecentralChain Wallet) on Android and iOS with seed management, transaction signing, and DCC token support
- Ship DCW browser extension (evolution of Cubensis Connect — webpack → Vite, Babel → native TS)
- Run security audit across all mainnet apps (DeFi + CR Coin) before public launch announcements
- Harden decentral.exchange: fix CORS wildcard, add CSP headers, non-root Docker, IP spoofing fix

**Key Repositories:**
| Project | Repository | Target |
|---------|-----------|--------|
| DCW Android | `33imattei33/DCW-Android` | Jun 2026 |
| DCW iOS | `33imattei33/DCW-iOS` | Jun 2026 |
| DCW Extension | `33imattei33/DCW-Extension` | May 2026 |

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
    "DecentralScan v2" : 20
    "RWA Tokenization" : 20
    "Node Infrastructure" : 15
    "Partner Integrations" : 15
    "Docs Portal" : 15
    "Marketing & Community" : 15
```

**Goals:**
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
| DCC Node | DecentralChain Node | — | Running (Scala/JVM) |
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
| Sol-to-DCC Gateway | `dylanpersonguy/sol-gateway-dcc-zk-proof` | 🟡 Mainnet — Deadline Mar 25 |
| DCC AMM Swap | `dylanpersonguy/dcc-amm-swap` | 🟡 Mainnet — Deadline Mar 30 |
| Liquidity Locker | `dylanpersonguy/dcc-liquidity-locker` | 🟡 Mainnet — Deadline Mar 31 |
| DCC Liquid Staking | `dylanpersonguy/dcc-staking` | 🟡 Mainnet — Deadline Apr 1 |
| RWA Tokenization | `33imattei33/decentralchain-rwa` | In development |

### CR Coin Economy

| Project | Repository | Live URL | Status |
|---------|-----------|----------|--------|
| CR Coin Website | `dylanpersonguy/cr-coin-website` | crcoin.net | 🟡 Mainnet — Deadline Apr 15 |
| CR Coin Quests | `dylanpersonguy/cr-coin-quests-app` | — | 🟡 Mainnet — Deadline Apr 15 |
| CR Coin Raffles | `dylanpersonguy/cr-coin-raffles-app` | — | 🟡 Mainnet — Deadline Apr 15 |
| CRC Marketplace | `dylanpersonguy/crc-marketplace-app` | — | 🟡 Mainnet — Deadline Apr 20 |
| CRC Casino 2.0 | `dylanpersonguy/crc-casino-2.0` | — | 🟡 Mainnet — Deadline Apr 20 |
| DCC Airdrop Bot | `dylanpersonguy/dcc-airdrop` | — | 📅 Deadline Apr 5 |

### Web Properties

| Property | URL | Status |
|----------|-----|--------|
| Main Website | decentralchain.io | Active — Redesign by Apr 2 |
| Block Explorer | decentralscan.com | Active |
| Explorer Beta | beta.decentralscan.com | Beta |
| DEX | decentral.exchange | Full launch Apr 5 |
| Documentation | docs.decentralchain.io | Active |
| CR Coin | crcoin.net | Active |

### Utilities

| Project | Repository | Status |
|---------|-----------|--------|
| Data Writer App | `dylanpersonguy/decentralchain-data-writer-app` | Mainnet, QA needed |

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
| 2.0 | 2026-03-21 | Roadmap restructured: Phase 2 rewritten with hard deadlines (Mar 25 – Apr 10), Phase 3 deadlines added (Apr 15 – Apr 20), cleaned up branding |
| 1.1 | 2026-03-19 | Updated 12 projects to 90% complete (mainnet deployed, QA/debug phase). Restructured phases to reflect actual progress |
| 1.0 | 2026-03-19 | Complete roadmap with real ecosystem data — SDK status, wallets, DeFi, CR Coin, cross-chain, web properties |
| 0.1 | 2026-03-19 | Initial placeholder roadmap |

---

*Last updated: March 21, 2026*
