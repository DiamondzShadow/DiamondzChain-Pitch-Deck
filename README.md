# Shadow Diamondz — DiamondzChain Pitch Deck

Pitch deck for the Shadow Diamondz ecosystem, v1.0 (April 2026).

Source deck: [`pitch-deck.md`](./pitch-deck.md)

---

## What this deck pitches

Shadow Diamondz is **a blockchain we operate** (DiamondzChain L3, Chain ID 7791) **plus five live products** built on top of it and four additional EVM chains. Every protocol fee across every product routes to a single revenue router that buys SDM and seeds liquidity.

18 slides covering:

1. Cover
2. Pitch in one line
3. The problem
4. What we built
5. **DiamondzChain L3** — our Arbitrum Orbit AnyTrust L3
6–10. Product detail — ShadowVault V15, ShadowzDex, Financial NFTs + Lending, CrabbyTV, OnlyShellz
11. Multi-chain architecture
12. Fee flywheel
13. SDM token economy
14. Security posture
15. V11 → V15 shipping record
16. 12-month roadmap
17. Team
18. Ask — raise / cap table / use of funds
19. Risks & honest caveats
20. Why this bet is valuable
21. Contact

Every product has a status tag: `LIVE` / `IN DEV` / `PLANNED`. The Risks slide lists what we'd rather tell investors than have them find in diligence.

**No traction slide yet** — we'll add it back once we have live metrics worth showing. Placeholder numbers in front of investors is worse than no numbers. The shipped-product evidence across slides 4–10 carries the narrative until then.

---

## For Claude browser (connected to this GitHub repo)

Claude browser can update this deck when connected to GitHub + Blockscout MCP. Useful workflows:

- **Add a traction slide** when live metrics are worth showing — query totals from Blockscout, insert between the Fee Flywheel and SDM Token slides
- **Verify DiamondzChain infrastructure** before an investor send — ping `rpc-mainnet.diamondz.baby` and `diamondz.tryethernal.com`, flag if either is down on slide 5
- **Refresh roadmap** when quarters ship — move shipped items to the V11→V15 record, update remaining dates

### Addresses Claude browser will need

| Contract | Chain | Address |
|----------|-------|---------|
| SDM token | Arbitrum (42161) | `0x602b869eEf1C9F0487F31776bad8Af3C4A173394` |
| Arb Treasury Safe | Arbitrum | `0x6052C6559eD5e5CbE74Ac0D42205Ad4A1CFBEd43` |
| SDM/USDC Uni V3 pool | Arbitrum | `0x25a7f80d191086B77cEB5Bb368C3e71F875Bb4AE` |
| DODO DPP (DBV/USDC) | Arbitrum | `0x781dfce2518b9840e8f0165333bdff3170ef1f9c` |
| Seeder V2 | Arbitrum | `0x23e48B14177b6288b5c961d3000CD2666bdc2550` |
| DBV Vault V3 | Arbitrum | `0xFc2B1DFdeE79139356C3deae983f74FC2aB96855` |
| BridgeMint (DiamondzChain) | DiamondzChain (7791) | `0x3d9F35cB176e808E95F8fc665E34407114748967` |
| BridgeValidatorV2 (DiamondzChain) | DiamondzChain | `0xC239A8647F00EE01587659AA5B169aA21A60779d` |

For the full address set — including partial addresses that need completion before Blockscout queries can run — see [`DiamondzShadow/White-Paper`](https://github.com/DiamondzShadow/White-Paper) § 11 and § 14.

---

## How to render

Written in [Marp](https://marp.app/) markdown. Pick one:

### Option A — VS Code plugin (easiest)

1. Install the **Marp for VS Code** extension
2. Open `pitch-deck.md`
3. Export: `Cmd/Ctrl+Shift+P` → "Marp: Export slide deck" → PDF / PPTX / HTML

### Option B — Marp CLI

```bash
npm install -g @marp-team/marp-cli

marp pitch-deck.md --pdf    # investor-ready PDF
marp pitch-deck.md --pptx   # PowerPoint if investor wants to mark up
marp pitch-deck.md --html   # standalone HTML
```

### Option C — Read raw on GitHub

GitHub renders the markdown as a long page; `---` horizontal rules mark slide boundaries. Fine for quick review, not for presenting.

---

## Before sending

Checklist for any investor send:

- [ ] **Team backgrounds** — one-line bios filled under each named exec
- [ ] **Advisors list** — filled if any are onboard
- [ ] **Roadmap dates** — shifted forward if any have slipped; quarters marked "shipped" where applicable
- [ ] **DiamondzChain status** — RPC + explorer pinged green on slide 5
- [ ] **Render** — fresh PDF / PPTX exported

---

## Versioning

Tag meaningful revisions:

```bash
git tag -a v1.0 -m "Initial pitch deck, April 2026"
git tag -a v1.1 -m "Refreshed traction metrics, May 2026"
```

Investor decks drift quickly; a tagged version lets you re-send a specific point-in-time deck if needed.

---

## License

Internal / confidential. Do not redistribute without permission.

*© 2025–2026 Shadow Diamondz Game + Movie Development, Inc.*
