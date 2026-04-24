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

## We built a blockchain.
## Then we built the DeFi and creator economy on top of it.
### — and every protocol fee buys SDM

DiamondzChain L3 · Arbitrum · Polygon · Base · HyperEVM

April 2026

---

## The pitch in one line

> Shadow Diamondz **operates its own L3 blockchain (DiamondzChain, Chain ID 7791)** and **five live products** across four additional EVM chains. Every fee from every product routes to a **single revenue router** that buys SDM and seeds liquidity.

We run the rails, not just ride them.

---

## The problem we set out to solve

DeFi ecosystems today fragment three ways:

- **Across chains** — a "multi-chain protocol" usually means N forked deployments that don't share a treasury or a token market
- **Across products** — yield, trading, lending, and NFTs live in separate protocols with separate fee flows
- **Across fee schedules** — every product collects fees into a different bucket that may or may not ever benefit the token

Result: users pay fees to multiple surfaces, but no single token captures the ecosystem's composite value.

---

## What we built

One blockchain, five live products, one fee router, one token treasury:

| # | Layer | Status |
|---|-------|--------|
| 0 | **DiamondzChain L3** — our Arbitrum Orbit AnyTrust L3 (Chain ID 7791) with 2-of-3 validator bridge and 6 zwTokens | <span class="status-live">LIVE</span> |
| 1 | **ShadowVault V15** — 9 USDC yield vaults across Arb / Polygon / HyperEVM | <span class="status-live">LIVE</span> |
| 2 | **ShadowzDex** — intent-based DEX at dex.diamondz.one | <span class="status-live">LIVE</span> |
| 3 | **EcosystemMarketplace + LendingPool v1.4** — NFT marketplace + NFT-backed lending | <span class="status-live">LIVE</span> |
| 4 | **CrabbyTV** — live streaming + FAST-channel distribution + on-chain creator progression | <span class="status-live">LIVE</span> |
| 5 | **OnlyShellz** — Patreon-alternative, USDC-native recurring subscriptions | <span class="status-dev">PHASE 1 — IN DEV</span> |

We don't rent blockspace from someone else's L1. We run our own.

---

## Layer 0 — DiamondzChain L3 <!-- Claude browser: verify RPC/explorer uptime before investor send -->

An **Arbitrum Orbit AnyTrust L3** we operate end-to-end:

| Parameter | Value |
|-----------|-------|
| Chain ID | **7791** |
| RPC | `rpc-mainnet.diamondz.baby` |
| Explorer | `diamondz.tryethernal.com` |
| Bridge validator consensus | 2-of-3 on `BridgeValidatorV2` |
| Bridge mint contract | `0x3d9F35cB176e808E95F8fc665E34407114748967` |
| zwTokens live | 6 (zwUSDC, zwBTC, zwSDM, zwPGOLD, zwARB, zwETH) |
| zDi0 (bridged DBV share) | `0xafa689849631A9420ab8C514EE96E66af205eC4d` |

Why we operate our own L3 rather than rent blockspace:

- **Gas control** — we set the fee structure for our own creator and DeFi flows
- **Ecosystem alignment** — every transaction on DiamondzChain routes value back to the Shadow Diamondz treasury
- **Scale headroom** — creator-economy throughput (tips, streams, subscriptions) is a different load profile than L1 DeFi; we tune for it
- **Sovereignty** — if an L1 changes rules, we don't have to migrate

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

## Architecture — blockchain + multi-chain app, by design

```
  DiamondzChain L3 (Chain ID 7791) ← we operate this chain
  ├── Own RPC, own explorer, own validator set
  ├── 6 zwTokens + zDi0 bridge mirror
  └── Creator-economy + DeFi throughput, our fee rules

                    ┌── Arbitrum One ──────────── SETTLEMENT HOME
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

   Solana — devnet deployed, mainnet cost measured (3.376 SOL)
```

We run DiamondzChain. We settle canonical SDM on Arbitrum. We bridge everywhere else. Fees collected anywhere bridge to the Arbitrum Safe before the buyback fires.

---

## The fee flywheel — every product, one router

| Source | Rate |
|--------|------|
| V15 withdrawal (on-time / FLEX) | 1.2% |
| V15 protocol yield fee | 5% |
| LPFeeGateway (any V2/V3 LP deposit) | 0.03% |
| ShadowzDex intent fee (post-FeeVault) | 5–20 bps |
| EcosystemMarketplace royalty | 2.5% |
| LendingPool v1.4 interest split | 10% of interest |
| AI co-host (CrabbyTV / OnlyShellz) | $0.99/min USDC |

Every fee lands in one revenue router: **50% buys SDM + seeds liquidity, 50% funds operations**. Fees from Polygon and HyperEVM bridge to Arbitrum before the buyback fires — **one chain, one market, no fragmentation**.

---

## SDM token economy

| Token | Role |
|-------|------|
| **SDM** | Governance + utility. ERC677, 4B initial / 5B max. CCIP-native on 4 chains. |
| **vSDM** | Voting wrap for DAO governance |
| **wSDM / gSDM / sSDM** | BTC-backed / gold-backed / stablecoin-backed wrappers |
| **DBV** | Diamond Basket Vault shares — diversified ERC-4626 |

Governance via OpenZeppelin Governor + Timelock. DAO moves economic parameters; per-chain Safes retain pause and emergency rights.

---

## Security posture

- **Per-chain Gnosis Safe multisig** on every production contract — no Ownable surface
- **USDC-native adapter rule** — no adapter may return a non-USDC asset on withdraw, eliminating a whole class of swap-step bugs
- **Chainlink price feeds with enforced staleness** — stale oracles revert, they don't fall back

External audits are the primary line item in our security budget (see Use of Funds).

---

## Traction

<!--
  CLAUDE BROWSER: refresh this slide before every investor send.
  Run these queries on Blockscout MCP. Chain IDs: Arb=42161, Poly=137, Base=8453.
  Replace each [PLACEHOLDER] with the fetched number + append "as of <UTC>" footer.
-->

| Metric | Value |
|--------|-------|
| Total TVL across 9 V15 vaults | [PLACEHOLDER — sum totalAssets() across all V15 vaults, Arb+Poly+Hyper] |
| Unique depositors | [PLACEHOLDER — count unique addresses receiving YieldReceipt NFTs] |
| SDM holders | [PLACEHOLDER — get_address_info on 0x602b869eEf1C9F0487F31776bad8Af3C4A173394] |
| ShadowzDex 30-day volume | [PLACEHOLDER — sum amountIn from IntentRouter transactions, 30d window] |
| LPFeeGateway fees collected | [PLACEHOLDER — sum FeeCollected events from LPFeeGateway] |
| SDM/USDC Uni V3 pool liquidity | [PLACEHOLDER — read_contract liquidity() on 0x25a7f80d191086B77cEB5Bb368C3e71F875Bb4AE] |
| Cumulative SDM buyback | [PLACEHOLDER — sum SDM transfers into Seeder V2 address] |
| Active NFT-backed loans | [PLACEHOLDER — read_contract totalBorrowed() on LendingPool v1.4] |
| DiamondzChain L3 tx count (30d) | [PLACEHOLDER — query diamondz.tryethernal.com API] |
| Revenue reserves (Arb Safe) | [PLACEHOLDER — get_address_info on 0x6052C6559eD5e5CbE74Ac0D42205Ad4A1CFBEd43] |

*Data as of [TIMESTAMP UTC], fetched via Blockscout MCP.*

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

**Yakini Crews** — Founder & Lead Engineer
*[one-line background: prior work, credentials]*
Architected and shipped the full Shadow Diamondz on-chain stack: ShadowVault V11→V15 (9 vaults, 3 chains), ShadowzDex intent router, EcosystemMarketplace + LendingPool v1.4, cross-chain SDM via CCIP + LayerZero.

**Richarda Davis** — Head of Growth
*[one-line background]*
Owns creator acquisition, DeFi BD, and partnership pipeline across the ShadowVault / ShadowzDex / CrabbyTV surfaces.

**Kory Whittaker** — Chief Media Officer
*[one-line background]*
FAST channel strategy, CrabbyTV distribution (Roku / Fire TV / Apple TV), and media rights.

**Shunice Atkins** — Chief Marketing Officer
*[one-line background]*
Ecosystem-wide brand, creator positioning, and go-to-market across DeFi and consumer products.

Advisors: [PLACEHOLDER — add named advisors with one-line each]

---

## The ask

**Raise:** $1.2M – $3.6M seed, sized per investor conviction.
**Valuation anchor:** the live protocol stack — ShadowVault V15 (9 vaults, 3 chains), ShadowzDex (intent DEX + CCIP mesh), DiamondzChain Bridge (L3 + 2-of-3 validator + 6 zwTokens), EcosystemMarketplace + LendingPool v1.4, and the SDM multichain token economy.

### Three scenarios

| Scenario | Raise | Post-money | Investor dilution | Runway |
|----------|-------|------------|-------------------|--------|
| Strategic / minimum | **$1.2M** | **$12M** | ~10% | 18 months |
| Core seed | **$2.4M** | **$18M** | ~13% | 24–30 months |
| Full seed | **$3.6M** | **$24M** | ~15% | 30–36 months |

### Post-raise cap table target (core seed)

| Holder | Allocation |
|--------|-----------|
| Founding team (4 × 12%) | **48%** |
| Investors (seed round) | 13% |
| Option pool (new hires) | 15% |
| Reserved for future rounds & advisors | 24% |

---

### Use of funds — core seed ($2.4M)

| Bucket | % | Amount |
|--------|---|--------|
| **Engineering** — contracts, keepers, UI, multi-chain launches | 40% | $960K |
| **Security** — external audits + bounty program across the stack | 25% | $600K |
| **Growth** — creator acquisition, DeFi BD, partnerships | 25% | $600K |
| **Operations** — infra, monitoring, incident response | 10% | $240K |

Security is the line item we under-fund at our own peril. We currently run on internal audits only — external audits across V15, LendingPool, ShadowzDex, Marketplace, and the bridge are the single highest-value use of funds.

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
