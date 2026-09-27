# anthonywlicausi.com — status

Canonical status file for this repo. See `CLAUDE.md` for hard constraints (deploy, contrast
rules, color system). This file is the backlog.

## 🔴 OPEN — address next

- Nothing currently open on this page. Next likely touch: re-diff the Products section against
  trans-intel's `SiteNav.tsx` once Anthony's Deal Engine rename lands there, and again whenever
  dealithic.co's nav changes (see `CLAUDE.md` — no automated link between the two repos).
- Monthly essay cadence now runs through September 2026 — next one due ~October if the cadence
  continues. Ideas not yet used from the September pitch round: Deal Engine ("What AI Can't
  Underwrite"), QUARRY ("Deals Are Made By People Who Remember You"), DEALITHIC/Investor Network
  ("Why I Gave the Map Away").
- The 7 pre-existing essays (everything before June 2026) still use the old dark-blue accent
  (`#1155FF`) in their headers, not the Node Cyan the homepage and the 4 new essays now use —
  minor cross-page inconsistency, not fixed yet since it wasn't asked for.

## 🏗 Ops & architecture (stable)

- Static `index.html`, no build step, no framework. GitHub Pages serves the repo root directly;
  `git push` to `main` is the deploy.
- `writing/` holds standalone essay pages, each its own static HTML file, linked from the
  Writing section on the homepage.
- Two dark sections (hero, nav/ticker, contact) and two light sections (Products, Writing,
  footer) — see `CLAUDE.md` for the color-variable split between them.

## ✅ Shipped (newest first)

- **2026-09-26 — 4 new essays added, one per month June–September, each backlinking a product.**
  RYRA ("The Founder Attention Tax"), TradeCoach ("The Trade You Don't Remember"), STEADSPARK
  ("The Myth of the Leap"), Obsidian Quant ("The Discipline of the Pre-Registered Bet"). Picked
  from a 7-idea pitch after checking dealithic.co/insights to confirm no topic overlap (that site
  runs tactical/regulatory research pieces; this site runs personal philosophy essays — different
  registers, safe to coexist). The Obsidian piece was written carefully around the existing
  public-copy rule: never call Obsidian's own process a "backtest," frame it as a research ledger
  that may reject ideas but never silently promotes them. Restructured the homepage Writing
  section (new feat + 2 sm + 8-card grid, "11 · ESSAYS PUBLISHED"), and fixed the grid accent-color
  CSS which only cycled the first 4 `nth-child`s.
- **2026-09-26 — Ticker speed doubled**, 44s → 20s per loop (was too slow at the larger text size
  from the legibility fix below).
- **2026-09-26 — Products section expanded 3 → 11 rows.** Added Deal Engine, RYRA, Investor
  Network, DEALITHIC IR, DEALITHIC Enterprise, Agents API, QUARRY (renamed from D:CRM),
  STEADSPARK, TradeCoach alongside DEALITHIC and OBSIDIAN QUANT. Copy/links sourced from
  trans-intel's live `SiteNav.tsx`. Corrected a stale "25,000+ investors" line to the verified
  93,000+, and added the "third-largest network, behind PitchBook and Crunchbase" claim (Anthony
  confirmed this was independently researched). Added `--l-cyan` (`#007A98`) as a light-safe
  brand-cyan variant. Bumped `.prow-sub`/`.prow-learn` off sub-16px sizes now that they carry
  real content across 11 rows instead of 3.
- **2026-09-26 — Ticker legibility fix.** Was 9px at 34%-opacity cyan on near-black —
  unreadable. Bumped to 16px near-white with green up-arrows added after each item (stock-ticker
  motif).
- **2026-09-26 — Hero right column replaced.** Swapped the "Live Products" panel + stats grid for
  a single stat pull-quote ("4,100+ commits shipped..."), with three phrases bolded in the new
  cyan accent.
- **2026-09-26 — Hero/header accent swapped to Dealithic Node Cyan (`#01C9FE`).** The old dark
  blue (`#1155FF`) read poorly against the near-black hero background; cyan fixed contrast there.
  Left the Products section's product-card wordmarks on the original blue since that already read
  fine against white cards — see `CLAUDE.md` color-system note for why the two palettes diverge.
- **2026-09-25 — "The AI Cost Trap" essay added**, SEO pass across all 7 essays.
- **2026-09-?? — 6 blog posts + full SEO added** to the portfolio site (`writing/`).
- **2026-05-01 — New portfolio redesign launched**, CNAME added for the custom domain.

## ⚠️ Known risks/debt

- `preview-redesign.html` / `preview-split.html` sit in the repo root and are publicly served by
  GitHub Pages at their own paths (not linked from anywhere, but reachable). See `CLAUDE.md`.
- No build/lint/test step of any kind — every change ships straight to prod on push. Preview
  locally (`python3 -m http.server` + Chrome) before pushing anything content-sensitive, since
  this page is now linked from an investor-facing email signature.
