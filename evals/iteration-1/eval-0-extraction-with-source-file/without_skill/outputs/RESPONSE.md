Extraction is done for the excerpt you gave me. Two files in this folder:

- **`requirements-catalog.csv`** — 21 atomic requirements, one per row, with source clause, verbatim text, modality, characteristic mapping, trigger condition, a proposed acceptance criterion, verification method and ambiguity flags.
- **`extraction-notes.md`** — method, coverage tables, verifiability profile, gaps and open items.

All 15 numbered provisions in clauses 5–7 are accounted for. They expand to 21 rows because a few carry more than one obligation (7.2.1 and 7.3.1 each split in two), and because I added two flagged **derived** rows for capabilities the standard presupposes but never states: the opt-in mechanism behind 5.1.1's retention exception, and the setting behind 7.2.2's quiet-hours exception. They're marked so you can exclude them from any count of explicit requirements.

Coverage by your four characteristics: Privacy 7, Safety 7, Personalisation 5, Accessibility 2.

Four things worth deciding before this scales:

1. **Accessibility looks thin but isn't.** 7.1.1 is a single sentence that incorporates ~50 WCAG 2.1 A/AA success criteria by reference. If you report coverage per requirement, that row alone will distort the comparison — you need a counting rule for incorporation by reference. Related: 7.1.2 (200 % text) restates WCAG SC 1.4.4, so it's redundant with 7.1.1. I kept it and flagged the overlap rather than deduplicating, since the restatement signals emphasis.
2. **Clause structure doesn't equal characteristic.** Clause 7 "User interaction" splits three ways — the 22:00–07:00 quiet window (7.2.2) is functionally a safety requirement sitting in a notifications sub-clause. I've recorded secondary characteristics rather than duplicating rows, so the coverage counts don't double-count.
3. **Personalisation is genuinely thin.** 7.3.1 requires disclosure that adaptation is happening and on what data categories — but grants the user no right to opt out of, correct, or turn off adaptation, and says nothing about how adaptation interacts with the risk signals in clause 6. That's a real finding for the paper, not a gap in the extraction.
4. **Prohibitions need their own treatment.** 6.1.2 ("shall not present an automated assessment of suicide risk") is one of the most consequential provisions here and it's a negative requirement — it also constrains what's *shown* to the user, not what's computed internally. Catalogues that normalise everything to positive "shall" statements lose both points.

Two caveats on the source. It's an **excerpt** — clauses 1–4 and anything past clause 7 are missing, and the terms clause is truncated to definition 3.4 alone. That matters because seven terms are used normatively but never defined here: "personally identifiable", "therapeutic content", "non-essential", "engagement-driven", "last active session", "commonly used" format, "persistently reachable". Most are probably in the unseen clause 3; until then each one is an interpretation I'm making on your behalf, flagged per row. Getting the full Part 2 (and Part 1) would resolve most of them.

If you're comparing against other standards later, add a `source_standard` column now rather than retrofitting it. Happy to run the same schema over a second standard, or turn the catalogue into a browsable page if that's easier for co-authors to review than a CSV.
