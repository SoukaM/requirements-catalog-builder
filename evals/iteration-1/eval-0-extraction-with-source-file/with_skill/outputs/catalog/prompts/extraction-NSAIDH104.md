# Extraction prompt — NSAIDH104

- **Model:** claude-opus-5
- **Date of extraction:** 2026-09-07
- **Source supplied to the model:** excerpt only — clauses 5 to 7 plus definition 3.4,
  as contained in `NSAI-DH-104-2024.txt`. Clauses 1–4 and any clause after 7 were not
  supplied and were not extracted.

---

```
You are extracting candidate software requirements from an authoritative source,
for a requirements catalog in the domain of:

  Mobile applications intended for use by adults to self-manage their mental
  wellbeing, including apps that support self-monitoring, self-directed therapeutic
  content, and behavioural self-management, delivered directly to the user on a
  consumer mobile device.

In scope: native and hybrid mobile apps on consumer smartphones and tablets; adult
users (18+) acting on their own behalf without a clinician in the loop;
self-monitoring of mood, symptoms, activity and free-text journalling; self-directed
therapeutic or psychoeducational content delivered in-app; data the app holds about
the user, including its retention, export and transmission; the behaviour of the app
towards the user, including notifications, content adaptation and crisis signposting.

Out of scope: apps intended for children or adolescents; clinician-facing tools and
care-team dashboards; regulated medical devices making a diagnostic or treatment
claim; desktop and web-only products; obligations falling on the operator or
organisation rather than on the software; crisis-line and emergency-service
integration beyond signposting.

Quality characteristics the catalog covers:
  PRIV  Privacy, including data retention, deletion, portability and transmission
  SAFE  Safety, including clinical safety, crisis handling and content provenance
  ACC   Accessibility
  PERS  Personalisation

The source is:

  NSAI/DH-104:2024, National Standard for Digital Health Applications Supporting
  Adult Mental Wellbeing — Part 2: Product Requirements. Excerpt: clauses 5 to 7.
  Short code: NSAIDH104

The full text of the source follows at the end of this prompt. Work only from that
text. Do not use anything you recall about this source from elsewhere.

For each obligation, prohibition, constraint or capability in the source that a
software product in this domain would have to satisfy, produce one candidate
requirement with these seven fields:

  cand_id                Sequential, prefixed with the source code: NSAIDH104-001
  source                 The source short code
  clause                 The exact locator inside the source: an article and
                         paragraph, a numbered clause, a table and row, or a page
                         and paragraph number. Never a section title alone.
  quoted_text            The source's own words, copied exactly, long enough to
                         show that the clause supports the requirement. Do not
                         paraphrase in this field.
  candidate_requirement  One "shall" statement. One obligation only. Testable.
                         Written about the class of software, not about a vendor
                         or an organisation, unless the obligation genuinely falls
                         on the operator.
  category               One of the category codes listed above.
  rationale              One sentence: why this clause implies this requirement.

Rules:

1. Every candidate must have a clause locator. If you cannot point to a specific
   clause, do not produce the candidate.
2. quoted_text must be copied from the text given to you. If you find yourself
   reconstructing wording, stop and drop the candidate.
3. One obligation per requirement. If a clause carries three obligations, produce
   three candidates.
4. Prefer proposing over withholding. A weak candidate costs the reviewer a few
   seconds; a missed one costs a gap in the catalog. Mark borderline candidates in
   the rationale with "borderline:" and the reason.
5. Do not restate the same obligation twice from the same clause under different
   categories. Pick the better fit and say in the rationale that it also touches
   the other.
6. Skip definitions, scope statements, informative notes and bibliography entries.
   They are not requirements. Skip obligations that fall entirely outside the
   domain scope above.

Output as a CSV with the header:

cand_id,source,clause,quoted_text,candidate_requirement,category,rationale

Then, after the CSV, list separately any clause you judged important but could not
turn into a testable requirement, with a one-line reason. The reviewer decides what
to do with those.

SOURCE TEXT:

[the full contents of NSAI-DH-104-2024.txt, clauses 5 to 7 plus definition 3.4]
```

---

## Clauses judged important but not turned into a testable requirement

| Clause | Text | Why not a requirement |
|---|---|---|
| 5.1.3 (first half) | "Aggregate statistics derived from user records may be retained indefinitely" | A permission, not an obligation. Only its proviso ("provided they cannot be re-identified") is testable, and that is carried as candidate `NSAIDH104-003`, flagged borderline. |
| 5.2.2 | "NOTE An export offered only as a rendered PDF does not satisfy 5.2.1." | Informative note; skipped per rule 6. It is however the sharpest *verification* criterion for `NSAIDH104-004` and is recommended as a note on that requirement and as the wording of its audit-checklist question. |
| 3.4 | "wellbeing record: structured or free-text entry created by a user describing their mental state, mood, activity or symptoms." | A definition. Belongs in SRS section 1.4, not in a requirement table. It is load-bearing: several candidates turn on what counts as a "wellbeing record". |
| Clause headings 5, 5.1, 5.2, 5.3, 6, 6.1, 6.2, 7, 7.1, 7.2, 7.3 | — | Section titles, not obligations. Never cited as a locator on their own. |
