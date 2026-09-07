# Extraction Log

**Domain:** Privacy, security and accessibility requirements for mental wellbeing applications
**Input:** `partial-verification-log.csv`
**Verification window:** two weeks, closing 2026-09-07
**Verification status:** all 17 log entries marked `confirmed`. Nothing pending.

This log records what was screened, what was kept, and — importantly — what was thrown away and why.
The rejections are the part that makes the retention rate meaningful, so they are listed in full.

---

## 1. Retention rates

Retention rate = (KEEP + REWRITE) ÷ candidates screened. Rewrites count as retained: the obligation
survived, only the wording changed. Author-contributed requirements are excluded from every rate
below, because nothing was screened to produce them.

### Per source

| Source | Candidates | KEEP | REWRITE | REJECT | Retained | Retention rate |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| GDPR | 6 | 2 | 2 | 2 | 4 | **66.7%** |
| NIST SP 800-63B | 5 | 2 | 1 | 2 | 3 | **60.0%** |
| WCAG 2.2 | 4 | 2 | 1 | 1 | 3 | **75.0%** |
| **All sources** | **15** | **6** | **4** | **5** | **10** | **66.7%** |

### Composition of the retained set

| Measure | Count | Share of retained |
| --- | ---: | ---: |
| Retained unchanged (KEEP) | 6 | 60.0% |
| Retained after rewrite (REWRITE) | 4 | 40.0% |
| Rejected | 5 | — (33.3% of candidates screened) |

### Catalog composition

| Measure | Count |
| --- | ---: |
| Source-derived requirements | 10 |
| Author-contributed requirements | 2 |
| **Total requirements in catalog** | **12** |

**How to read these numbers.** A two-thirds retention rate across three well-drafted normative
documents is unremarkable and does not indicate a problem with the sources — the rejected candidates
were mostly aimed at clauses that turned out not to say what the candidate claimed. What it does
indicate is that roughly one candidate in three would have entered the catalog as an unsupported
statement had it not been checked. The rate is a measure of the screening, not of the sources.

The rewrite share is the number to watch: 40% of surviving requirements needed their wording
corrected. Three of the four rewrites were the same class of error — the candidate was stronger,
broader or more specific than the clause it cited (an invented deadline, a bundled obligation, an
inflated modal). That is a systematic drafting bias toward over-claiming, and it is worth
correcting upstream rather than catching downstream.

---

## 2. Disposition of every candidate

### GDPR — 6 candidates

| Candidate | Clause | Verdict | Outcome |
| --- | --- | --- | --- |
| PRIV-SRC-001 | Art. 20(1) | KEEP | → PRIV-01 |
| PRIV-SRC-002 | Art. 17(1)(a) | REWRITE | → PRIV-02 |
| PRIV-SRC-003 | Art. 25(2) | KEEP | → PRIV-03 |
| PRIV-SRC-004 | Art. 33(9) | REJECT | dropped — clause not found |
| PRIV-SRC-005 | Art. 5(1)(b) | REJECT | dropped — not a requirement |
| PRIV-SRC-006 | Art. 32(1)(a) | REWRITE | → PRIV-04 |

### NIST SP 800-63B — 5 candidates

| Candidate | Clause | Verdict | Outcome |
| --- | --- | --- | --- |
| SEC-SRC-001 | 5.1.1.2 | KEEP | → SEC-01 |
| SEC-SRC-002 | 5.1.1.2 | KEEP | → SEC-02 |
| SEC-SRC-003 | 5.2.2 | REJECT | dropped — out of scope |
| SEC-SRC-004 | 4.3.1 | REJECT | dropped — clause does not support the candidate |
| SEC-SRC-005 | 5.1.1.2 | REWRITE | → SEC-03 |

### WCAG 2.2 — 4 candidates

| Candidate | Clause | Verdict | Outcome |
| --- | --- | --- | --- |
| USA-SRC-001 | SC 1.4.4 | KEEP | → USA-01 |
| USA-SRC-002 | SC 2.4.7 | KEEP | → USA-02 |
| USA-SRC-003 | SC 3.3.9 | REJECT | dropped — clause not found |
| USA-SRC-004 | SC 1.1.1 | REWRITE | → USA-03 |

### Author-contributed — 2 entries, not screened

| Entry | Verdict | Outcome |
| --- | --- | --- |
| AUTHOR-001 | author | → AUTH-01 (author-asserted, no clause) |
| AUTHOR-002 | author | → AUTH-02 (author-asserted, no clause) |

---

## 3. Rejections, by reason

| Reason | Count | Candidates |
| --- | ---: | --- |
| Clause not found at the cited address | 2 | PRIV-SRC-004 (GDPR Art. 33(9)), USA-SRC-003 (WCAG SC 3.3.9) |
| Clause exists but does not support the candidate | 1 | SEC-SRC-004 (NIST 4.3.1) |
| Cited text is not a requirement | 1 | PRIV-SRC-005 (GDPR Art. 5(1)(b)) |
| Out of scope for this domain | 1 | SEC-SRC-003 (NIST 5.2.2) |

Two of the five rejections are citation failures — the clause address does not resolve. Both are
worth a second look before the log is closed; see the audit checklist, items R1 and R2.

---

## 4. Rewrites, by reason

| Requirement | Reason recorded | Class of error |
| --- | --- | --- |
| PRIV-02 | candidate said "immediately"; source gives no deadline | invented specificity |
| PRIV-04 | candidate bundled encryption at rest and in transit | compound obligation |
| SEC-03 | candidate used "should" | modal inflated / weakened relative to source |
| USA-03 | candidate was compound | compound obligation |

Two compound-obligation rewrites produced dropped halves. **The discarded half of PRIV-SRC-006 —
encryption in transit — was not re-entered as its own candidate.** That is a live gap, not a
decision. The discarded half of USA-SRC-004 is likewise unrecorded.

---

## 5. Coverage gaps

These are stated so the catalog is not read as more complete than it is.

1. **Encryption in transit has no requirement.** PRIV-04 covers data at rest only. GDPR Art. 32(1)(a)
   supports both. A candidate for the in-transit half should be raised and verified.
2. **The dropped half of USA-SRC-004 is unrecorded.** The log notes the candidate was compound but
   does not say what the second obligation was. It cannot be recovered from this log alone.
3. **Security coverage rests on one clause.** All three security requirements come from NIST SP
   800-63B §5.1.1.2. Nothing in the catalog covers session management, multi-factor authentication,
   rate limiting (explicitly rejected as out of scope) or account recovery.
4. **No safety requirements at all.** The domain is mental wellbeing apps, and the catalog contains
   nothing on crisis-support routing, automated risk assessment, clinical-content provenance, or
   notification timing. These are the requirement classes that distinguish a mental wellbeing app
   from any other app handling personal data, and none of the three sources screened addresses them.
5. **A fourth source is sitting unscreened in the same folder.** `NSAI-DH-104-2024.txt` — *National
   Standard for Digital Health Applications Supporting Adult Mental Wellbeing*, Part 2, excerpt of
   clauses 5–7 — is in the fixtures folder but does not appear anywhere in the verification log. It
   is domain-specific in exactly the way the three screened sources are not, and it appears to
   address several of the gaps above directly (retention periods, deletion deadlines, transport
   encryption, crisis-support routing, content provenance, notification timing). **Nothing from it
   has been extracted into this catalog**, because no candidate from it has been verified. It is
   listed here as the single highest-value next extraction pass, not as content.
6. **Author-contributed requirements have no evidence record.** AUTH-01 and AUTH-02 rest on "prior
   fieldwork" with no study, date or method cited. See audit checklist item A1.

---

## 6. Method notes

- Retention rate counts REWRITE as retained. If you prefer a stricter "survived unchanged" measure,
  that figure is 6/15 = 40.0% across all sources.
- Author entries are excluded from retention arithmetic in both directions — they neither inflate
  the numerator nor the denominator.
- Requirement IDs are newly assigned and stable. Candidate IDs from the log are preserved in every
  output so that any requirement can be traced back to its screening row.
- Rejected candidates were assigned no requirement ID, and their candidate IDs are deliberately not
  reused. Gaps in the candidate sequence (PRIV-SRC-004, -005; SEC-SRC-003, -004; USA-SRC-003) are
  the rejections and should stay visible.
