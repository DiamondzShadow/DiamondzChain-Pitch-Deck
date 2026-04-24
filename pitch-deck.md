---
marp: true
theme: default
paginate: true
header: 'Shadow Diamondz · DiamondzChain'
footer: 'April 2026 · Confidential'
style: |
  section { font-family: 'Inter', -apple-system, sans-serif; }
  h1 { color: #0b1021; letter-spacing: -0.02em; }
  h2 { color: #1a2b4a; letter-spacing: -0.01em; }
  code { background: #f4f4f8; padding: 2px 6px; border-radius: 4px; }
  table { font-size: 0.85em; }
  .status-live { color: #10803a; font-weight: 600; }
  .status-staged { color: #b56a00; font-weight: 600; }
  .status-dev { color: #6a6a85; font-weight: 600; }
---

<!-- _class: lead -->

# Shadow Diamondz

## A multi-chain DeFi + creator-economy ecosystem
### where every protocol fee buys SDM

Arbitrum · Polygon · Base · HyperEVM · DiamondzChain L3

April 2026

---

## The pitch in one line

> Shadow Diamondz runs **five live products** on **four EVM chains**, and every fee from every product routes to a **single revenue router** that buys SDM and seeds liquidity.

One chain, one market, one unfragmented buyback.

---

## The problem we set out to solve

DeFi ecosystems today fragment three ways:

- **Across chains** — a "multi-chain protocol" usually means N forked deployments that don't share a treasury or a token market
- **Across products** — yield, trading, lending, and NFTs live in separate protocols with separate fee flows
- **Across fee schedules** — every product collects fees into a different bucket that may or may not ever benefit the token

Result: users pay fees to multiple surfaces, but no single token captures the ecosystem's composite value.

---

## What we built

Five **live** products sharing one fee router and one token treasury:

| # | Product | Status |
|---|---------|--------|
| 1 | **ShadowVault V15** — 9 USDC yield vaults across Arb / Polygon / HyperEVM | <span class="status-live">LIVE</span> |
| 2 | **ShadowzDex** — intent-based DEX at dex.diamondz.one | <span class="status-live">LIVE</span> |
| 3 | **EcosystemMarketplace + LendingPool v1.4** — NFT marketplace + NFT-backed lending | <span class="status-live">LIVE</span> |
| 4 | **CrabbyTV** — live streaming + FAST-channel distribution + on-chain creator progression | <span class="status-live">LIVE</span> |
| 5 | **OnlyShellz** — Patreon-alternative, USDC-native recurring subscriptions | <span class="status-dev">PHASE 1 — IN DEV</span> |

---

## Product 1 — ShadowVault V15

9 USDC-denominated yield vaults across three chains:

- **Arbitrum**: Morpho · GMX · Aave · Fluid
- **Polygon**: Aave · Gains · Aave · C4C
- **HyperEVM**: HyperSkin (HLP) · ShadowPass

Every deposit mints a **live-value financial NFT** — an ERC-721 that can be listed on the marketplace, borrowed against in LendingPool v1.4, or bridged across chains.

Lock tiers FLEX → 365-day with up to **3.0× share multiplier**. USDC in, USDC out — no adapter may return a non-USDC asset on withdraw.

---

## Product 2 — ShadowzDex

Intent-based DEX with an off-chain attestor and on-chain verification:

- User signs an **11-field intent** naming the tokens, minOut, and Chainlink oracle
- Attestor picks the venue: **0x aggregator**, Uniswap V2/V3, Sushi V2, or V15 direct
- Router re-checks `minOut` and oracle staleness on-chain before dispatch
- Cross-chain intents settle over the **Arbitrum ↔ Polygon ↔ Base CCIP mesh**

$1 USDC Arb ↔ Base round-trip proven on mainnet. First cross-chain intent settlement in the ecosystem.

---

## Product 3 — Financial NFTs + NFT-Backed Lending

Every ShadowVault deposit is a tradable, borrowable primitive:

- **List on EcosystemMarketplace** — USDC sales, 2.5% royalty to treasury
- **Borrow against in LendingPool v1.4** — up to 50% LTV, **yield-to-loan auto-repay slider**
- **Bridge cross-chain** — Poly ↔ Arb via Chainlink CCIP, Hyper ↔ Arb via LayerZero
- **Priced live** by `NFTValuer v2` with Chainlink staleness guards

The NFT is the position. Selling transfers the underlying vault deposit.

---

## Product 4 — CrabbyTV

Creator-first live streaming platform on Arbitrum:

- **FAST channel distribution** — Roku, Fire TV, Apple TV. The single hardest thing to replicate.
- **Co-host multi-video grid** — multiple creators in one stream
- **AI co-host** — Beyond Presence avatar + Claude + 11Labs, **$0.99/min** USDC pre-deposit to the treasury Safe
- **On-chain creator progression** — `CrabbyTVMVP.sol` tracks Milestone Units → Creator Credits → Reputation Badges → Wavz Score

CrabbyTV is the **consumer wedge**. A fan who tips in CRABBY is one deposit away from holding SDM.

---

## Product 5 — OnlyShellz

Patreon-style crypto memberships. **Phase 1 in development.**

Architecturally different from every subscription platform on the market:

- **Fan owns the subscription** — USDC allowance granted to a contract, never custodied by the platform
- **Keeper-driven recurring pulls** — a cron, not a custodian. No payout holds. No deplatforming.
- **Live-tipping UX** — on-screen real-time contributions during streams
- Shares the **AI co-host stack** with CrabbyTV

Positioned as a Patreon alternative, not an OnlyFans alternative. This distinction is load-bearing.

---

## Architecture — multi-chain by design, not by fork

```
                    ┌── Arbitrum One ──────────── CANONICAL HOME
                    │   SDM · V15 A-D · ShadowzDex · Marketplace · Lending · Safe
                    │
   CCIP mesh ───────┼── Polygon ──────────── V15 A-D · NFT locker · zSDM
                    │   (fees bridge to Arb)
                    │
                    ├── Base ──────────── SDM · DEX settlement · zSDM
                    │   (fees bridge to Arb)
                    │
   LayerZero ───────┴── HyperEVM ──────────── V15 Pool E + F · ShadowPass · zSDM
                        (fees bridge to Arb)

   DiamondzChain L3 (ID 7791) — zwToken mirror via 2-of-3 bridge
   Solana — devnet deployed, mainnet cost measured (3.376 SOL)
```

Fees collected anywhere in the system bridge to the Arbitrum Safe before the buyback fires. One chain, one market, one liquidity pool.

---

## The fee flywheel — every product, one router

| Source | Rate | Where it lands |
|--------|------|----------------|
| V15 withdrawal (on-time / FLEX) | 1.2% | Seeder V2 |
| V15 protocol yield fee | 5% | Seeder V2 |
| LPFeeGateway (any V2/V3 LP deposit) | 0.03% | Arb Safe |
| ShadowzDex intent fee (post-FeeVault) | 5–20 bps | FeeVault → Seeder V2 |
| EcosystemMarketplace royalty | 2.5% | Arb Safe |
| LendingPool v1.4 interest split | 10% of interest | Arb Safe |
| DiamondzChain Bridge | 0.30% / flat | BridgeFeeDAO |
| AI co-host (CrabbyTV / OnlyShellz) | $0.99/min USDC | Arb Safe |

**Seeder V2 splits 50/50**: SDM buyback on DODO DPP + Uniswap V3 LP seeding, and Arbitrum treasury Safe.

---

## Why the buyback isn't per-chain

Fees collected on Polygon and HyperEVM **bridge to Arbitrum first** — via Chainlink CCIP and LayerZero respectively — before any buyback executes.

Multiple per-chain buyback sites would:

- Fragment SDM liquidity across chains
- Dilute the flywheel on every fee dollar
- Create arbitrage surface that leaks treasury value

One chain, one market, one buyback. The cost is a bridge fee per batch; the benefit is every SDM holder sits in the same liquidity pool no matter where fees originated.

---

## Protocol integrations — built on the right primitives

| Protocol | What we use | Where |
|----------|-------------|-------|
| **0x** | Swap API v2 via AllowanceHolder | V15 rebalancer, ShadowzDex aggregator venue, Token Tester (7-size quote probes) |
| **Uniswap** | V3 SDM/USDC canonical pool (1% fee) + V2/V3 paste-box for any pool | LP surface, LPFeeGateway 0.03% hook |
| **Chainlink** | CCIP mesh + Data Feeds with staleness guards | Cross-chain SDM, DEX settlement, NFT value push, wrapper ratios, intent oracles |

Every external primitive we lean on is **audited, permissioned at the token-pool level where applicable, and replaceable**. We do not reinvent cross-chain messaging or price oracles.

---

## SDM token economy

| Token | Role |
|-------|------|
| **SDM** | Ecosystem governance + utility. ERC677, 4B initial / 5B max supply. CCIP-native on Arb + Poly + Base + HyperEVM. |
| **vSDM** | ERC20Votes wrap for DAO voting |
| **wSDM / gSDM / sSDM** | BTC-backed / gold-backed / stablecoin-backed wrappers with Chainlink-fed ratio enforcement |
| **DBV** | Diamond Basket Vault ERC-4626 shares — diversified basket |
| **CRABBY** | CrabbyTV platform utility |
| **zwSDM** | DiamondzChain L3 mirror |

Governance via OpenZeppelin Governor + TimelockController. DAO can move economic parameters; Safe retains pause / rescue / adapter-swap rights. No Ownable in production.

---

## Security posture

- **Per-chain Gnosis Safes** — one Safe per chain per purpose, cross-checked before any admin-handoff deploy
- **AccessControl, not Ownable** — in every production contract
- **USDC-native adapters only** — no adapter returns a non-USDC asset on withdraw. Pendle / Gamma / ICHI / Balancer swap-step adapters were eliminated, not fixed.
- **Every adapter has `rescueToken`** — rule enforced ecosystem-wide after a prior adapter stranded funds
- **Chainlink staleness guards** — stale feeds revert, not fall back. Stale valuation is the highest-risk input to NFT-backed lending.
- **LayerZero DVN config read-back-verified** on both libraries on both chains for the Hyper ↔ Arb bridge

---

## Traction

<!-- Fill via Blockscout before sending -->

| Metric | Value |
|--------|-------|
| Total TVL across 9 V15 vaults | [PLACEHOLDER — Blockscout] |
| Unique depositors | [PLACEHOLDER] |
| SDM holders | [PLACEHOLDER — Blockscout] |
| ShadowzDex 30-day volume | [PLACEHOLDER] |
| LPFeeGateway fees → treasury | [PLACEHOLDER] |
| SDM/USDC Uni V3 pool liquidity | [PLACEHOLDER] |
| Cumulative SDM buyback | [PLACEHOLDER] |
| Active NFT-backed loans | [PLACEHOLDER] |

All metrics are queryable on-chain via Blockscout; this slide should be regenerated from live data immediately before any investor meeting.

---

## The V11 → V15 shipping record

We iterate in public, and every iteration hardened the design:

- **V11** — first live deposit vault, Aave E-Mode recursive lending (still used in DBV)
- **V13** — weighted pool vault, archived (architectural flaws caught pre-scale)
- **V14** — abandoned in favor of V15 after audit found structural issues
- **V15** — current. No swap-step adapters. No shared-registry collisions. Every adapter has `rescueToken`. Whitelist-open. Direct deposits, not routed through a buggy IntentRouter.

A pattern investors should recognize: we ship, we learn from bugs that happen on small capital, we harden, we re-ship. V15 is the product of that discipline.

---

## Roadmap — next 12 months

**Q2 2026**
- OnlyShellz Phase 1 public launch
- ShadowzDex FeeVault + SwapIntent extension + keeper
- V15 Base port (same-day port of Arb V15)

**Q3 2026**
- Solana mainnet deployment (devnet complete, 3.376 SOL cost measured)
- Kamino / Jupiter JLP / Sanctum / Maple pools
- V15 Sonic + BNB ports

**Q4 2026**
- Berachain V15 port
- Uniswap V4 hooks evaluation for ShadowzDex
- CrabbyTV FAST channel expansion

**H1 2027**
- DiamondzChain L3 production deposits
- Full DAO transition (phase 4 — Safe renounces emergency cancel)

---

## Team

[PLACEHOLDER]

- Founder / CEO — [name, background, prior exits]
- Head of Engineering — [name, background]
- Lead Smart Contract Engineer — [name, background]
- Head of Growth — [name, background]

Advisors: [PLACEHOLDER]

Prior experience to highlight: Solidity production at scale, multi-chain operational experience, creator-economy product experience.

---

## The ask

[PLACEHOLDER]

**Raise:** $[AMOUNT] at $[VALUATION] valuation.

**Use of funds:**

| Bucket | Allocation |
|--------|-----------|
| Engineering (contracts + keepers + UI) | [__]% |
| Security (audits, bounty programs) | [__]% |
| Operations (GCP infra, RPC, monitoring) | [__]% |
| Growth (creator acquisition, DeFi partnerships) | [__]% |
| Treasury runway / liquidity seeding | [__]% |

Current treasury runway at current burn: [__] months.

---

## Risks & honest caveats

We'd rather tell you now than have you find them in due diligence:

- **HyperEVM is not Blockscout-indexed** — our Hyper metrics rely on HypurrScan, which has less maturity than Blockscout
- **Solana is devnet only** — mainnet deployment is funded and planned but not yet executed
- **ShadowzDex intent fees are spec'd but not collected yet** — FeeVault extension is pending
- **Smart-contract exposure** — DeFi is inherently risky; adapters interact with third-party protocols (Aave, Morpho, GMX, Fluid, Gains, C4C) that carry their own risk
- **Prior iterations lost small capital during testing** — documented in internal runbooks; contributed to current adapter-design rules
- **OnlyShellz is not live** — Phase 1 punch-list remains before public launch
- **DAO transition is incomplete** — currently Phase 1 (multisig-owned); target state is Phase 4 (fully autonomous)
- **Regulatory uncertainty** — USDC dependencies, token economy, and creator payments all sit in evolving regulatory perimeters

---

## Why this bet is valuable

1. **Real products shipping**, not a whitepaper with a roadmap
2. **A single fee flywheel** across five products — SDM captures ecosystem value by construction, not by hope
3. **Multi-chain done right** — one canonical token market, fees bridged to it, no per-chain forks fighting each other
4. **Creator economy layer** — top-of-funnel the DeFi side does not have on its own
5. **Discipline visible in the shipping record** — iteration pattern that compounds

This is an ecosystem, not a product. It's already running.

---

## Contact

**Website** — [diamondzshadow.info](https://diamondzshadow.info)
**DEX** — [dex.diamondz.one](https://dex.diamondz.one)
**CrabbyTV** — [crabbytv.com](https://crabbytv.com)
**Whitepaper v4.0** — [github.com/DiamondzShadow/White-Paper](https://github.com/DiamondzShadow/White-Paper)
**GitHub** — [github.com/DiamondzShadow](https://github.com/DiamondzShadow)
**Email** — [development@diamondzshadow.com](mailto:development@diamondzshadow.com)
**Twitter / X** — [@DiamondShadoM](https://twitter.com/DiamondShadoM)
**Discord** — [discord.gg/diamondzshadow](https://discord.gg/diamondzshadow)

---

<!-- _class: lead -->

# Thank you

*Built by Shadow Diamondz Game + Movie Development, Inc.*
*© 2025–2026. All rights reserved.*
