# Audit Checklist

**Catalog audited:** Requirements Catalog — Mental Wellbeing Apps, v1.0 (2026-09-07)
**Basis:** `partial-verification-log.csv`, 17 entries, all marked `confirmed`

This checklist is for someone re-checking the catalog independently — a reviewer, a second author,
or you in six months. It is in three parts: per-requirement checks, open items that the current
verification pass left unresolved, and process checks on the catalog as a whole.

Sign each item with initials and a date. An unchecked box is a claim not yet independently
confirmed, not a defect.

---

## Part A — Per-requirement verification

For each requirement: open the cited clause in the cited source, and confirm all four.

- **[S] Source resolves.** The clause address exists in the named document, in the edition used.
- **[T] Text supports.** The clause actually says what the requirement says. Not adjacent, not implied.
- **[M] Modality matches.** A `shall` in the requirement corresponds to an obligation in the source, not a recommendation. A `shall not` corresponds to a prohibition.
- **[A] Atomic and testable.** One obligation, phrased so a tester could produce a pass or fail.

### Privacy — GDPR

| Req ID | Clause to open | S | T | M | A | Reviewer / date |
| --- | --- | :-: | :-: | :-: | :-: | --- |
| PRIV-01 | GDPR Art. 20(1) | ☐ | ☐ | ☐ | ☐ | |
| PRIV-02 | GDPR Art. 17(1)(a) | ☐ | ☐ | ☐ | ☐ | |
| PRIV-03 | GDPR Art. 25(2) | ☐ | ☐ | ☐ | ☐ | |
| PRIV-04 | GDPR Art. 32(1)(a) | ☐ | ☐ | ☐ | ☐ | |

Specific things to look for:
- **PRIV-02** — confirm the deadline really is absent from the source. The candidate's "immediately" was struck; check nothing elsewhere in Art. 12 or Art. 17 reimposes a timeframe that ought to be cited instead.
- **PRIV-04** — Art. 32(1)(a) names pseudonymisation and encryption without distinguishing at-rest from in-transit, and without confining either to the user's device. Confirm that the narrowing to "at rest on the user's device" is a deliberate scoping decision and not an unsupported addition.

### Security — NIST SP 800-63B

| Req ID | Clause to open | S | T | M | A | Reviewer / date |
| --- | --- | :-: | :-: | :-: | :-: | --- |
| SEC-01 | NIST SP 800-63B §5.1.1.2 | ☐ | ☐ | ☐ | ☐ | |
| SEC-02 | NIST SP 800-63B §5.1.1.2 | ☐ | ☐ | ☐ | ☐ | |
| SEC-03 | NIST SP 800-63B §5.1.1.2 | ☐ | ☐ | ☐ | ☐ | |

Specific things to look for:
- ☐ **Which revision?** The log does not record which revision of SP 800-63B was consulted. Section numbering is not stable across revisions of this document, so §5.1.1.2 may not point at the same text in the edition a reviewer picks up. **Record the revision and publication date before anything else in this section is checked.** This is the single most consequential open item in the catalog.
- **SEC-03** — confirm the source states a prohibition and not merely an absence of a rotation requirement. The rewrite promoted "should" to "shall not"; that is only correct if the clause prohibits rather than declines to require.

### Accessibility — WCAG 2.2

| Req ID | Clause to open | S | T | M | A | Reviewer / date |
| --- | --- | :-: | :-: | :-: | :-: | --- |
| USA-01 | WCAG 2.2 SC 1.4.4 | ☐ | ☐ | ☐ | ☐ | |
| USA-02 | WCAG 2.2 SC 2.4.7 | ☐ | ☐ | ☐ | ☐ | |
| USA-03 | WCAG 2.2 SC 1.1.1 | ☐ | ☐ | ☐ | ☐ | |

Specific things to look for:
- ☐ **Conformance level not recorded.** None of the three requirements states whether its criterion is Level A, AA or AAA. A catalog that mixes levels without saying so cannot support a conformance claim. Add the level to each row.
- **USA-03** — SC 1.1.1 attaches conditions and exceptions to the text-alternative obligation (controls, time-based media, CAPTCHA, decoration). Confirm the flat statement is an acceptable simplification for this catalog's purpose, or qualify it.

### Author-contributed

| Req ID | Check | Status |
| --- | --- | --- |
| AUTH-01 | ☐ Evidence record exists and is citable ☐ Statement is atomic and testable | |
| AUTH-02 | ☐ Evidence record exists and is citable ☐ Statement is atomic and testable | |

---

## Part B — Open items

These are unresolved. Each one is a specific question with a specific way to close it.

### R1 — Re-check the rejection of WCAG SC 3.3.9

The log rejects USA-SRC-003 with the reason **"clause not found."** WCAG 2.2 added success criteria
in the 3.3.x range that did not exist in WCAG 2.1, and SC 3.3.9 is among the numbers in use. A
"clause not found" result is what you get from consulting WCAG 2.1, or a 2.2 draft, rather than the
published 2.2 recommendation.

☐ Re-open SC 3.3.9 in the published WCAG 2.2 recommendation.
☐ If the clause exists: reinstate USA-SRC-003 as a live candidate and verify it properly. Record its conformance level — if it is AAA, it may still be correctly excluded, but *on scope grounds, not on "not found"*.
☐ If it genuinely does not resolve, record which document and version was consulted, so the rejection stands on a stated basis.

**Effect if reinstated and retained:** WCAG retention rises from 75.0% (3/4) to 100% (4/4), and
all-source retention from 66.7% (10/15) to 73.3% (11/15).

### R2 — Confirm the rejection of GDPR Art. 33(9)

Rejected as "clause not found." Art. 33 is short and the paragraph numbering does not run as high as
(9), so the rejection is very likely correct — but a non-resolving citation usually means the
candidate was aimed at *something*.

☐ Confirm Art. 33 has no paragraph (9).
☐ Determine what the candidate was trying to cite. Breach notification obligations are a plausible target and are absent from the catalog entirely. If a valid clause was intended, raise it as a new candidate rather than leaving the rejection as the end of the matter.

### R3 — Revisit "not a requirement" for GDPR Art. 5(1)(b)

PRIV-SRC-005 was rejected on the grounds that the cited text is not a requirement. Art. 5(1)(b) is
the purpose-limitation principle, and Art. 5 principles are binding on controllers rather than
advisory.

☐ Confirm the intended reason: was it *not binding* (contestable), or *not translatable into a testable product-level statement* (defensible)?
☐ Record the reason in the form actually meant. The two are different rejections and a reviewer cannot tell them apart from the current note.

### R4 — Record the scope decision behind the NIST 5.2.2 rejection

SEC-SRC-003 was rejected as "out of scope." §5.2.2 concerns rate limiting / throttling of
authentication attempts. For an app holding mental health records behind an account, that is not
self-evidently out of scope.

☐ State the scope boundary being applied, in one sentence, in the log.
☐ Confirm the same boundary was applied consistently to the other four NIST candidates.

### R5 — Raise the missing encryption-in-transit candidate

PRIV-SRC-006 was split; only the at-rest half survives as PRIV-04. The in-transit half was not
re-entered as a candidate and is absent from the catalog.

☐ Raise a new candidate for encryption in transit against GDPR Art. 32(1)(a).
☐ Verify and admit, or record why not.

### R6 — Recover the dropped half of USA-SRC-004

The log records that the candidate was compound but not what the second obligation was.

☐ Recover the original candidate text from working notes.
☐ Raise the second obligation as its own candidate, or record that it was intentionally abandoned.

### R7 — Decide on the unscreened fourth source

`NSAI-DH-104-2024.txt` (*National Standard for Digital Health Applications Supporting Adult Mental
Wellbeing*, Part 2, clauses 5–7 excerpt) sits in the same folder as the verification log and appears
nowhere in it. It is the only domain-specific source available, and the catalog currently has no
safety, retention-period, content-provenance or notification requirements at all.

☐ Decide: in scope for this catalog, or deliberately excluded?
☐ If in scope, run an extraction and verification pass over it and issue the catalog as v1.1. **Do not fold its clauses in without verification** — every requirement now in the catalog carries a confirmed verdict, and admitting unverified text would break that guarantee.
☐ If excluded, record the reason, so the absence of safety requirements from a mental-wellbeing catalog is a stated decision rather than an oversight.

### A1 — Establish an evidence basis for the author-contributed requirements

AUTH-01 and AUTH-02 are supported only by "added by author from prior fieldwork."

☐ Cite the fieldwork: what study, when, what method, what sample.
☐ Or find a published clause that supports each statement and re-derive them as source-derived requirements.
☐ Until one of those is done, keep them in a separately labelled section (they are) and label them author-asserted anywhere the catalog is reused.

---

## Part C — Whole-catalog process checks

- ☐ **Source editions recorded.** Every source has a version, edition or publication date attached. Currently none does. GDPR and WCAG 2.2 are stable enough to be unambiguous; NIST SP 800-63B is not (see Part A).
- ☐ **Verification dates recorded per row.** The log records *that* each entry was confirmed, not *when*. Over a two-week window with a source that may be revised, the date matters.
- ☐ **Verifier recorded.** Single-author verification throughout. Note it, so a reader knows no second pair of eyes has been on these clauses.
- ☐ **Traceability holds both directions.** Every requirement traces to a candidate ID; every candidate ID has a disposition. Confirmed for all 17 log rows and all 12 requirements.
- ☐ **No unverified content admitted.** All 12 requirements derive from rows marked `confirmed`. Nothing was inferred, filled in, or carried over from an unscreened source. Confirmed at v1.0 — **re-confirm after any future extraction pass.**
- ☐ **Rejected candidates remain visible.** The five rejections are listed with reasons in the extraction log, and their candidate IDs are not reused. Confirmed.
- ☐ **Modal verbs consistent.** All 12 requirements use *shall* or *shall not*. No *should*, *may*, or *must* mixed in. Confirmed by inspection.
- ☐ **One obligation per requirement.** Two compound candidates were split during verification. Re-check the remaining ten for compounds that were not caught — particularly USA-03 and PRIV-01.
- ☐ **Conformance levels recorded for WCAG items.** Not currently present. See Part A.
- ☐ **Coverage gaps stated, not hidden.** Six gaps are listed in the extraction log §5. A reader who takes this catalog as complete would be misled; a reader who reads §5 would not.
- ☐ **Scope statement written.** The catalog does not yet contain a paragraph saying what it covers and what it deliberately does not. Add one before the catalog is circulated outside the author.

---

## Status at close of v1.0

| | |
| --- | --- |
| Requirements in catalog | 12 (10 source-derived, 2 author-asserted) |
| Candidates screened | 15 across 3 sources |
| Overall retention | 66.7% |
| Log rows unverified | 0 |
| Open items in this checklist | 8 (R1–R7, A1) |
| Blocking items before external circulation | R1, R7, A1, and the NIST revision item in Part A |
