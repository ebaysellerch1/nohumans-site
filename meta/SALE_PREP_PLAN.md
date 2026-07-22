# SALE_PREP_PLAN.md — 28-day commercial sale-prep initiative for nohumans.xyz

Status: ADDITIVE thread, tracked alongside the existing traffic/engagement mission (CONSTITUTION.md §2). Started 2026-07-22 (run 21). See CONSTITUTION.md §2.1 and DECISIONS.md (2026-07-22) for the mandate, hard constraints, and the black-hat-request-then-declined precedent that governs this whole initiative.

**Reality check before planning anything else**: this domain is ~2.5 weeks old, has 20 pages of content, a stable baseline of roughly 0-2 visits/day (GoatCounter, run 20 finding), 0 Google-organic clicks and 26 impressions total since inception (Search Console, checked run 21), average search position 24.7 (page 3), 6 of 13 tracked URLs indexed, and — as of run 21 — no confirmed external backlinks visible yet in Search Console's Links report (still "processing data"). Any plan that assumes this becomes a meaningfully monetizable or highly-ranked asset in 28 days is fiction. The realistic goal of this initiative is: **make the asset objectively cleaner, better-documented, and more credible than it is today, backed by real numbers** — not to manufacture a growth story. A buyer for a 4-week-old, near-zero-traffic domain is going to be valuing the experiment/content/build-quality and domain itself, not current revenue (there is none) or current traffic (negligible).

This plan does not replace BACKLOG.md — it is a second, parallel lens on the same site. Where a sale-prep task overlaps an existing backlog item (e.g. OG images, internal linking, indexing), this plan references the backlog item instead of duplicating it.

---

## Phase A — Technical & infrastructure audit (Week 1)

Goal: find and fix anything that would show up badly in a technical due-diligence pass, within sandbox bounds.

- Page speed / weight (no PSI account needed — public API hit its shared quota this run; use direct measurement as fallback, retry PSI next run)
- Security headers (fetch live response headers)
- HTTPS enforcement status (GitHub Pages `pages` API — read-only check, fix via same API if a simple config flag)
- Mobile responsiveness (375px reasoning/CSS audit — full checklist already run repeatedly per RUNBOOK periodic checklist)
- URL structure and sitemap.xml cleanliness
- robots.txt correctness
- Real backlink/indexing baseline from Search Console (Links report + Coverage/index report + Performance report) — no estimates
- Fix what's fixable within CONSTITUTION §3 bounds (meta tags, sitemap, small config flips via the already-authorized token); anything needing a new account/service/paid tool → admin request, not attempted

Executed in run 21 (2026-07-22) — see reports/2026-07-22-21-saleprep-week1.md for the full findings/fixes and before/after numbers.

## Phase B — Content & SEO strategy (Week 1–2)

Goal: identify real, documented keyword/content gaps and quick SEO wins — reusing and extending BACKLOG.md, not duplicating it.

- Cross-reference Search Console queries/impressions (real data, however thin) against the 12 existing guides — is there a query with impressions but no matching page, or a page ranking page-3+ for a fixable reason (title/meta mismatch, thin content)?
- Revisit BACKLOG #23b (guide refresh queue), #51 (guide 13 — demand-gated), #79 (OG image preview QA) through a "would this matter to a buyer's due diligence" lens rather than a pure growth lens.
- Internal linking audit: are all 20 pages reachable within 2 clicks from the homepage?
- No new guides written solely "for the sale" — CONSTITUTION §2's demand-gate rule for new content still applies unchanged.
- Output: a short prioritized list added to BACKLOG.md (not a separate list) so it survives independent of this plan.

## Phase C — Authority & credibility building (Week 2–3)

Goal: real, disclosed, white-hat ways to earn legitimate mentions/backlinks — no schemes, no paid placements, no link farms.

- Submitting the site to genuinely curated, free, no-signup-required directories/lists that fit the niche (e.g. "awesome AI tools" GitHub lists, curated newsletters) — most require a GitHub PR (fine, no account beyond the existing repo) or an email (admin must send — flag as admin request, no sending in admin's name).
- The already-planned Hebrew-share experiment (BACKLOG #67) is a legitimate organic-authority lever — still gated on the admin telling the model when a real share event is planned.
- Documenting the experiment itself (the "AI runs this site autonomously" story) is the site's actual differentiation and most link-worthy asset.
- What this phase will NOT do: guest-post schemes, PBNs, reciprocal-link exchanges, paid directory submissions, "buy 50 backlinks" services, or anything requiring a new account.
- Output: any concrete outreach idea gets logged as an admin request with a draft the admin can choose to send personally.

## Phase D — Proving commercial value (Week 3–4)

Goal: document real traffic/engagement trends a buyer could verify themselves — and make an honest call on monetization.

- Continue the existing METRICS.md cadence (weekly/daily GoatCounter reads, Search Console checks).
- Compile a single "current state, verifiable by anyone" snapshot: unique visitors trend, top pages, indexed-page count, Search Console impressions/clicks/position, GitHub commit history — all sourced with dates and links, no rounding, no projection.
- Monetization question (explicitly flagged, not decided unilaterally): the site currently has zero monetization. Adding a disclosed, ethical affiliate link *could* marginally support a "has revenue potential" narrative, but at ~0-2 visits/day the financial effect is negligible and the real question is a values/disclosure judgment call. **Recommendation: log as an admin request, do not implement unilaterally.**

## Phase E — Actual sale prep (Week 4) — documents only, no execution

Goal: produce what an admin would need to actually list the domain, without taking any irreversible or account-creating action.

- **Valuation estimate + methodology**: a reasoned, honest range — not false precision — based on domain age/cost baseline, content asset volume, build/documentation quality, current real (near-zero) traffic, and the "AI-built and run" novelty/portfolio value.
- **Draft listing copy**: honest about current traffic level (near-zero, stable), not hyped.
- **Marketplace recommendation**: reasoned comparison of Sedo/Afternic/Flippa/private-sale-via-broker — recommendation only, no account creation.
- All of the above are **documents for the admin to review and act on personally**. Actually creating a marketplace seller account or publishing a listing is explicitly out of bounds for the model and will be logged as an admin request, never attempted.

---

## Week-by-week mapping (realistic, assumes manual/admin-triggered runs — not daily cron)

- **Week 1** (run 21, this run): Phase A executed in full. Phase B started.
- **Week 2**: Phase B continued/closed. Phase C started.
- **Week 3**: Phase C continued. Phase D data collection starts.
- **Week 4**: Phase D closed with a real trend writeup. Phase E documents drafted.

Given the manual-runs-only model (no cron, admin-triggered), "week N" means "the Nth run-session that touches this initiative," not a calendar guarantee. Future runs should check the progress log below before assuming any phase is further along than documented.

## Progress log (update every run that touches this initiative)

- **Run 21 (2026-07-22)**: Plan created. Phase A executed — see reports/2026-07-22-21-saleprep-week1.md. Findings: added a Referrer-Policy meta tag site-wide (the one security header achievable via `<meta>` on static GitHub Pages hosting; shipped, live-verified, commit d966f19); no other security headers (CSP/X-Content-Type-Options/X-Frame-Options/HSTS/Permissions-Policy) are achievable without a proxy/CDN layer requiring a new account — flagged as admin decision (#85), not attempted. `https_enforced` was false — attempted fix via the existing GitHub Pages API, got a clean 403 (token lacks Pages-admin scope) — logged as admin request (#84), a 5-second UI fix, not pursued further. Homepage is 3080 bytes gzipped / 2 requests (HTML+CSS) — inherently fast structurally; PSI API quota exhausted (429) so no numeric Lighthouse score this run. Search Console shows 0 organic clicks / 26 impressions / avg position 24.7 since inception, 6/13 URLs indexed, Links report not yet populated (no confirmed backlinks visible yet). All real, sourced, dated.
