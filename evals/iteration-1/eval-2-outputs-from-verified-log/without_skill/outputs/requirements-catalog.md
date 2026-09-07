# Requirements Catalog — Mental Wellbeing Apps

**Domain:** Privacy, security and accessibility requirements for mental wellbeing applications
**Catalog version:** 1.0
**Date compiled:** 2026-09-07
**Basis:** `partial-verification-log.csv` (17 verified entries, two-week verification pass)

**Contents:** 12 requirements — 10 derived from three normative sources, 2 contributed by the author.
Every requirement below carries a verification verdict of `confirmed`. No unverified or provisional
statement has been admitted to the catalog.

**Reading the tables**

| Column | Meaning |
| --- | --- |
| Req ID | Stable catalog identifier. Cite this in downstream work. |
| Requirement | Normative statement as verified. Wording is final; do not paraphrase when citing. |
| Source / Clause | The document and clause the statement is traceable to. |
| Candidate ID | Row in the verification log this requirement came from. |
| Derivation | `KEEP` = candidate wording survived verification unchanged. `REWRITE` = wording was corrected against the source; see the note. `AUTHOR` = not derived from a published source. |

---

## 1. Privacy — GDPR (Regulation (EU) 2016/679)

Four requirements, from six candidates.

| Req ID | Requirement | Source / Clause | Candidate ID | Derivation |
| --- | --- | --- | --- | --- |
| PRIV-01 | The app shall enable the user to receive their personal data in a structured, commonly used and machine-readable format. | GDPR Art. 20(1) | PRIV-SRC-001 | KEEP |
| PRIV-02 | The app shall erase the user's personal data on request where the data are no longer necessary for the purpose for which they were collected. | GDPR Art. 17(1)(a) | PRIV-SRC-002 | REWRITE |
| PRIV-03 | The app shall by default process only the personal data necessary for each specific purpose. | GDPR Art. 25(2) | PRIV-SRC-003 | KEEP |
| PRIV-04 | The app shall encrypt personal data at rest on the user's device. | GDPR Art. 32(1)(a) | PRIV-SRC-006 | REWRITE |

**Rewrite notes**

- **PRIV-02** — the original candidate said the erasure must happen *immediately*. Art. 17(1)(a)
  sets no deadline, so the deadline was struck rather than invented. If the product needs a
  concrete SLA, it has to come from somewhere other than this clause.
- **PRIV-04** — the original candidate bundled encryption at rest and encryption in transit into a
  single statement. It was split, and only the at-rest half is carried here. **There is currently
  no in-transit requirement in this catalog.** See the coverage gaps in the extraction log.

---

## 2. Security — NIST SP 800-63B (Digital Identity Guidelines, Authentication)

Three requirements, from five candidates.

| Req ID | Requirement | Source / Clause | Candidate ID | Derivation |
| --- | --- | --- | --- | --- |
| SEC-01 | The app shall permit passwords of at least 64 characters in length. | NIST SP 800-63B §5.1.1.2 | SEC-SRC-001 | KEEP |
| SEC-02 | The app shall verify prospective passwords against a list of commonly used or compromised values. | NIST SP 800-63B §5.1.1.2 | SEC-SRC-002 | KEEP |
| SEC-03 | The app shall not require periodic password rotation in the absence of evidence of compromise. | NIST SP 800-63B §5.1.1.2 | SEC-SRC-005 | REWRITE |

**Rewrite notes**

- **SEC-03** — the original candidate used *should*. The source clause is a `SHALL NOT`, so the
  modal was strengthened to *shall not*. This is a prohibition, not an option: a product that
  offers optional rotation prompts still conforms, one that forces rotation on a schedule does not.

**Note on §5.1.1.2.** All three security requirements come from one clause. That clause is the
memorized-secret verifier section and is dense; the concentration is expected, but it also means
this catalog's security coverage rests on a single paragraph of a single document.

---

## 3. Accessibility — WCAG 2.2

Three requirements, from four candidates.

| Req ID | Requirement | Source / Clause | Candidate ID | Derivation |
| --- | --- | --- | --- | --- |
| USA-01 | The app shall support resizing of text up to 200 percent without loss of content or functionality. | WCAG 2.2 SC 1.4.4 | USA-SRC-001 | KEEP |
| USA-02 | The app shall render a visible focus indicator for any keyboard-operable user interface component. | WCAG 2.2 SC 2.4.7 | USA-SRC-002 | KEEP |
| USA-03 | The app shall provide a text alternative for each non-text content element. | WCAG 2.2 SC 1.1.1 | USA-SRC-004 | REWRITE |

**Rewrite notes**

- **USA-03** — the original candidate was compound (it joined text alternatives to a second,
  separate obligation). It was reduced to the single testable statement above. If the second half
  of the original candidate mattered, it needs its own candidate row and its own verification pass;
  it is not in this catalog.

---

## 4. Author-contributed requirements

Two requirements. **These are not traceable to a published source.** They were added by the author
from prior fieldwork and verified only in the sense that the author confirms the wording is what
they intend. They are held in a separate section deliberately: any downstream user who needs
source-backed requirements only should take sections 1–3 and stop.

| Req ID | Requirement | Source / Clause | Candidate ID | Derivation |
| --- | --- | --- | --- | --- |
| AUTH-01 | The app shall allow a user to use all self-monitoring features without creating an account. | — (author, prior fieldwork) | AUTHOR-001 | AUTHOR |
| AUTH-02 | The app shall present a plain-language summary of what data leave the device, before first data transmission. | — (author, prior fieldwork) | AUTHOR-002 | AUTHOR |

**Evidence status.** Neither statement has an external clause behind it. To raise them to the same
standing as sections 1–3 they need either (a) a published clause that supports them, or (b) a
written record of the fieldwork — study, sample, date, method — cited as the source. Until then they
should be labelled as author-asserted wherever the catalog is reused.

---

## Summary

| Group | Source | Requirements | Candidates screened | Retention |
| --- | --- | --- | --- | --- |
| Privacy | GDPR | 4 | 6 | 66.7% |
| Security | NIST SP 800-63B | 3 | 5 | 60.0% |
| Accessibility | WCAG 2.2 | 3 | 4 | 75.0% |
| **Source-derived total** | 3 sources | **10** | **15** | **66.7%** |
| Author-contributed | — | 2 | n/a | n/a |
| **Catalog total** | | **12** | | |
