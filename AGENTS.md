# anthonywlicausi.com — hard constraints

Personal site for Anthony W. Licausi. Linked from the DEALITHIC email signature going out to
investors and prospective customers — treat copy changes here as investor/customer-facing, same
bar as dealithic.co itself.

## Deploy

- **No build step.** Plain static HTML/CSS/JS in `index.html`. GitHub Pages serves the repo root
  directly at the custom domain (`CNAME` → `anthonywlicausi.com`).
- `git push` to `main` **is** the deploy — live within a minute or two, no staging.
- ⛔ `preview-redesign.html` and `preview-split.html` are leftover draft files from the last
  redesign, still sitting in the repo root — GitHub Pages serves them too, so they're publicly
  reachable at `/preview-redesign.html` / `/preview-split.html`. Not linked from anywhere, but
  ask before deleting (may still be wanted as a reference) or before assuming they're safe to leave.

## Text contrast — same rule as every other project

See the global `~/AGENTS.md` floor (16px body minimum, no `text-sm`/`text-xs` on public copy,
lighter-not-darker on dark backgrounds). This page got hit by it directly in 2026-09-26: the
ticker was 9px at 34%-opacity cyan on near-black and was reported unreadable. Fixed — see below.

## Color system (as of 2026-09-26)

Two palettes, split by section background:
- **Dark sections** (hero, nav, ticker, contact): `--d-*` bg vars + `--cyan` (`#01C9FE`, Dealithic
  Node Cyan) for the accent. Also `--amber` (`#1155FF`) still exists as a raw dark-blue accent —
  it reads fine against **white** chips but fails against black, which is why it's no longer used
  for anything sitting directly on the dark background (that's what `--cyan` replaced it for).
- **Light sections** (#work / Products, #thinking, footer): `--l-*` vars. `--l-cyan` (`#007A98`)
  is a darkened version of the brand cyan for use on white/cream — the bright `--cyan` fails
  contrast there.
- ⛔ Don't reuse `--cyan` (the bright one) for text on a light background, and don't reuse
  `--amber`/`--blue`/`--green` (the dark-bg variants) for anything that needs strong contrast on
  white without checking first — some existing usages (product-card wordmarks) get away with it
  because those specific hexes happen to be dark enough; that's not a rule to extend casually.

## Products section (`#work`) — content source of truth

The 11 rows mirror the live nav in the **trans-intel repo**
(`~/Projects/SaaS/transaction_intelligence/frontend/app/components/SiteNav.tsx`,
`PRODUCTS_MENU`/`SERVICES_MENU`) — that file is the canonical copy/link source, not this one.
When dealithic.co's nav copy or routes change, this page drifts out of sync silently (no build
link between the repos). Re-diff against `SiteNav.tsx` when touching this section again.

Known drift as of 2026-09-26: trans-intel's nav still labels the Deal Engine row "Deal
Intelligence" (route `/products/deal-engine`) — Anthony is renaming it to "Deal Engine" in that
repo directly; this page already uses "Deal Engine."

## 🤖 GROK / MULTI-AGENT ATTRIBUTION — required for every AI agent working in this repo

Git cannot tell which AI wrote a commit — every agent commits as the same human. So the commit
message and branch name must say it. **If you are Grok (Grokbot):**

1. ⭐ **Every commit ends with this trailer** (blank line before it):
   `Co-Authored-By: Grok <noreply@x.ai>`
2. ⭐ **Name your branches `grok/<topic>`.** Claude uses its own session branches; the prefix is how
   `git branch` shows who owns what.
3. ⛔ **Do NOT change `git config user.name` / `user.email`.** The author email must stay the
   owner's GitHub-linked address — a wrong email makes Vercel silently block the deploy.
4. ⭐ **Work in your own worktree, never the shared checkout:**
   `git worktree add ../<repo>-grok -b grok/<topic> origin/main`. Two agents in one working tree
   overwrite each other's uncommitted edits (this has broken `main` before).
5. ⭐ **Commit as you go** — loose uncommitted edits belong to whichever agent runs `git add` first.
   Commit specific files by name; never `git add -A`.
6. ⛔ Never `git reset --hard`, `git checkout -- .`, `git clean`, or `git stash` in a checkout you
   don't exclusively own.
7. Before starting, run `git log --oneline -15` and `git status` and read the repo's handoff doc,
   so you know what the other agents already did.

Find an agent's work later: `git log --grep "Co-Authored-By: Grok"` (Grok) or
`--grep "Co-Authored-By: Claude"` (Claude).
