# Shadow Diamondz — DiamondzChain Pitch Deck

Pitch deck for the Shadow Diamondz ecosystem, v1.0 (April 2026).

Source deck: [`pitch-deck.md`](./pitch-deck.md)

---

## What's in the deck

20 slides covering:

1. Cover
2. Pitch in one line
3. The problem
4. What we built
5. Live products matrix
6–10. Product detail — ShadowVault V15, ShadowzDex, Financial NFTs + Lending, CrabbyTV, OnlyShellz
11. Multi-chain architecture
12. Fee flywheel
13. Why the buyback is single-chain
14. Protocol integrations (0x, Uniswap, Chainlink)
15. SDM token economy
16. Security posture
17. Traction (placeholders — fill from Blockscout)
18. V11 → V15 shipping record
19. 12-month roadmap
20. Team, ask, risks, contact

The deck is deliberately honest: every product has a status tag (LIVE / IN DEV / PLANNED), every metric that isn't in this repo is marked `[PLACEHOLDER]`, and the Risks slide lists what you'd rather tell investors than have them find in diligence.

---

## How to render

The deck is written in [Marp](https://marp.app/) markdown. Pick one:

### Option A — VS Code plugin (easiest)

1. Install the **Marp for VS Code** extension
2. Open `pitch-deck.md`
3. Export: `Cmd/Ctrl+Shift+P` → "Marp: Export slide deck" → PDF / PPTX / HTML

### Option B — Marp CLI

```bash
npm install -g @marp-team/marp-cli

# PDF
marp pitch-deck.md --pdf

# PowerPoint
marp pitch-deck.md --pptx

# Standalone HTML
marp pitch-deck.md --html
```

### Option C — Read as markdown

GitHub renders the deck as a long markdown page; `---` horizontal rules mark slide boundaries. Fine for quick review, not for presenting.

---

## Before sending

Fill these before any investor meeting:

- **Traction slide** — run Blockscout queries to replace every `[PLACEHOLDER]` with a live number and a "fetched at <UTC>" footnote
- **Team slide** — founder / engineering / growth names and backgrounds
- **Ask slide** — raise amount, valuation, use-of-funds percentages, runway
- **Roadmap slide** — shift dates forward if any have slipped; tag quarters as "shipped" where applicable

---

## Versioning

Tag meaningful revisions. Example:

```bash
git tag -a v1.0 -m "Initial pitch deck, April 2026"
git tag -a v1.1 -m "Refreshed traction metrics, May 2026"
```

Investor decks drift quickly; a tagged version lets you re-send a specific point-in-time deck if needed.

---

## License

Internal / confidential. Do not redistribute without permission.

*© 2025–2026 Shadow Diamondz Game + Movie Development, Inc.*
