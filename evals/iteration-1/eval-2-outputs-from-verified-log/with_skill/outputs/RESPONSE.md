Your log had everything the later phases need — 15 candidates across three sources, every row `verified = confirmed`, plus your two author requirements — so I went straight to origin tagging, IDs, SRS structure and outputs. Files are in this folder:

- **`catalog.md`** — the full catalog as an IEEE 29148 SRS: 12 requirements in three categories (PRIV, SEC, USA), each row carrying its clause and its origin tag, with the extraction log and its interpretation in Appendix C.
- **`catalog-table.csv`** — the requirement tables as data.
- **`extraction-log.csv`** — per-source counts and retention rates.
- **`audit-checklist.md`** / **`.csv`** — one question per requirement, Yes / No / Partially / N/A, keyed by ID.
- **`appendix-prompts.md`** — the extraction prompt filled in for your domain, for the paper appendix.

**Origin split:** 6 AI-K, 4 AI-R, 2 H. Ten of the twelve are clause-anchored; PRIV-05 and PRIV-06 are yours and carry no citation, which the catalog states rather than hides.

## The numbers, and what I think they say

| Source | Proposed | Kept | Rewritten | Rejected | Retention |
|---|---|---|---|---|---|
| GDPR | 6 | 2 | 2 | 2 | 66.7% |
| NIST-SP-800-63B | 5 | 2 | 1 | 2 | 60.0% |
| WCAG-2.2 | 4 | 2 | 1 | 1 | 75.0% |
| **TOTAL** | **15** | **6** | **4** | **5** | **66.7%** |

Two thirds survived, and the per-source spread (60–75% on four to six candidates each) is noise, not signal. I would not write the "standards retain better than guidelines" sentence — the sample cannot carry it.

The finding that does carry is the **citation failure rate: 3 of 15, 20%**, combining `clause not found` (GDPR Art. 33(9), WCAG SC 3.3.9) and `clause does not support` (NIST 4.3.1). One in five candidates pointed somewhere that did not hold up, spread across all three sources. GDPR Art. 33 has five paragraphs, so a citation to 33(9) is an invention — and the requirement hanging off it would have read perfectly well to a reviewer who did not open the regulation. That is your results-section headline, and it is the argument for the verification gate.

Worth pairing with it: of the ten survivors you rewrote four, and your notes name the failure modes — an invented deadline, a bundled obligation, a softened modality, a compound requirement. Strengthening, bundling and softening are exactly the errors that survive a citation check and are caught only by reading the requirement against the clause.

## Things I need from you

1. **The scope sentence.** I drafted one in §1.2 from your one-line brief, with inclusions and exclusions. It needs your wording, because SEC-SRC-003 was rejected as `out of scope` against a scope statement that only existed in your head. Revisit that rejection if my draft is off.
2. **Source editions.** Clause 5.1.1.2 is the NIST SP 800-63B **Revision 3** locator — Rev 4 renumbers that material — so I cited Rev 3 (June 2017). Same question for which WCAG 2.2 republication you read. Confirm both; the citations are only as good as the edition.
3. **Model and date per extraction run**, for the prompt appendix. Only you have those, and the reproducibility claim needs them plus whether you gave the model the full source or selected sections.
4. **PRIV-04 (encryption at rest).** I kept the `PRIV` code from your candidate ID even though the requirement sits in the security section. Flip it to `SEC-04` now if you would rather — IDs are permanent once this is circulated.

## One thing to double-check

You rejected **WCAG SC 3.3.9** as `clause not found`. My recollection is that WCAG 2.2 does have a 3.3.9 — Accessible Authentication (Enhanced), at AAA — but clause numbering is precisely what I should not be trusted on, so treat this as a prompt to spend thirty seconds with the spec, not as a correction. If the criterion exists and the problem was that it did not say what the candidate claimed, the reason code becomes `clause does not support`. Your headline number is unaffected either way, since the two are reported together, but the rejection table should be right.

## One assumption

I took the verification log as the complete record of what was proposed, so "candidates proposed" is just the row count per source. If anything was dropped before it reached the log, the retention rates are flattering.

Say the word if you want a Word version of the catalog to circulate, or want me to add a fourth source and run the extraction properly against text you can supply.
