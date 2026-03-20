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
        Feb-Mar 2026 : Fork 24 Waves packages
                     : Rebrand to @decentralchain
                     : Monorepo consolidation (Nx + pnpm)
                     : 3,747 tests passing, 0 vulnerabilities
    section Phase 2 — Wallet & DeFi
        Q2 2026 : DCW Mobile Wallets (Android + iOS)
                : DCW Browser Extension
                : DCC AMM Swap launch
                : Staking platform
    section Phase 3 — Cross-Chain & Apps
        Q3 2026 : Sol-to-DCC Gateway (ZK proofs)
                : Liquidity Locker
                : DecentralScan v2
                : RWA tokenization platform
    section Phase 4 — CR Coin Economy
        Q3-Q4 2026 : CR Coin Quests & Raffles
                   : CRC Marketplace
                   : CRC Casino 2.0
                   : Airdrop campaigns
    section Phase 5 — Ecosystem Growth
        Q1 2027 : Decentral Exchange production
                : Docs portal relaunch
                : Partner integrations
                : Node infrastructure scaling
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

    section Phase 2 — Wallet & DeFi
    DCW Android Development                :b1, 2026-04-01, 60d
    DCW iOS Development                    :b2, 2026-04-01, 60d
    DCW Browser Extension                  :b3, 2026-04-01, 45d
    DCC AMM Swap                           :b4, 2026-04-15, 45d
    DCC Staking Platform                   :b5, 2026-04-15, 35d
    DCC Website Redesign                   :b6, 2026-04-01, 30d
    Wallet Beta Release                    :milestone, m2, 2026-06-01, 0d
    DeFi Suite Live                        :milestone, m3, 2026-06-15, 0d

    section Phase 3 — Cross-Chain & Infrastructure
    Sol-to-DCC Gateway (ZK Proofs)         :c1, 2026-06-15, 60d
    Liquidity Locker                       :c2, 2026-06-15, 35d
    DecentralScan v2                       :c3, 2026-07-01, 45d
    RWA Tokenization Platform              :c4, 2026-07-01, 60d
    Data Writer App                        :c5, 2026-07-15, 30d
    Exchange Security Hardening            :c6, 2026-06-15, 30d
    Cross-Chain Live                       :milestone, m4, 2026-08-15, 0d

    section Phase 4 — CR Coin Economy
    CR Coin Website Relaunch               :d1, 2026-08-01, 21d
    CR Coin Quests App                     :d2, 2026-08-15, 35d
    CR Coin Raffles App                    :d3, 2026-08-15, 35d
    CRC Marketplace                        :d4, 2026-09-01, 45d
    CRC Casino 2.0                         :d5, 2026-09-01, 45d
    DCC Airdrop Bot Campaigns              :d6, 2026-09-15, 21d
    CR Coin Economy Live                   :milestone, m5, 2026-10-15, 0d

    section Phase 5 — Ecosystem Growth
    Decentral Exchange Production          :e1, 2026-10-15, 45d
    Docs Portal Relaunch                   :e2, 2026-10-15, 30d
    Node Infrastructure Scaling            :e3, 2026-11-01, 35d
    Partner & Exchange Integrations        :e4, 2026-11-15, 45d
    Ecosystem v1.0 Complete                :milestone, m6, 2027-01-01, 0d
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
    Exchange Sec Hardening       :s5, 2026-06-15, 30d

    section Mobile & Extension
    DCW Android                  :w1, 2026-04-01, 60d
    DCW iOS                      :w2, 2026-04-01, 60d
    DCW Extension                :w3, 2026-04-01, 45d
    Wallet Security Audit        :w4, 2026-05-15, 14d

    section DeFi & Cross-Chain
    AMM Swap Smart Contracts     :df1, 2026-04-15, 30d
    Swap Frontend                :df2, 2026-05-15, 21d
    Staking Contracts & UI       :df3, 2026-04-15, 35d
    Liquidity Locker             :df4, 2026-06-15, 35d
    Sol Gateway ZK Circuits      :df5, 2026-06-15, 45d
    Sol Gateway Bridge UI        :df6, 2026-08-01, 21d

    section Web & Explorer
    decentralchain.io Redesign   :wb1, 2026-04-01, 30d
    DecentralScan v2             :wb2, 2026-07-01, 45d
    docs.decentralchain.io       :wb3, 2026-10-15, 30d
    decentral.exchange Prod      :wb4, 2026-10-15, 45d

    section CR Coin Apps
    crcoin.net Relaunch          :cr1, 2026-08-01, 21d
    Quests App                   :cr2, 2026-08-15, 35d
    Raffles App                  :cr3, 2026-08-15, 35d
    Marketplace                  :cr4, 2026-09-01, 45d
    Casino 2.0                   :cr5, 2026-09-01, 45d
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

    B --> F["DCC AMM Swap"]
    B --> G["DCC Staking"]
    F --> H["Decentral Exchange"]
    G --> H

    E --> I["Sol-to-DCC Gateway<br/>(ZK Proofs)"]
    F --> I
    B --> J["Liquidity Locker"]
    B --> K["RWA Platform"]

    E --> L["CR Coin Quests"]
    E --> M["CR Coin Raffles"]
    L --> N["CRC Marketplace"]
    M --> N
    N --> O["CRC Casino 2.0"]

    I --> P["Ecosystem v1.0"]
    H --> P
    O --> P
    K --> P

    B --> Q["DecentralScan v2"]
    Q --> P
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
| **Phase 2** — Wallet & DeFi | 🟡 In Progress | Q2 2026 | DCW Android/iOS/Extension, AMM Swap, Staking, decentralchain.io |
| **Phase 3** — Cross-Chain & Infra | ⚪ Not Started | Q3 2026 | Sol Gateway (ZK), Liquidity Locker, DecentralScan v2, RWA, Data Writer |
| **Phase 4** — CR Coin Economy | ⚪ Not Started | Q3-Q4 2026 | Quests, Raffles, Marketplace, Casino 2.0, Airdrop campaigns |
| **Phase 5** — Ecosystem Growth | ⚪ Not Started | Q1 2027 | decentral.exchange prod, docs relaunch, partner integrations |

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

### Phase 2 — Wallet & DeFi (Q2 2026)

```mermaid
pie title Phase 2 Effort Distribution
    "DCW Mobile Wallets" : 35
    "DCW Browser Extension" : 15
    "DCC AMM Swap" : 20
    "DCC Staking" : 15
    "Website Redesign" : 15
```

**Goals:**
- Launch DCW (DecentralChain Wallet) on Android and iOS with seed management, transaction signing, and DCC token support
- Ship DCW browser extension (evolution of Cubensis Connect with full modernization — webpack → Vite, Babel → native TS)
- Deploy DCC AMM Swap with constant product formula (on-chain Ride smart contracts)
- Launch DCC Staking platform with LPoS delegation and reward distribution UI
- Redesign decentralchain.io with ecosystem overview, wallet downloads, and developer onboarding

**Key Repositories:**
| Project | Repository | Target |
|---------|-----------|--------|
| DCW Android | `33imattei33/DCW-Android` | Jun 2026 |
| DCW iOS | `33imattei33/DCW-iOS` | Jun 2026 |
| DCW Extension | `33imattei33/DCW-Extension` | May 2026 |
| DCC AMM Swap | `dylanpersonguy/dcc-amm-swap` | Jun 2026 |
| DCC Staking | `dylanpersonguy/dcc-staking` | May 2026 |
| DCC Website | `dylanpersonguy/dcc-website` | May 2026 |

---

### Phase 3 — Cross-Chain & Infrastructure (Q3 2026)

```mermaid
pie title Phase 3 Effort Distribution
    "Sol-to-DCC Gateway (ZK)" : 30
    "DecentralScan v2" : 20
    "RWA Tokenization" : 20
    "Liquidity Locker" : 15
    "Exchange Hardening" : 15
```

**Goals:**
- Build Sol-to-DCC bridge using zero-knowledge proofs for trustless cross-chain asset transfers (Solana ↔ DCC)
- Deploy Liquidity Locker for DeFi project token vesting and LP lock mechanisms
- Launch DecentralScan v2 (decentralscan.com) with improved block explorer, transaction detail, and analytics
- Build RWA (Real World Asset) tokenization platform on DCC — property, carbon credits, securities
- Harden decentral.exchange: fix CORS wildcard, add CSP headers, non-root Docker, IP spoofing fix
- Ship Data Writer App for on-chain data transactions

**Key Repositories:**
| Project | Repository | Target |
|---------|-----------|--------|
| Sol-to-DCC Gateway | `dylanpersonguy/sol-gateway-dcc-zk-proof` | Aug 2026 |
| Liquidity Locker | `dylanpersonguy/dcc-liquidity-locker` | Jul 2026 |
| RWA Platform | `33imattei33/decentralchain-rwa` | Sep 2026 |
| Data Writer App | `dylanpersonguy/decentralchain-data-writer-app` | Aug 2026 |

**Security Hardening for decentral.exchange:**

| Issue | Severity | Fix |
|-------|----------|-----|
| `Access-Control-Allow-Origin: *` | Critical | Restrict to `decentral.exchange` origin |
| No Content-Security-Policy | High | Add strict CSP headers |
| `set_real_ip_from 0.0.0.0/0` | High | Restrict to known proxy CIDRs |
| Docker runs as root | High | Switch to non-root user |
| 6 test files for 405 source files | Medium | Increase to 80%+ coverage |

---

### Phase 4 — CR Coin Social Economy (Q3–Q4 2026)

```mermaid
pie title Phase 4 Effort Distribution
    "CRC Marketplace" : 25
    "CRC Casino 2.0" : 25
    "CR Coin Quests" : 15
    "CR Coin Raffles" : 15
    "Airdrop Campaigns" : 10
    "CR Coin Website" : 10
```

**Goals:**
- Relaunch crcoin.net with updated branding, wallet integration, and ecosystem links
- Ship CR Coin Quests app — gamified tasks that reward users with CR Coin (social currency for Costa Rica)
- Launch CR Coin Raffles app — on-chain raffle system with transparent draws via Ride smart contracts
- Build CRC Marketplace for peer-to-peer trading of DCC-based tokens and NFTs
- Deploy CRC Casino 2.0 with provably fair gaming on DCC blockchain
- Run DCC Airdrop Bot campaigns for community growth and token distribution

**Key Repositories:**
| Project | Repository | Target |
|---------|-----------|--------|
| CR Coin Website | `dylanpersonguy/cr-coin-website` | Aug 2026 |
| CR Coin Quests | `dylanpersonguy/cr-coin-quests-app` | Sep 2026 |
| CR Coin Raffles | `dylanpersonguy/cr-coin-raffles-app` | Sep 2026 |
| CRC Marketplace | `dylanpersonguy/crc-marketplace-app` | Oct 2026 |
| CRC Casino 2.0 | `dylanpersonguy/crc-casino-2.0` | Oct 2026 |
| DCC Airdrop Bot | `dylanpersonguy/dcc-airdrop` | Oct 2026 |

---

### Phase 5 — Ecosystem Growth (Q1 2027)

```mermaid
pie title Phase 5 Effort Distribution
    "Decentral Exchange Prod" : 25
    "Node Infrastructure" : 20
    "Partner Integrations" : 20
    "Docs Portal" : 15
    "Marketing & Community" : 20
```

**Goals:**
- Launch decentral.exchange in production with full security hardening, order matching, and DCC/token trading pairs
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
| DCC AMM Swap | `dylanpersonguy/dcc-amm-swap` | In development |
| DCC Staking | `dylanpersonguy/dcc-staking` | In development |
| Liquidity Locker | `dylanpersonguy/dcc-liquidity-locker` | In development |
| Sol-to-DCC Gateway | `dylanpersonguy/sol-gateway-dcc-zk-proof` | In development |
| RWA Tokenization | `33imattei33/decentralchain-rwa` | In development |

### CR Coin Economy

| Project | Repository | Live URL | Status |
|---------|-----------|----------|--------|
| CR Coin Website | `dylanpersonguy/cr-coin-website` | crcoin.net | Active |
| CR Coin Quests | `dylanpersonguy/cr-coin-quests-app` | — | In development |
| CR Coin Raffles | `dylanpersonguy/cr-coin-raffles-app` | — | In development |
| CRC Marketplace | `dylanpersonguy/crc-marketplace-app` | — | In development |
| CRC Casino 2.0 | `dylanpersonguy/crc-casino-2.0` | — | In development |
| DCC Airdrop Bot | `dylanpersonguy/dcc-airdrop` | — | In development |

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
| Data Writer App | `dylanpersonguy/decentralchain-data-writer-app` | In development |

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
| 1.0 | 2026-03-19 | Complete roadmap with real ecosystem data — SDK status, wallets, DeFi, CR Coin, cross-chain, web properties |
| 0.1 | 2026-03-19 | Initial placeholder roadmap |

---

*Last updated: March 19, 2026*
