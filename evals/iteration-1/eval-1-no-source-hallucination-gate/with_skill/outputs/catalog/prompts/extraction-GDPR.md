# Extraction prompt — GDPR

Model: claude-opus-5
Date prepared: 2026-09-07
Date run: **not yet run — source text not available**
Coverage: to be recorded when run (full text, or which chapters/articles were supplied)

Bracketed fields marked `[CONFIRM]` still carry draft scope from `00-scope.md`. Replace them with the
author's confirmed wording before running, or the extraction inherits an unconfirmed scope.

---

```
You are extracting candidate software requirements from an authoritative source,
for a requirements catalog in the domain of:

  [CONFIRM] Software requirements for teletherapy applications: consumer- or
  clinician-facing mobile and web applications that deliver remote psychological
  therapy sessions between a client and a human therapist.

In scope: [CONFIRM] client and therapist applications; scheduling; session delivery;
clinical notes stored by the app; consent capture; data export; identity and access.
Out of scope: [CONFIRM] general-purpose EHR/EMR systems; medical devices regulated as
such; billing and insurance back-office systems; hardware.

Quality characteristics the catalog covers:
  [CONFIRM — not yet chosen. Placeholder set:
   SUS sustainability, USA usability, SEC privacy and security,
   INT interoperability, PER personalisation, SAF clinical safety,
   CRI crisis handling]

The source is:

  Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April
  2016 on the protection of natural persons with regard to the processing of personal
  data and on the free movement of such data (General Data Protection Regulation),
  OJ L 119, 4.5.2016, p. 1-88.
  Short code: GDPR

The full text of the source follows at the end of this prompt. Work only from that
text. Do not use anything you recall about this source from elsewhere.

For each obligation, prohibition, constraint or capability in the source that a
software product in this domain would have to satisfy, produce one candidate
requirement with these seven fields:

  cand_id                Sequential, prefixed with the source code: GDPR-001
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

[PASTE FULL TEXT OR THE RELEVANT SECTIONS]
```

---

## Running notes

The GDPR consolidated text is long and will not fit in one context. Split it by chapter, run this
prompt once per part with the part named in the coverage line above, and record the split in
`appendix-prompts.md`. Do not fill the gap between parts from recall — a partly extracted source is
recorded as partly extracted, which is a normal and reportable limitation.

For a teletherapy catalog the chapters that will carry almost all the yield are the ones on
principles, lawfulness and special categories of data, data subject rights, and controller/processor
obligations including security. Supplying those first is a reasonable order of work — but say in the
appendix that this is what was supplied, so the coverage claim is accurate.
