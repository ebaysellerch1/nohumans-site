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

**Update (run 22, 2026-07-22)**: Both open items from run 21 are now closed. HTTPS enforcement (#84) — admin flipped it manually in GitHub Settings → Pages; model verified independently via the Pages API (`https_enforced: true`) and a direct `curl` against `http://nohumans.xyz/` (301 → `https://nohumans.xyz/`). Full security headers via Cloudflare/CDN (#85) — the admin explicitly declined ("skip Cloudflare/proxy"), a deliberate scope decision, not a technical gap. **The site will proceed without a CDN/proxy layer.** The Referrer-Policy meta tag shipped in run 21 (all 20 HTML pages) remains the only security-header-equivalent achievable on this static GitHub Pages hosting without a proxy, and that's the final state for this phase — not a placeholder pending a future fix.

## Phase B — Content & SEO strategy (Week 1–2)

Goal: identify real, documented keyword/content gaps and quick SEO wins — reusing and extending BACKLOG.md, not duplicating it.

- Cross-reference Search Console queries/impressions (real data, however thin) against the 12 existing guides — is there a query with impressions but no matching page, or a page ranking page-3+ for a fixable reason (title/meta mismatch, thin content)?
- Revisit BACKLOG #23b (guide refresh queue), #51 (guide 13 — demand-gated), #79 (OG image preview QA) through a "would this matter to a buyer's due diligence" lens rather than a pure growth lens — e.g. a buyer will check for broken links, orphan pages, duplicate titles, stale copyright years, working RSS/sitemap — same checks BACKLOG already schedules, just prioritized higher this month.
- Internal linking audit: are all 20 pages reachable within 2 clicks from the homepage? (Likely yes — nav + guide groups + read-next; verify, don't assume.)
- No new guides written solely "for the sale" — CONSTITUTION §2's demand-gate rule for new content still applies unchanged.
- Output: a short prioritized list added to BACKLOG.md (not a separate list) so it survives independent of this plan.

## Phase C — Authority & credibility building (Week 2–3)

Goal: real, disclosed, white-hat ways to earn legitimate mentions/backlinks — no schemes, no paid placements, no link farms.

Legitimate options within sandbox bounds (all still require either admin action or organic discovery — none of these can be executed by the model alone without an account):
- Submitting the site to genuinely curated, free, no-signup-required directories/lists that fit the niche (e.g. "awesome AI tools" GitHub lists, curated newsletters) — most require a GitHub PR (fine, no account beyond the existing repo) or an email (admin must send — flag as admin request per CONSTITUTION §3, no sending in admin's name).
- The already-planned Hebrew-share experiment (BACKLOG #67) is a legitimate organic-authority lever (real audience, real language-market signal) — still gated on the admin telling the model when a real share event is planned, per the existing open admin request. Not duplicated here, just cross-referenced.
- Documenting the experiment itself (the "AI runs this site autonomously" story) is the site's actual differentiation and most link-worthy asset — continuing to keep about.html/live.html/changelog.html current and citable is itself authority-building, at zero incremental cost.
- What this phase will NOT do: guest-post schemes, PBNs, reciprocal-link exchanges, paid directory submissions, "buy 50 backlinks" services, or anything that requires opening a new account. If a legitimate-looking opportunity requires signup or payment, it gets logged as an admin request, not attempted.
- Output: any concrete outreach idea gets logged as an admin request (since sending on the admin's behalf is out of bounds) with a draft the admin can choose to send personally.
- **Forward-looking mechanism, noted 2026-07-22, not yet active**: the admin wants to eventually let the model help draft Phase C outreach emails directly, rather than the model just writing drafts into BACKLOG/reports for manual copy-paste. The intended mechanism, once the admin sets it up: connect the Gmail MCP connector (the one available in this environment exposes only `create_draft` / `list_drafts` / `search_threads` / `get_thread` / `list_labels` — **no send capability at all**). This lets the model research outreach targets and write ready-to-send drafts straight into the admin's Gmail drafts folder; the admin then reviews and sends each one personally from his own account. This satisfies CONSTITUTION §3's "no sending messages in the admin's name" rule by construction — the connector is physically incapable of sending. **No outreach drafting is happening yet**: Phase C hasn't started (the plan is still in Phase A/B per the week-by-week mapping above) and the admin hasn't connected anything yet. This note exists purely so a future run doesn't have to rediscover the mechanism from scratch.

## Phase D — Proving commercial value (Week 3–4)

Goal: document real traffic/engagement trends a buyer could verify themselves — and make an honest call on monetization.

- Continue the existing METRICS.md cadence (weekly/daily GoatCounter reads, Search Console checks) — by week 4 there will be roughly 2-3 more data points beyond run 20/21, enough to show trend direction (still expected to be a flat, low baseline — that's the honest number, not something to talk up).
- Compile a single "current state, verifiable by anyone" snapshot: unique visitors trend, top pages, indexed-page count, Search Console impressions/clicks/position, GitHub commit history (proof of build velocity and real authorship trail), all sourced with dates and links to the live dashboards — no rounding, no projection.
- Monetization question (explicitly flagged, not decided unilaterally): the site currently has zero monetization. Adding a disclosed, ethical affiliate link (e.g. to a book or tool genuinely referenced in a guide, clearly labeled) *could* marginally support a "has revenue potential" narrative for a buyer, but at ~0-2 visits/day any such revenue would be effectively zero for the 28-day window and the main effect would be a values/disclosure judgment call, not a financial one. **Recommendation: log as an admin request, do not implement unilaterally** — this touches CONSTITUTION §4 (content red lines) and reads as a monetization-model decision the admin should make explicitly, not infer from the sale mandate.

## Phase E — Actual sale prep (Week 4) — documents only, no execution

Goal: produce what an admin would need to actually list the domain, without taking any irreversible or account-creating action.

- **Valuation estimate + methodology**: a reasoned range based on comparable-ish signals (domain age/registration cost baseline, content asset volume, build/documentation quality, current real traffic — explicitly near-zero — and the meta-narrative value of "AI-built and run" as a novelty/portfolio asset). This will be a wide, honest range, not a confident number — real domain appraisal for a low-traffic 1-month-old site is inherently uncertain, and the plan will say so rather than inventing false precision.
- **Draft listing copy**: description of the asset, what's included (domain + 20 pages of original content + full public build history + working analytics/Search Console setup), written honestly about current traffic level (near-zero, stable) rather than hyping it.
- **Marketplace recommendation**: reasoned comparison of Sedo/Afternic/Flippa/private-sale-via-broker on fit for a content-driven, low-traffic, high-story-value domain — recommendation only, no account creation.
- All of the above are **documents for the admin to review and act on personally**. Actually creating a marketplace seller account or publishing a listing is explicitly out of bounds for the model (CONSTITUTION §3) and will be logged as an admin request, never attempted.

---

## Week-by-week mapping (realistic, assumes manual/admin-triggered runs — not daily cron)

- **Week 1** (run 21, this run): Phase A executed in full. Phase B started (cross-reference exercise, added to BACKLOG).
- **Week 2**: Phase B continued/closed. Phase C started (legitimate-mention research, draft outreach ideas as admin requests).
- **Week 3**: Phase C continued. Phase D data collection starts (second/third METRICS read-out since this plan began).
- **Week 4**: Phase D closed with a real trend writeup. Phase E documents drafted (valuation, listing copy, marketplace recommendation).

Given the manual-runs-only model (no cron, admin-triggered per ADMIN.md), "week N" means "the Nth run-session that touches this initiative," not a calendar guarantee — consistent with how run cadence has actually worked since 2026-07-08 (14-day gaps have happened). Future runs should check this file's "progress log" section below before assuming any phase is further along than documented.

## Progress log (update every run that touches this initiative)

- **Run 21 (2026-07-22)**: Plan created. Phase A executed — see reports/2026-07-22-21-saleprep-week1.md. Findings: added a Referrer-Policy meta tag site-wide (the one security header achievable via `<meta>` on static GitHub Pages hosting; shipped, live-verified, commit d966f19); no other security headers (CSP/X-Content-Type-Options/X-Frame-Options/HSTS/Permissions-Policy) are achievable without a proxy/CDN layer requiring a new account — flagged as admin decision (#85), not attempted. `https_enforced` was false — attempted fix via the existing GitHub Pages API, got a clean 403 (token lacks Pages-admin scope) — logged as admin request (#84), a 5-second UI fix, not pursued further. Homepage is 3080 bytes gzipped / 2 requests (HTML+CSS) — inherently fast structurally; PSI API quota exhausted (429) so no numeric Lighthouse score this run. Search Console shows 0 organic clicks / 26 impressions / avg position 24.7 since inception, 6/13 URLs indexed, Links report not yet populated (no confirmed backlinks visible yet). All real, sourced, dated.
- **Run 22 (2026-07-22, same admin session, governance/bookkeeping follow-up — no content run)**: Three admin decisions from chat closed out in BACKLOG/DECISIONS: (1) #84 confirmed fixed and closed — `https_enforced: true` via Pages API + live 301 redirect on `http://nohumans.xyz/` verified via direct curl (not just admin's word). (2) #85 closed as declined-by-admin (scope decision, not a fix) — site proceeds without a CDN/proxy layer, Referrer-Policy meta remains the ceiling on this hosting. (3) #89 decided by the model per admin delegation — no affiliate/monetization added now (reasons: sandbox account-creation limit, near-zero real traffic making any "revenue proof" meaningless, risk of diluting the site's one proven differentiator); logged as a revisit-conditioned BACKLOG item (#90), not a permanent no. Also noted (no action taken): future Phase C outreach mechanism will be the Gmail MCP connector (draft-only, no send capability) once the admin connects it — Phase C itself has not started.
- **Run 23 (2026-07-22, real content/growth run)**: Operating-mode change first: admin instructed (in chat, not a sandbox-boundary change) that in-bounds judgment calls no longer get escalated mid-run — codified as RUNBOOK.md §3.5, ADMIN.md standing instruction #2, and a DECISIONS.md entry, so future runs with zero chat context know the rule. Then Phase B executed and closed (#83): cross-referenced Search Console's real query/page data (18-day window, still just 26 impressions/0 clicks/pos 24.7 — no material change from run 21) against the 12 guides — found 3 pages with real impressions (home 5, ask-ai-to-check-its-own-work.html 11, verify-ai-facts.html 10) and confirmed the one visible query ("ai output verification") already matches verify-ai-facts.html's existing title/description well; no fixable title/meta mismatch exists. Also found, via live URL Inspection (not just the aggregate Coverage report), that 2 pages previously flagged "crawled, not indexed" are now actually indexed — the aggregate report lags. Full site-wide link/duplicate-title/stale-date audit (buyer-due-diligence lens) came back clean (0 broken links, 0 duplicates, all pages ≤2 clicks from home, no stale copyright years). One real, fixable finding: several pages (about.html x2, one guide, llms.txt) still claimed the site runs on a fixed "several times a day" schedule — stale since the 2026-07-08 manual-run switch, missed by run 18's earlier pass on the same issue. Fixed, plus a faq.html refresh (stale "wave still climbing" claim; new disclosed Q&A about this sale-prep thread itself). Commit 690b345, deployed and live-verified (8 URLs), IndexNow pinged. This closes out Phase B for this initiative — no further title/meta gaps found at current traffic/impression levels; Phase B revisits only if Search Console impressions grow enough to surface new queries.
