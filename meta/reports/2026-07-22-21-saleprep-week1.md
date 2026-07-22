# Run 21 (2026-07-22, ~17:00-17:35 local) — Sale-prep initiative, Phase A

New additive mandate from the admin (2026-07-22, same day as run 20): a 28-day initiative to increase nohumans.xyz's commercial resale value, alongside — not instead of — the existing traffic/engagement mission (CONSTITUTION.md §2). Full constraints documented in CONSTITUTION.md §2.1 and the decision (with an important precedent) in DECISIONS.md 2026-07-22. This run executed Phase A (technical/infrastructure audit) of the resulting SALE_PREP_PLAN.md.

## Lock check

.runlock20 was present but its own content stated "RELEASED: run 20 completed cleanly" (bash cannot unlink lock files — known limitation, same handling as run 19). No other fresh lock existed. Before pushing, `git fetch origin main` confirmed local HEAD matched origin/main exactly (75499d8) — no concurrent-run signal.

## Governance work (done first, before any site changes)

1. **CONSTITUTION.md §2.1 added**: documents the additive sale-prep goal and its hard constraints (white-hat only, all §3 sandbox limits still apply, all buyer-facing data must be 100% real/sourced, final sale-execution phase produces documents only).
2. **DECISIONS.md entry added (2026-07-22)**: records that an earlier version of this same request, in the same conversation, tried to permit black-hat tactics; the model declined, explained the conflict with both the existing mission and the sale-integrity goal itself, and the admin backed down ("do what's allowed, don't do what's forbidden"). Logged explicitly as a binding precedent for any future run that meets a similar request without today's chat context.
3. **SALE_PREP_PLAN.md written** (project folder + repo/meta/): 5 phases across 4 weeks — A) technical/infra audit, B) content/SEO gap analysis, C) legitimate authority/backlink building, D) proving real commercial value + a monetization question flagged for the admin, E) sale-prep documents only. The plan is blunt about the site's real baseline so future runs don't inflate expectations.

## Phase A findings — all real, sourced, dated

**Security headers** (`curl -D -` against the live site):
- Present: none of the standard security headers (no CSP, X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security, Permissions-Policy).
- **Fixed**: added `<meta name="referrer" content="strict-origin-when-cross-origin">` to all 20 HTML pages — the one security-relevant header achievable via `<meta>` on static GitHub Pages hosting, with zero risk to the GoatCounter tracking script (verified still present/firing after deploy).
- **Not fixable within sandbox bounds**: CSP, X-Content-Type-Options, X-Frame-Options, HSTS, Permissions-Policy have no `<meta>` equivalent and GitHub Pages has no custom-headers config. Achieving these would require a CDN/proxy layer (e.g. Cloudflare), which requires a new account — out of bounds per CONSTITUTION §3. **Logged as admin request (#85)**, not attempted.

**HTTPS enforcement**:
- GitHub Pages API showed `https_enforced: false` and plain `http://nohumans.xyz/` returns `200 OK` directly (not a redirect to https).
- Attempted fix via the existing GITHUB_TOKEN (`PUT .../pages {"https_enforced": true}`) — **failed with 403 "Resource not accessible by personal access token"**. The token can push commits but lacks the Pages-admin scope needed to change this repo setting. **Logged as admin request (#84)**, no workaround attempted.

**Page speed**:
- Google PageSpeed Insights public API returned `429 quota exceeded` for the shared/keyless quota (a personal API key would require a Google Cloud account — out of bounds). Fell back to direct measurement (real, measured, not estimated):
  - Homepage: 3,080 bytes gzipped (7,955 uncompressed), single HTML response.
  - style.css: 2,042 bytes gzipped.
  - Homepage load is 2 first-party requests (HTML + CSS) plus one async third-party script (GoatCounter's count.js). No web fonts, no JS framework, no render-blocking assets.
  - Conclusion: structurally about as fast as a static site can be; no numeric Lighthouse score obtained this run — retry PSI next run once quota resets.

**Mobile responsiveness**:
- CSS review (style.css): two `@media (max-width: 600px)` blocks covering typography scale-down, nav tap targets, table horizontal-scroll containment, hero sizing — consistent with accessibility/mobile audits already done in runs 4 and 5. No new issues found.

**URL structure / sitemap**:
- sitemap.xml: 19 URLs, well-formed, lastmod dates current, all canonical. robots.txt clean. No orphaned or duplicate URLs found.

**Backlinks / indexing — real data from Search Console (already-connected, no new login)**:
- **Links report**: not yet populated ("the system is processing data, check back in about a day") — no confirmed external backlinks visible yet.
- **Performance report** (2026-07-02 to 2026-07-20): **0 total clicks**, **26 total impressions**, **0% average CTR**, **24.7 average position**. Only one query recorded: "ai output verification" (3 impressions, 0 clicks).
- **Indexing (Pages) report**: **6 of 13** tracked URLs indexed; 7 not indexed (2 redirects to another URL, 2 duplicate-with-valid-canonical, and **3 genuinely "crawled — currently not indexed"**).

## Fix executed and shipped

- Commit `d966f19` — "security: add Referrer-Policy meta tag (strict-origin-when-cross-origin) site-wide — sale-prep Phase A technical audit (run 21)". Pure 20-line addition (one line per file), `git diff` confirmed no replacements/duplicates. GitHub Actions run completed `success` on first attempt. Live-verified via cache-busted curl on the homepage plus 5 spot-checked pages (a guide, the tool, live.html, about.html, faq.html) — all 6 show the new tag; GoatCounter script tag confirmed still present (no analytics regression).
- Local `repo/` mirror refreshed via `rsync --delete` (one known-limitation warning: couldn't unlink a stale `meta/_sync_marker.txt`, non-critical).
- No IndexNow ping this run — no URLs were added/changed in a way search engines would need to re-crawl differently (meta-only change to existing indexed pages).

## Before / after

| Item | Before | After |
|---|---|---|
| Referrer-Policy header/meta | none | `strict-origin-when-cross-origin` meta tag, all 20 pages |
| https_enforced (GitHub Pages) | false | still false — admin action required (403 on model's attempt) |
| Other security headers | none | still none — requires proxy/CDN layer, admin decision needed |
| Homepage weight | not previously measured this precisely | 3,080 bytes gzipped, 2 requests |
| GSC organic clicks (since inception) | undocumented | 0 clicks, 26 impressions, pos. 24.7 (real, dated) |
| GSC indexed pages | undocumented | 6 / 13 indexed |
| GSC backlinks | undocumented | not yet available (report still processing) |

## Planned for week 2 (Phase B)

- Cross-reference the one real Search Console query ("ai output verification") and any future impressions against existing guide content.
- Full internal-link reachability check (2-click rule from homepage).
- Continue tracking BACKLOG #83 (added this run).

## Admin requests logged

1. **#84 — enable "Enforce HTTPS"** in GitHub repo Settings → Pages. Confirmed via a live 403 that the model's token can't do this.
2. **#85 — full security header set** (CSP, X-Content-Type-Options, X-Frame-Options, HSTS, Permissions-Policy) is not achievable on static GitHub Pages hosting without a CDN/proxy layer (e.g. Cloudflare), which requires a new account — flagged for the admin to decide.
3. **#86 (forward-looking)** — Phase C legitimate-outreach ideas will need the admin to actually send anything email-based; the model will draft, not send.
4. **#89 (forward-looking, flagged for awareness)** — whether to add a disclosed, ethical affiliate mention is a values/monetization decision for the admin, not something inferred from the sale mandate.

No scheduling/cron was touched — remains manual/admin-triggered only. No accounts opened, no payments made, no black-hat tactic used or considered "in bounds" at any point this run.

## State files

STATE.md, BACKLOG.md, DECISIONS.md, CONSTITUTION.md, SALE_PREP_PLAN.md all updated in the mapped project folder; mirrored into repo/meta/ as part of this run's final sync commit.
