# Validation rules: keep, rewrite, reject

Read this before running phase 3, and use it when proposing a rewrite so that the user is choosing between a bad version and a fixed one rather than being asked to write from scratch.

The first check is always the citation. Everything below it is about the quality of the requirement, and it only matters once the clause has been confirmed. A beautifully formed requirement hanging off a clause that does not exist is the worst possible outcome, because it survives review.

## Check 1: does the citation hold?

Three questions, in order:

1. **Does the clause exist?** The locator resolves to a real place in the source.
2. **Does it say what was quoted?** The `quoted_text` matches the source's own words.
3. **Does it support the requirement?** The requirement is a fair reading of that clause, not of a neighbouring one and not of the standard's general spirit.

Any "no" means REJECT, with the reason recorded. Do not rescue a candidate by hunting for a different clause that would support it: that is a new candidate, extracted properly, not a repair.

Watch for the near-miss, which is the most common and most dangerous failure. The clause exists, the subject matter is right, and the obligation has been strengthened, generalised or invented in a plausible direction: the source says the controller "shall inform the data subject", the requirement says "shall obtain explicit consent". Reject those. They read as correct to anyone who does not open the source, which is most readers.

## Check 2: is it a well-formed requirement?

IEEE 29148 gives nine quality attributes for an individual requirement. Use them as the rewrite checklist.

| Attribute | Test |
|---|---|
| Necessary | Removing it would leave a real gap. |
| Appropriate | Stated at the right level of abstraction, and does not over-constrain the design. |
| Unambiguous | One reading only. No "appropriate", "adequate", "user-friendly", "as needed", "where possible". |
| Complete | Stands on its own, no dangling reference to something unstated. |
| Singular | One obligation. No "and", no "and/or", no bullet list smuggled into a sentence. |
| Feasible | Achievable by software in this class, with current technology. |
| Verifiable | Someone could inspect, test or demonstrate whether it holds. This is what makes the audit checklist possible. |
| Correct | A true rendering of the source clause. |
| Conforming | Uses the catalog's standard sentence form. |

Standard sentence form: `The [system / app] shall [action] [object] [condition or constraint].`

Use "shall" for obligations. Reserve "should" for recommendations that the source itself framed as recommendations, and mark those in the note so a reader can tell a legal duty from good practice. Avoid "will", "must" and "may" in requirement text, since mixing modal verbs makes conformance ambiguous.

## Verdict criteria

**KEEP** when the citation holds and the requirement passes every attribute above. Do not rewrite for style. Churning wording that is already correct inflates the AI-R count and misrepresents the extraction quality the log is reporting.

**REWRITE** when the citation holds but the requirement fails on form. Typical causes, with the fix:

- *Compound*: split into two or more requirements, each with its own ID, all citing the same clause.
- *Vague qualifier*: replace with a measurable or observable criterion, or, if the source itself is vague, keep the vagueness and say so in the note. Do not invent a threshold the source does not give. A fabricated "within 3 seconds" is the same class of error as a fabricated clause number.
- *Wrong subject*: the requirement is about the organisation when the source obliges the software, or the reverse.
- *Wrong modality*: the source recommends, the requirement commands.
- *Too specific*: the requirement names a technology where the source names a capability. Catalogs outlive technologies.
- *Too abstract*: the requirement restates the clause heading and cannot be tested.

**REJECT** when:

- The citation fails any of the three questions in check 1.
- The text is a definition, a scope note, an informative note, an example, or a bibliography entry rather than an obligation.
- The obligation falls outside the domain scope agreed in phase 0. Point at the scope sentence when recording the reason.
- It duplicates a requirement already in the catalog. Record which ID it duplicates, since duplicates found across sources are worth a sentence in the paper: they show which obligations are corroborated by several authorities.
- It is untestable in principle, not just badly worded.
- It obliges the operator rather than the software and the catalog is about software. If the user wants operator obligations too, that is a scope decision to make explicitly in phase 0, not a judgement call made here.

## Recording the reason

Every rejection gets a reason from a fixed set, so that the rejections are countable and a reviewer can see the shape of what went wrong:

`clause not found` / `clause does not support` / `not a requirement` / `out of scope` / `duplicate of <ID>` / `untestable` / `wrong actor`

`clause not found` and `clause does not support` are the two that matter most for the paper. Report their combined count alongside the retention rate: it is the direct measure of how often the model fabricated or misread a citation, and it is the number a methods-minded reviewer will want.

## Reopening a rejection

Rejections are human judgements made quickly, and they are wrong sometimes too. The one that matters is `clause not found`, because it can mean the clause genuinely does not exist, or it can mean the wrong edition was open: standards renumber between revisions, and a clause that is missing from WCAG 2.1 may be present in 2.2, a NIST locator from Rev 3 may not survive Rev 4.

So when a rejection reason is `clause not found`, check that the edition consulted is the edition cited in the source register. If a later source, a co-author, or your own reading suggests a rejected clause does exist, reopen it: re-verify against the right edition and record the change of verdict in the log rather than editing the old row silently. Note the reopening in the extraction log, since a corrected rejection moves the retention rate and a reader is entitled to see that the number was revised.

Do not reopen a rejection on the strength of a model's recall that the clause exists. That is the same failure the method is guarding against, just running in the opposite direction. Reopening means going back to the document.

## A note on pace

Verification is slow, and it should be. A realistic rate is roughly 20 to 40 candidates an hour when the sources are open and being checked properly. If the user is going much faster than that, they are probably reading the requirements rather than the clauses. Say so once, kindly, and offer to break the batch across sessions. Do not nag past that: it is their paper and their name on it.
