# Run 22 report — 2026-07-22 — admin decisions on #84/#85/#89 (governance/bookkeeping, not a content run)

## What this run was

A short administrative follow-up in the same admin chat session as run 21 (sale-prep Phase A). No live-site HTML, design, or scheduling changed. Purpose: record three admin decisions given in chat today and update BACKLOG/DECISIONS/SALE_PREP_PLAN/STATE accordingly.

## Lock check

.runlock20 showed explicit RELEASED entries for both run 20 and run 21. Created .runlock22 for this session. Verified `git fetch origin main` matched local HEAD (66bffbf, run 21's sync commit) before cloning/editing — no concurrent-run signal.

## #84 — HTTPS enforcement: confirmed live, closed as done

The admin reported flipping "Enforce HTTPS" manually in GitHub Settings → Pages. Verified independently (not just took the admin's word):
- `GET https://api.github.com/repos/ebaysellerch1/nohumans-site/pages` (requires the repo token — this endpoint 404s without auth even for a public repo) → `"https_enforced": true`, `https_certificate.state: "approved"`, cert valid to 2026-10-01.
- Direct `curl` (no follow) against `http://nohumans.xyz/` → `HTTP/1.1 301 Moved Permanently`, `Location: https://nohumans.xyz/`.

Both independent sources agree. BACKLOG #84 marked ✔ done and archived.

## #85 — Full security headers via Cloudflare/proxy: closed as declined-by-admin

The admin explicitly said to skip this ("על 2 נוותר" — skip Cloudflare). This is a deliberate scope decision, not a technical failure — marked closed/declined in BACKLOG (not "done"). The site proceeds without a CDN/proxy layer; the Referrer-Policy meta tag (shipped run 21, all 20 HTML pages) remains the only security-header-equivalent achievable on this static hosting. Noted in SALE_PREP_PLAN.md Phase A.

## #89 — Affiliate/monetization: admin delegated the decision to the model

The admin said explicitly: "אתה מחליט, לפי המטרות שהצבנו" (you decide, based on our stated goals). Decision: **do not add affiliate/monetization at this time.** Three reasons, logged in full in DECISIONS.md (2026-07-22):
1. Any affiliate signup is itself a new-account action — out of CONSTITUTION §3 bounds without the admin doing it personally, so the model can't unilaterally "add" it anyway.
2. Real traffic is ~0-2 visits/day (run 20/21 GoatCounter+Search Console data) — nowhere near enough to produce a meaningful, honest revenue proof-point; it would only add clutter.
3. The site's one demonstrated differentiator (about.html/live.html curiosity-driven transparency content) risks dilution from a promotional element this early.

Logged as a **revisit trigger, not a permanent no** — new BACKLOG #90 tracks the condition (sustained double-digit-plus daily traffic, and even then only a specific, disclosed, relevant affiliate).

## Forward-looking note (no action taken)

The admin wants to eventually let the model help draft Phase C outreach emails via a connected Gmail account. Noted in SALE_PREP_PLAN.md Phase C: the intended mechanism, once connected, is the Gmail MCP connector (create_draft/list_drafts/search_threads/get_thread/list_labels only — **no send capability**), so the model can research and write ready-to-send drafts into the admin's Gmail drafts folder, and the admin reviews+sends personally. This satisfies CONSTITUTION §3 by construction. No outreach drafting happened this run — Phase C hasn't started and the admin hasn't connected anything yet.

## Files touched

- BACKLOG.md — #84 marked done, #85 closed as declined, #89 marked decided, new #90 added, archive entries added.
- DECISIONS.md — new dated entry (2026-07-22, run 22) with full reasoning for all three items.
- SALE_PREP_PLAN.md — Phase A update note (HTTPS/headers resolution), Phase C forward-looking Gmail-connector note, progress log entry for run 22.
- STATE.md — one-line pointer to DECISIONS.md, run 22 summary in the sale-prep section and in "מצב נוכחי".

## Git / deployment

- Cloned fresh to `/tmp/nh-run-22-3592`, verified `origin/main` matched local HEAD before editing (66bffbf) and again immediately before push — no concurrent-run signal either time.
- Commit `4109436` ("meta: run 22 — governance follow-up on admin decisions #84/#85/#89"), pushed to main.
- GitHub Actions Pages build for commit 4109436: **conclusion=success** on first attempt.
- Mirrored `meta/` from the clone to the mapped project's `repo/meta/` via rsync (all four files verified byte-identical; the usual non-critical `_sync_marker.txt` unlink error is the known mapped-folder deletion limitation, not a problem).

## Admin requests

None new. Both open admin requests from run 21 (#84, #85) are now resolved (one fixed, one explicitly declined).

## Next run

- #83 (Phase B — Search Console query cross-reference) still open, untouched this run.
- #86 (Phase C — concrete outreach candidate list) still open.
- #90 (monetization revisit trigger) — not urgent, condition-gated.
- Continue watching for the Gmail MCP connector being set up before starting any Phase C draft work.
