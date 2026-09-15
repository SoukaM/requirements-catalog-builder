---
name: requirements-catalog-builder
description: Builds a publication-grade software requirements catalog for any domain. Extracts candidate "shall" statements from standards, laws, papers, validated questionnaires, evaluation frameworks and coding taxonomies; forces human verification of every clause/item citation; tags origin (human / AI-kept / AI-rewritten); organises survivors into an IEEE 29148 SRS with requirement tables, extraction log and audit checklist. Use for a requirements catalog, requirements set/framework or compliance checklist; for SIREN, IEEE 29148, ISO 25010, an SRS, requirements elicitation/engineering; for a "requirements for X apps" catalog paper; to pull requirements from a regulation, guideline or standard (GDPR, HIPAA, WHO, ISO/IEC, clinical guidelines) even without the word "catalog"; and whenever a source is or contains a validated questionnaire, assessment instrument, coding scheme, or item-based checklist, even buried inside a narrative paper. Also for an audit checklist or evaluation instrument derived from standards.
---

# Requirements Catalog Builder

## What this is for

A requirements catalog is a reusable, traceable set of requirements for a *class* of software, not for one product. It is the artefact behind a family of published catalog papers (Ouhbi, Zapata, Bachiri, Sardi, all with Ali Idri) that follow the SIREN approach: harvest requirements from authoritative sources, keep every one anchored to its clause, structure the result as an IEEE 29148 SRS, and derive an evaluation instrument from it.

The method is fixed. The domain and the sources are inputs. This skill works the same way for anxiety and depression apps, for pregnancy tracking apps, for agricultural IoT dashboards, or for accounting software.

**The single thing that makes or breaks this work: a model can produce a clause number that looks perfect and does not exist, or exists and says something else entirely.** One fabricated citation in a published catalog is a retraction-class error, and reviewers of this exact paper genre check citations. So the pipeline below is built so that no requirement can reach the catalog without a human having opened the source and looked at the clause. Everything else in this skill is bookkeeping around that gate.

## Working posture

Work in phases and stop at the end of each one. Do not run the whole pipeline and present a finished catalog: the user has to do real work in phase 3, and a catalog that arrives fully formed invites them to rubber-stamp it, which defeats the point. Announce which phase you are in and what the user has to do next.

Keep everything in a working directory (default `catalog/` in the current folder). Write files as you go rather than holding state in conversation, because these projects run over days.

---

## Phase 0: Scope intake

Ask for these three things. Do not guess any of them.

1. **The domain.** Push for precision. "Mental health apps" is too broad to bound a catalog; "mobile apps for self-management of anxiety and depression in adults" is a scope statement. Write the scope as one sentence plus explicit inclusions and exclusions, and get the user to confirm the wording, because this sentence is what justifies every later rejection for "out of scope".

2. **The sources.** For each: full citation, type (international standard, national law, clinical guideline, professional body guidance, systematic review, primary study), and critically, **whether the user has the actual full text**. A standard the user cannot open cannot be verified, so it cannot contribute a requirement. Record it as a source they need to obtain rather than dropping it silently.

3. **The quality characteristics to cover.** Ask the user to list them. Do not impose a standard menu, because the choice of characteristics is itself a contribution of the paper and different domains need different ones. If they want a starting point, offer ISO/IEC 25010 characteristics, or the recurring e-health set (sustainability, usability, privacy and security, interoperability, personalisation), but let them decide and let them add domain-specific ones such as clinical safety or crisis handling.

Write the result to `catalog/00-scope.md` and get explicit confirmation before extracting anything.

## Phase 1: Source register

Create `catalog/01-sources.md`: one row per source with a short code (`ISO25010`, `GDPR`, `NICE-CG113`), the full citation, the file path if available, status (`full text available` / `to obtain`), and **type** (`normative` / `instrument`). Extraction runs per source and every candidate carries this code, so settle the codes now.

Type decides which extraction mode Phase 2 uses for that source, so get it right here rather than discovering it mid-extraction:

- **`normative`**: standards, regulations, guidelines, and papers whose requirements live in prose — "shall", "should", "we recommend", "developers are required to". Most standards and laws are this type.
- **`instrument`**: validated questionnaires, evaluation frameworks, coding taxonomies, and assessment checklists. Their requirements live in the item list itself, not in a sentence anywhere. A 38-item assessment questionnaire *is* 38 candidate requirements; the paper's two-sentence conclusion is not where the content is.

The trap is that an empirical paper reporting an instrument still reads like a normative source: it has an introduction, a discussion, a conclusion, and those sections may contain a handful of genuine "should" sentences. Hunting only for those verbs on a paper like this will find a few real candidates and miss the instrument entirely, because the instrument's 30-plus items were never phrased as obligations, they were phrased as questions or codes for scoring a sample. Judge the type by where the requirements actually live, not by whether the source is a paper versus a standard: a systematic review built around a validated coding scheme or assessment questionnaire is an `instrument` source even though it is, formally, a paper.

## Phase 2: Candidate extraction

Extract from one source at a time, and only from sources whose text you actually have in front of you.

**If the source file is available**, read it and extract from the text. Quote the clause. This is the only mode that produces trustworthy candidates.

**If it is not available**, do not extract from memory of the standard. Say plainly that you can recall the general shape of, say, GDPR Article 17 but cannot be trusted with its exact clause numbering or wording, and ask the user to supply the text or to extract that source by hand. Producing plausible-looking clause references from recall is the exact failure mode this skill exists to prevent, and it is worse than producing nothing, because it looks like work.

Use the extraction prompt in `references/extraction-prompt.md` verbatim, so that the prompt can be reported in the paper appendix and the extraction is reproducible. It has two variants, normative and instrument; use the one matching the source's type from the Phase 1 register. Save the filled-in version (with the domain and source substituted) to `catalog/prompts/extraction-<SOURCE>.md`.

Each candidate is a row in `catalog/02-candidates-<SOURCE>.csv` with these columns:

`cand_id | source | clause | quoted_text | candidate_requirement | category | rationale`

- `clause` is the exact locator: "Art. 17(1)(a)", "clause 6.2.3", "Table 4, row 2", "p. 412, para 3". A candidate without a clause locator is not a candidate; drop it.
- `quoted_text` is the source's own words, copied not paraphrased. This is what the user compares against in phase 3, and it is what makes verification take seconds instead of minutes.
- `candidate_requirement` is a single "shall" statement: one obligation, testable, no "and/or" bundling. See `references/validation-rules.md` for what a well-formed requirement looks like.
- `category` maps to one of the user's quality characteristics or to a functional area.

Extract generously here. It is cheap for the user to reject a candidate and expensive for them to notice a missing one, so err toward proposing.

### Instrument sources

For a source tagged `instrument` in the register, the mode above is the wrong one to run, and running it anyway is how a 44-app study with a 38-item questionnaire yields three candidates instead of forty. Do not hunt for normative verbs in the prose. Go straight to the item table, coding scheme, or criteria appendix — that is where the source's content actually is, and the prose around it (introduction, discussion, conclusion) is mostly discussion of *findings using* the instrument, not the instrument's own content.

Convert every item to a "shall" statement. This is a format change, not an inference, so it does not need the same evidentiary hedging a normative source needs: the source already decided this item matters enough to measure across its whole sample, which is a stronger claim than one sentence of prose. "TF29: user authentication" becomes "The app shall provide user authentication." "Item 47, does the app support offline access to key features?" becomes "The app shall support offline access to key features." Work through the item list exhaustively rather than picking out the ones that feel most requirement-shaped; an item that seems minor to you may be exactly the one the user's quality characteristics need.

- `clause` is the item identifier exactly as the source prints it: "item TF29", "Table 1, Tracking", "item 47". Not a paraphrase of what the item is about.
- `quoted_text` is the item's own wording: the questionnaire item, the coding-scheme description, the checklist row. Copy it, do not summarise it.
- Do not convert prevalence figures into requirements. "Present in 24% of apps" or "achieved by 9 of 44 apps" is a finding about the sample the source studied, not a requirement about software in general — it tells you how well the field currently does at meeting the item, not whether the item belongs in the catalog. The item is the requirement; the percentage, if you want to use it at all, belongs in the rationale as evidence that the item is a real discriminator between apps rather than something every app already does or nothing ever does.
- Flag duplicates across instruments explicitly in the rationale. Instruments in the same domain overlap heavily — a mood-tracking item in one questionnaire is often the same requirement as a self-monitoring item in another — and the user needs to merge these before Phase 5 assigns IDs, or the catalog double-counts the same requirement under two sources. Do not silently drop the duplicate yourself; that is the user's call to make with both quotations in front of them.

Use the instrument variant of the extraction prompt in `references/extraction-prompt.md` for these sources, the same way the normative variant is used for the rest.

## Phase 3: Human verification gate

This is the phase the skill exists for, so give it weight rather than treating it as a review step.

Present candidates to the user in batches of 10 to 15, one source at a time. For each candidate show: the clause locator, the quoted source text, and the proposed requirement. Ask for one of three verdicts:

- **KEEP**: the clause exists, says what is quoted, and the requirement is a fair rendering.
- **REWRITE**: the clause checks out but the requirement needs different wording. The user gives the new wording, or asks you to propose one and then approves it.
- **REJECT**: the clause does not exist, does not say that, or the requirement fails a validation rule.

State the rule at the start of the phase, and restate it if the user starts moving fast: **verification means opening the source and looking at the clause, not judging whether the requirement sounds sensible.** A requirement can read perfectly and be attached to a clause that does not exist. If the user says "these all look fine, keep them all", ask whether they opened the source, and offer to slow down to one source per session instead. Do not refuse to proceed, since it is their paper, but do record it: any candidate the user waved through without confirming the clause gets `verified = not confirmed` in the log, and the catalog carries a note saying which sources have unconfirmed citations. An honest record of a shortcut is more useful than a silent one.

Record every verdict in `catalog/03-verification-log.csv`:

`cand_id | source | clause | verdict | verified | final_text | note`

Rejections stay in this file with their reason. They never appear in the catalog, but the counts feed the extraction log, and a reviewer asking "what did the model get wrong" is answered from here.

The user can also add requirements of their own at any point, from their expertise or from a source they extracted by hand. Add them straight into the verification log with `verdict = author` so they flow into the catalog with the right origin tag.

## Phase 4: Origin tagging

Every surviving requirement carries exactly one origin tag. This is a research result: it tells a reader how much of the catalog the model actually produced and how much survived contact with the sources.

| Tag | Meaning |
|---|---|
| `H` | The user wrote it themselves. The model did not propose it. |
| `AI-K` | The model proposed it, the user kept it as is. |
| `AI-R` | The model proposed it, the user rewrote it. |

Derive the tag from the verification log rather than asking again: `author` becomes `H`, `KEEP` becomes `AI-K`, `REWRITE` becomes `AI-R`. A cosmetic fix that you made and the user approved is still `AI-R`, since the honest question the tag answers is "did the model's wording stand unchanged".

## Phase 5: Identifiers and SRS structure

Assign IDs of the form `<CAT>-<nn>`, where `<CAT>` is a three or four letter category code (`USA-01`, `SEC-07`, `INTEROP-03`). Numbering is per category, starting at 01, in the order requirements appear in the catalog. IDs are permanent once assigned: if a requirement is dropped later, retire its ID rather than renumbering, because the audit checklist and any published version cite these IDs.

Organise the requirements into the IEEE 29148 SRS structure given in `references/srs-structure.md`. Read that file before laying out the catalog. Map the user's quality characteristics onto the standard's sections rather than inventing a parallel structure, and where a characteristic has no natural home (a domain-specific one such as clinical safety), place it under software system attributes and say so in the introduction.

## Phase 6: Outputs

Produce all four. They are written to `catalog/` and are the deliverable set.

**1. Requirement tables**, one per category, in `catalog/catalog.md` and in `catalog/catalog-table.csv`. Columns:

`ID | Requirement | Source (with clause) | Origin`

The source cell carries the clause, not just the source name: `ISO/IEC 25010, clause 4.2.4` and not `ISO 25010`. A table that loses the clause loses the traceability the whole method was built for.

**2. Extraction log**, `catalog/extraction-log.csv` and rendered in `catalog.md`. Columns:

`Source | Candidates proposed | Kept | Rewritten | Rejected | Retention rate`

with a TOTAL row. Retention rate is `(kept + rewritten) / proposed`, one decimal place, as a percentage.

Present this as a finding, not as admin: it is the paper's evidence about how AI-assisted extraction performed against human verification. Two things to say about the numbers rather than leaving the reader to work them out.

First, report the **citation failure rate** separately and lead with it: the count of `clause not found` plus `clause does not support`, over candidates proposed. Retention rate mixes citation failures together with rejections for scope and for form, which are different kinds of error and reflect on different things. A 70% retention rate hiding a 20% citation failure rate is a very different result from one where every rejection was a scope call, and the citation figure is the one a methods reviewer will look for.

Second, interpret the per-source spread, and say honestly when it will not carry weight. A standard at 80% next to a guideline at 30% invites a claim about source types, and with five candidates per source that claim is noise. Say which it is.

**3. Audit checklist**, `catalog/audit-checklist.md` and `.csv`. One question per requirement, phrased so an assessor can answer it while looking at an app, with the answer domain `Yes / No / Partially / N/A`. Keep the requirement ID on each question, since the checklist's value is that a failed answer points back at a specific requirement and its clause.

Turn `The app shall allow the user to export their data in a machine-readable format` into `Does the app allow the user to export their data in a machine-readable format?` Avoid compound questions: if a requirement generates a question with an "and" in it, the requirement was not atomic, so go back and split it.

**4. The extraction prompt**, already saved in `catalog/prompts/`. Collect the filled-in versions into `catalog/appendix-prompts.md` for the paper appendix, with a one-line note of the model and date used per source, because reproducibility claims need both.

### Document formats

Alongside the markdown and CSV, produce a Word version of the catalog when the user wants something to circulate or to drop into a journal template. Build it from the finished markdown rather than composing it separately, so the two cannot drift. If a `docx` skill is installed in this environment, read its SKILL.md before building the file. If not, produce the closest equivalent available (an .rtf, an HTML file that Word opens cleanly, or plain markdown with a note on how to convert it) and tell the user which fallback was used.

## Resuming a catalog in progress

These projects span sessions. On re-entry, read `catalog/00-scope.md` and `catalog/03-verification-log.csv`, report where things stand (sources done, candidates pending verification, requirements confirmed), and pick up from the first incomplete phase rather than starting over.

## Reference files

- `references/srs-structure.md`: the IEEE 29148 SRS section layout and how to map quality characteristics onto it. Read before phase 5.
- `references/extraction-prompt.md`: the exact extraction prompts to use and to publish, normative and instrument variants. Read before phase 2, and pick the variant that matches each source's type.
- `references/validation-rules.md`: keep / rewrite / reject criteria and the IEEE 29148 requirement quality attributes. Read before phase 3, and use it when proposing rewrites.
- `assets/catalog-table.csv` and `assets/extraction-log.csv`: header templates for the two output tables.
