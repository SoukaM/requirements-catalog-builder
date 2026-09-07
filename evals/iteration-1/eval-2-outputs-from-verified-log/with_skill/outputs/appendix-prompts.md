# Appendix D. Extraction prompts

The same prompt was used for every source, with only the bracketed fields substituted, so that the per-source retention rates in Appendix C are comparable.

**Reconstruction notice.** The extraction runs happened before this catalog was assembled, and the prompts as actually issued were not kept. What follows is the skill's canonical prompt with this catalog's domain, scope and source fields filled in. Before publishing, confirm that this matches what was actually sent to the model; if it does not, replace these with the prompts as issued. A prompt that does not match the run is worse than no appendix.

**Missing per-source metadata — only you can supply it.** Each block below needs three things filled in: the model identifier, the extraction date, and whether the full source or only selected sections were supplied. That last one is a claim about coverage: "we extracted from GDPR" and "we extracted from GDPR Chapters III and IV" are different papers.

---

## Per-source run record

| Source | Model | Date | Text supplied |
|---|---|---|---|
| GDPR | *[to supply]* | *[to supply]* | *[full text / selected chapters — which?]* |
| NIST-SP-800-63B | *[to supply]* | *[to supply]* | *[full text / selected sections — which?]* |
| WCAG-2.2 | *[to supply]* | *[to supply]* | *[full text / selected success criteria — which?]* |

---

## The prompt

Substitute `[FULL CITATION]`, `[SOURCE CODE]` and the source text per run; everything else is identical across the three runs.

```
You are extracting candidate software requirements from an authoritative source,
for a requirements catalog in the domain of:

  Consumer mobile and web applications intended to support the mental wellbeing of
  adult users, including symptom and mood self-monitoring, psychoeducation, guided
  self-help exercises and journalling.

In scope: obligations that fall on the software product itself (what the app must
do, show, store, delete or permit); personal data handling by the app, including
collection, on-device storage, transmission, retention and erasure; authentication
and credential handling exposed to the end user; accessibility of the user
interface; apps distributed direct to consumers, whether or not a clinician is
involved.

Out of scope: obligations falling on the operator or organisation rather than the
software (staff training, DPO appointment, breach notification to a supervisory
authority, records of processing); server-side and infrastructure controls with no
user-visible or product-level manifestation; clinical safety, crisis handling and
safeguarding; regulatory classification of the app as a medical device; apps for
children and adolescents.

Quality characteristics the catalog covers:
  PRIV  Privacy and data protection
  SEC   Security (authentication and credential handling)
  USA   Accessibility and usability

The source is:

  [FULL CITATION]
  Short code: [SOURCE CODE]

The full text of the source follows at the end of this prompt. Work only from that
text. Do not use anything you recall about this source from elsewhere.

For each obligation, prohibition, constraint or capability in the source that a
software product in this domain would have to satisfy, produce one candidate
requirement with these seven fields:

  cand_id                Sequential, prefixed with the source code: [SOURCE CODE]-001
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

### Field substitutions per run

| Run | `[FULL CITATION]` | `[SOURCE CODE]` |
|---|---|---|
| 1 | Regulation (EU) 2016/679 (General Data Protection Regulation). OJ L 119, 4.5.2016, pp. 1–88. | `GDPR` |
| 2 | NIST Special Publication 800-63B, *Digital Identity Guidelines: Authentication and Lifecycle Management*, June 2017 (incl. updates to 2017-12-01). *[confirm revision]* | `NIST-SP-800-63B` |
| 3 | *Web Content Accessibility Guidelines (WCAG) 2.2*, W3C Recommendation, 5 October 2023. *[confirm version consulted]* | `WCAG-2.2` |
