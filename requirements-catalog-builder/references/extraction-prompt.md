# Extraction prompt

There are two variants below: **normative**, for sources whose requirements live in prose ("shall", "should", "we recommend"), and **instrument**, for validated questionnaires, evaluation frameworks, coding taxonomies and assessment checklists whose requirements live in the item list itself. Use whichever variant matches the source's `type` in `catalog/01-sources.md`, verbatim, substituting only the bracketed fields. Two reasons each is fixed rather than improvised per source: the paper reports it in an appendix, and a prompt that varies between sources makes the per-source retention rates in the extraction log incomparable.

Save the filled-in copy to `catalog/prompts/extraction-<SOURCE>.md` with the model name, date, and which variant was used at the top, then move on to the next source.

---

## The normative prompt

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

## The instrument prompt

Use this variant for a source tagged `instrument`: a validated questionnaire, evaluation framework, coding taxonomy or assessment checklist. Its content is the item list, not the surrounding prose, so this prompt sends the model to the items directly instead of asking it to hunt for normative verbs that mostly are not there.

```
You are extracting candidate software requirements from a validated instrument —
a questionnaire, evaluation framework, coding taxonomy or assessment checklist —
for a requirements catalog in the domain of:

  [DOMAIN SCOPE SENTENCE]

In scope: [INCLUSIONS]
Out of scope: [EXCLUSIONS]

Quality characteristics the catalog covers:
  [LIST OF CHARACTERISTICS WITH THEIR CATEGORY CODES]

The source is:

  [FULL CITATION]
  Short code: [SOURCE CODE]

This source carries a validated instrument (a numbered or coded item list: a
questionnaire, a set of assessment criteria, a coding scheme, a checklist). The
instrument's own items are what you extract from, not the paper's introduction,
discussion or conclusion. Prose sections around the instrument usually report
findings from applying it to a sample of existing products; that is evidence about
the current market, not the source of the requirements. Locate the full item list
first — a table, an appendix, a coding scheme definition — and confirm you have
every item before extracting. The full text of the source, including the item
list, follows at the end of this prompt. Work only from that text.

For EVERY item in the instrument, without skipping any as too minor or too
obvious, produce one candidate requirement with these seven fields:

  cand_id                Sequential, prefixed with the source code: [SOURCE CODE]-001
  source                 The source short code
  clause                 The item identifier exactly as the source prints it:
                         "item TF29", "Table 1, Tracking", "item 47", "criterion 12".
                         Not a paraphrase of what the item covers.
  quoted_text            The item's own wording: the questionnaire item, the
                         coding-scheme description, the checklist row. Copy it
                         exactly, do not summarise it.
  candidate_requirement  One "shall" statement converting the item into an
                         obligation. This is a format change, not an inference:
                         "TF29: user authentication" becomes "The app shall
                         provide user authentication." Do not add scope, a
                         mechanism, or a threshold the item itself does not name.
  category               One of the category codes listed above.
  rationale               One sentence: which instrument block or category this
                         item belongs to, and whether it is a plausible duplicate
                         of a requirement from another source (name the other
                         source and item if so). If the paper reports a
                         prevalence figure for this item (e.g. "present in 24%
                         of apps"), you may cite it here as evidence the item is
                         a real discriminator, but the figure is not itself the
                         requirement and must not appear in candidate_requirement.

Rules:

1. Work through the item list exhaustively, in the order the instrument presents
   it. Do not pre-select the items that read most like requirements to you; an
   item that looks minor may be exactly what the catalog's quality characteristics
   need. If the instrument has 38 items, produce 38 candidates (fewer only for
   items ruled out by rule 6 below).
2. Do NOT hunt the surrounding prose for "shall" / "should" / "we recommend"
   sentences as your primary source. If the paper's introduction, discussion or
   conclusion also contains a small number of genuine normative statements
   distinct from the instrument's items, note them but extract them under the
   normative prompt's rules, in their own candidates, clearly separated from the
   item-derived ones — do not blend the two extraction modes into one pass.
3. Do not convert a prevalence or scoring statistic into a requirement or into a
   qualifier on one ("shall usually provide...", "shall provide in most cases...").
   The item is the requirement; the percentage is evidence about the sample the
   source studied, not part of the obligation.
4. One obligation per item. If a single item bundles two distinct capabilities,
   split it into two candidates and say so in the rationale.
5. Flag likely duplicates across sources explicitly in the rationale, by name of
   the other source and its item or clause. Instruments in the same domain
   overlap heavily, and the reviewer needs to merge these before IDs are
   assigned in Phase 5, not discover the overlap after publication.
6. Skip items that are purely descriptive metadata about the product being
   assessed (name, cost, platform, country of origin, date of latest update) and
   carry no functional or quality obligation of their own. Skip items that fall
   entirely outside the domain scope above.

Output as a CSV with the header:

cand_id,source,clause,quoted_text,candidate_requirement,category,rationale

Then, after the CSV, list separately any items you judged out of scope or purely
descriptive under rule 6, with a one-line reason each, so the reviewer can check
that call rather than wonder where an item went.

SOURCE TEXT:

[PASTE FULL TEXT OR THE RELEVANT SECTIONS, INCLUDING THE COMPLETE ITEM LIST]
```

---

## What goes in the appendix

The paper appendix needs the prompt as written above (both variants, since different sources may have used different ones), plus, per source: the model identifier, the date of extraction, which variant was used, and whether the full source or only selected sections were supplied. That last one matters, because "we extracted from GDPR" and "we extracted from GDPR Chapters III and IV" are different claims about coverage.

## When the source text cannot be pasted

Long standards will not fit in one context. Split by chapter or clause range, run the prompt per part with the part named in the citation field, and note the split in the appendix. Do not switch to working from recall of the source for the parts that did not fit. A source that is only partly extracted is recorded as partly extracted; that is a normal, reportable limitation.
