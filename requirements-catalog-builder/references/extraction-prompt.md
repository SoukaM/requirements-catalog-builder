# Extraction prompt

Use this prompt verbatim for every source, substituting only the bracketed fields. Two reasons it is fixed rather than improvised per source: the paper reports it in an appendix, and a prompt that varies between sources makes the per-source retention rates in the extraction log incomparable.

Save the filled-in copy to `catalog/prompts/extraction-<SOURCE>.md` with the model name and date at the top, then move on to the next source.

---

## The prompt

```
You are extracting candidate software requirements from an authoritative source,
for a requirements catalog in the domain of:

  [DOMAIN SCOPE SENTENCE]

In scope: [INCLUSIONS]
Out of scope: [EXCLUSIONS]

Quality characteristics the catalog covers:
  [LIST OF CHARACTERISTICS WITH THEIR CATEGORY CODES]

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
7. Do not strengthen the clause. The most common drafting error is writing a
   requirement that goes further than its source: adding a deadline the clause
   does not give, turning "shall inform" into "shall obtain consent", turning a
   recommendation into an obligation, or merging two clauses into one broader
   duty. Match the clause's actual force. Where the source is vague, stay vague
   and say so in the rationale rather than inventing a threshold.

Output as a CSV with the header:

cand_id,source,clause,quoted_text,candidate_requirement,category,rationale

Then, after the CSV, list separately any clause you judged important but could not
turn into a testable requirement, with a one-line reason. The reviewer decides what
to do with those.

SOURCE TEXT:

[PASTE FULL TEXT OR THE RELEVANT SECTIONS]
```

---

## What goes in the appendix

The paper appendix needs the prompt as written above, plus, per source: the model identifier, the date of extraction, and whether the full source or only selected sections were supplied. That last one matters, because "we extracted from GDPR" and "we extracted from GDPR Chapters III and IV" are different claims about coverage.

## When the source text cannot be pasted

Long standards will not fit in one context. Split by chapter or clause range, run the prompt per part with the part named in the citation field, and note the split in the appendix. Do not switch to working from recall of the source for the parts that did not fit. A source that is only partly extracted is recorded as partly extracted; that is a normal, reportable limitation.
