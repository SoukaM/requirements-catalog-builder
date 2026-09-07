# Extraction notes — NSAI/DH-104:2024 Part 2 (Clauses 5–7 excerpt)

Source file: `NSAI-DH-104-2024.txt` — "National Standard for Digital Health Applications
Supporting Adult Mental Wellbeing, Part 2: Product Requirements (excerpt: Clauses 5 to 7)".
Extraction date: 2026-09-07. Companion file: `requirements-catalog.csv`.

## 1. Method

**Unit of extraction.** One catalogue row = one atomic, independently verifiable obligation.
Where a single numbered provision carries two obligations joined by "and", it is split
(7.2.1 → MW-PER-001/002; 7.3.1 → MW-PER-004/005). Where a provision offers alternative
ways to comply ("withdrawn **or** re-reviewed", 6.2.2), it is **not** split — either branch
satisfies it, so splitting would manufacture a requirement the standard does not impose.

**Modality is recorded, not normalised.** The catalogue distinguishes `shall`,
`shall not` (prohibition), and `may` (constrained permission). Prohibitions and permissions
are kept in the catalogue rather than dropped: 6.1.2 is one of the most consequential
provisions in the safety clause and it is a prohibition, and 5.1.3's binding content sits
entirely in its proviso.

**Derived requirements are flagged.** Two rows (MW-PRV-002, MW-PER-003) are not stated as
requirements; they are capabilities presupposed by the "unless the user has explicitly
opted in / configured otherwise" exceptions in 5.1.1 and 7.2.2. They are included because a
catalogue that records only the exception loses the control the exception depends on, but
they carry `derivation = derived from stated exception` so they can be excluded from any
count of the standard's explicit requirements.

**Traceability.** Every row carries its source clause and the verbatim sentence, so the
catalogue can be re-derived from, and audited against, the source text.

## 2. What is in the excerpt

| | count |
|---|---|
| Numbered provisions in clauses 5–7 | 15 |
| — of which `shall` / `shall not` | 14 |
| — of which `may` | 1 (5.1.3) |
| Non-normative items (NOTE, definition) | 2 |
| Atomic catalogue rows | 21 |
| — explicit | 19 |
| — derived from stated exceptions | 2 |

### Coverage by quality characteristic (primary assignment)

| Characteristic | Rows | Source clauses |
|---|---|---|
| Privacy | 7 | 5.1.1, 5.1.2, 5.1.3, 5.2.1 (×2), 5.3.1 |
| Safety | 7 | 6.1.1, 6.1.2, 6.1.3, 6.2.1 (×2), 6.2.2, 7.2.2 |
| Accessibility | 2 | 7.1.1, 7.1.2 |
| Personalisation | 5 | 7.2.1 (×2), 7.2.2, 7.3.1 (×2) |

Clause structure and characteristic do not line up one-to-one, which is the point of the
mapping. Clause 7 "User interaction" splits across three characteristics: 7.2 Notifications
carries a safety obligation (the 22:00–07:00 quiet window, MW-SAF-007) alongside two
personalisation obligations. Where a row plausibly serves two characteristics, the
secondary is recorded rather than the row duplicated — dual-counting would inflate the
coverage figures above.

Two placements are judgement calls worth stating explicitly in the paper's method section:

- **MW-SAF-007 (quiet hours)** is filed under Safety because its function is protecting
  sleep, with Personalisation secondary because the user can override it. It sits in the
  Notifications sub-clause alongside the personalisation rows.
- **MW-PRV-005/006 (export)** are filed under Privacy as data-subject rights, though data
  portability is sometimes catalogued under interoperability.

## 3. Non-normative items retained

These are not requirements and are excluded from the catalogue counts, but they change how
two rows are assessed and should be carried into the paper:

| Item | Type | Effect |
|---|---|---|
| 5.2.2 NOTE — "An export offered only as a rendered PDF does not satisfy 5.2.1." | Note | Supplies the only concrete acceptance test for MW-PRV-006. Notes are informative in standards drafting, so this is interpretive guidance, not an additional requirement. |
| 3.4 wellbeing record — "structured or free-text entry created by a user describing their mental state, mood, activity or symptoms." | Definition | Scopes MW-PRV-001, 003, 005. Confirms free-text entries are in scope for retention, deletion and export, linking clause 5 to the free-text trigger in 6.1.1. |

## 4. Verifiability profile

Useful for the paper if it says anything about how testable the standard is. Covers the
19 explicit rows; the 2 derived rows are excluded.

- **Objectively verifiable against a stated threshold (8 rows):** 24 months (MW-PRV-001),
  30 days (MW-PRV-003), 36 months (MW-SAF-006), 200 % (MW-ACC-002), 22:00–07:00
  (MW-SAF-007), plus the presence checks MW-SAF-003, MW-SAF-005, MW-PER-002.
- **Verifiable but with an undefined term in the predicate (7 rows):** "personally
  identifiable", "commonly used", "persistently reachable", "therapeutic content",
  "non-essential", "engagement-driven", "identifiable source".
- **Judgement-based (2 rows):** MW-PRV-004 (no re-identification test or threshold named),
  MW-SAF-002 (boundary between an automated risk assessment and generic risk messaging).
- **Time-dependent (1 row):** MW-PRV-007 — "current, non-deprecated" means conformance can
  lapse without any change to the product.
- **Incorporation by reference (1 row):** MW-ACC-001 pulls in roughly 50 WCAG 2.1 A/AA
  success criteria behind a single sentence. Any per-requirement weighting in the paper
  will need a rule for this row, or accessibility will look far thinner than it is —
  2 rows against 7 for privacy is an artefact of drafting style, not of coverage.

## 5. Gaps and open items

**The source is an excerpt.** Only clauses 5–7 are present, and only definition 3.4 of the
terms clause. Missing: clause 1 scope, clause 2 normative references, clauses 3–4 (terms
and any general/conformance requirements), and anything after clause 7. The catalogue
should be treated as partial until the full Part 2 is obtained. Part 1 is also referenced
by the numbering convention and has not been seen.

**Undefined terms used normatively.** "Personally identifiable", "therapeutic content",
"non-essential" (notification), "engagement-driven", "last active session", "commonly used"
(format), "persistently reachable". Several are likely defined in the unseen part of
clause 3. Until then, each is an interpretation the catalogue is making on the reader's
behalf; the ambiguity is recorded per row in the `ambiguity_flags` column.

**Characteristic-level gaps in what is present:**

- *Privacy* — encryption is required in transit only, with nothing on data at rest.
  Nothing on lawful basis or consent for collection, third-party sharing or processors,
  or breach handling. Deletion (5.1.2) is silent on backups.
- *Safety* — nothing on escalation to a human, on adverse-event reporting, on clinical
  safety governance, or on what the crisis support information must contain or how
  current it must be. 6.1.2 constrains what is *shown* to the user, not what is computed.
- *Accessibility* — two provisions, one of which is a subset of the other. Nothing beyond
  WCAG on cognitive accessibility, plain language, or accessibility of the crisis route
  specifically (MW-SAF-001 has an accessibility dependency recorded as secondary).
- *Personalisation* — the thinnest characteristic in substance. 7.3.1 requires disclosure
  of adaptation but grants the user no right to **opt out of, correct, or switch off**
  adaptation, and says nothing about how adaptation interacts with the risk signals in 6.1.

**Redundancy to note rather than resolve:** MW-ACC-002 (200 % text) restates WCAG 2.1
SC 1.4.4, already required by MW-ACC-001. Deduplicating would erase the standard's
deliberate emphasis; the relationship is recorded in the row's flags instead.

## 6. Suggested next steps

1. Obtain full Part 2 (and Part 1) and re-run the extraction — clause 3 in particular will
   resolve most of the ambiguity flags.
2. Confirm the catalogue schema before scaling to further standards. The current columns
   are: `req_id, source_clause, clause_title, modality, normative, derivation,
   primary_characteristic, secondary_characteristics, requirement_statement,
   verbatim_source_text, condition_trigger, acceptance_criterion, verification_method,
   verifiability, ambiguity_flags`. If the paper compares standards, add a
   `source_standard` column now.
3. Decide the counting rule for MW-ACC-001 (WCAG by reference) before reporting any
   coverage percentages.
4. Decide whether derived rows (MW-PRV-002, MW-PER-003) are in scope for the paper's
   counts, or reporting-only.
