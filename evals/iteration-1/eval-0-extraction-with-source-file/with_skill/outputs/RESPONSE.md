I've run phases 0 to 2 and stopped at the verification gate, which is where you have to
take over. Everything is in `catalog/`:

- `catalog/00-scope.md` — draft scope, inclusions/exclusions, category codes **(needs your confirmation)**
- `catalog/01-sources.md` — source register with a coverage note
- `catalog/prompts/extraction-NSAIDH104.md` — the extraction prompt as filled in, for your appendix
- `catalog/02-candidates-NSAIDH104.csv` — **18 candidate requirements**
- `catalog/03-verification-log.csv` — seeded with all 18 rows at `verdict = PENDING`

No catalog, extraction log or audit checklist yet. Those are built from verified
requirements only, and nothing is verified yet.

---

## First, the phase 0 questions I'd normally have stopped to ask

I went ahead on assumptions rather than leaving you with nothing, but these are real
questions and the answers change the output. Everything I assumed is marked
**[ASSUMPTION]** in `00-scope.md`.

1. **Scope wording.** I drafted: *"mobile applications intended for use by adults to
   self-manage their mental wellbeing, including apps that support self-monitoring,
   self-directed therapeutic content, and behavioural self-management, delivered
   directly to the user on a consumer mobile device."* Does "mental wellbeing" include
   diagnosed anxiety and depression for you, or only sub-clinical wellbeing? This
   sentence is what justifies every later "out of scope" rejection, so it's worth
   getting exact.
2. **Security.** You listed privacy but not security. Clause 5.3.1 (transport
   encryption) is really a security obligation. I filed it under `PRIV` for now — do
   you want a fifth characteristic `SEC`, or is privacy meant as the umbrella?
3. **Operator vs software obligations.** Clause 6.2.2 ("content more than 36 months
   past review shall be withdrawn or re-reviewed") arguably obliges the publisher, not
   the app. I've assumed **software behaviour only** and excluded operator duties. If
   you want operator obligations in, say so now — it's a scope decision, not something
   to settle candidate by candidate.
4. **Citation.** Please confirm publisher, date and exact title for the reference list.
5. **Other sources.** One source is thin for a catalog paper. Which others are you
   planning, and do you have full text for each?

## Assumed category codes

`PRIV` privacy · `SAFE` safety · `ACC` accessibility · `PERS` personalisation.
These become the ID prefixes and they're permanent once assigned, so flag now if you'd
rather have different ones.

## What came out of the source

An important limitation first: the file is labelled *"excerpt: Clauses 5 to 7"*. I
extracted from clauses 5, 6, 7 and nothing else. I did **not** fill in clauses 1–4 or
anything after 7 from memory of the standard. This source is recorded as **partly
extracted**, and that belongs in your methods section — "we extracted from NSAI/DH-104"
and "we extracted from clauses 5–7 of NSAI/DH-104" are different claims about coverage.

18 candidates: 5 `PRIV`, 7 `SAFE`, 2 `ACC`, 4 `PERS`. Four of them are splits of
clauses that carried two obligations each (6.2.1, 7.2.1, 7.3.1), since one requirement
means one obligation. Three are flagged **borderline** in the rationale field — 003,
011 and 016 — and those are the ones I'd look at hardest.

Three things in the source I deliberately did **not** turn into requirements: the
5.2.2 NOTE about PDF exports (informative — but it's the best audit question for the
export requirement), the 5.1.3 permission to keep aggregate statistics (a permission,
not an obligation), and definition 3.4 (belongs in SRS section 1.4).

---

## Phase 3: your turn, and the rule

**Verification means opening NSAI/DH-104 and looking at the clause — not judging
whether the requirement sounds sensible.** A requirement can read perfectly and hang
off a clause that doesn't exist or doesn't say that. That is the failure mode that gets
catalog papers retracted, and it's the only reason this pipeline has a gate in it.

For each candidate, one of:

- **KEEP** — clause exists, says what's quoted, requirement is a fair rendering
- **REWRITE** — clause checks out, wording needs changing (give me the wording, or ask me to propose one)
- **REJECT** — clause doesn't exist, doesn't say that, or the requirement fails a form rule

Anything you wave through without opening the source gets logged as
`verified = not confirmed`, and the catalog will carry a note naming the affected
source. That's not a threat, it's just what an honest record looks like — but I'd
rather you didn't need it. Expect roughly 20–40 candidates an hour when you're actually
checking clauses; 18 is one sitting.

You can also add your own requirements at any point. Those go into the log as
`verdict = author` and carry origin tag `H`.

### Batch 1 of 2 — candidates 001 to 012

| # | Clause | Source says | Proposed requirement | Cat |
|---|---|---|---|---|
| 001 | 5.1.1 | "A digital health application shall retain personally identifiable user-entered wellbeing records for no longer than 24 months after the user's last active session, unless the user has explicitly opted in to longer retention." | The app shall retain personally identifiable user-entered wellbeing records for no longer than 24 months after the user's last active session, unless the user has explicitly opted in to longer retention. | PRIV |
| 002 | 5.1.2 | "Where a user requests deletion of their account, the application shall erase all personally identifiable wellbeing records within 30 days of the request." | The app shall erase all personally identifiable wellbeing records within 30 days of a user's request to delete their account. | PRIV |
| 003 | 5.1.3 | "Aggregate statistics derived from user records may be retained indefinitely provided they cannot be re-identified." | The app shall ensure that any aggregate statistics derived from user records that it retains indefinitely cannot be re-identified. | PRIV |
| 004 | 5.2.1 | "The application shall enable the user to export their complete wellbeing record in a structured, commonly used, machine-readable format." | The app shall enable the user to export their complete wellbeing record in a structured, commonly used, machine-readable format. | PRIV |
| 005 | 5.3.1 | "All personally identifiable data transmitted between the application and any remote service shall be protected in transit using a current, non-deprecated transport encryption protocol." | The app shall protect all personally identifiable data transmitted between the app and any remote service in transit using a current, non-deprecated transport encryption protocol. | PRIV |
| 006 | 6.1.1 | "Where an application collects free-text entries from the user, it shall provide the user with a persistently reachable route to crisis support information from any screen on which free-text entry is possible." | The app shall provide a persistently reachable route to crisis support information from any screen on which free-text entry is possible. | SAFE |
| 007 | 6.1.2 | "The application shall not present the user with an automated assessment of suicide risk." | The app shall not present the user with an automated assessment of suicide risk. | SAFE |
| 008 | 6.1.3 | "The application shall display, on first use, a statement that it is not a substitute for professional care." | The app shall display, on first use, a statement that it is not a substitute for professional care. | SAFE |
| 009 | 6.2.1 | "Any therapeutic content presented to the user shall carry an identifiable source and a date of last clinical review." | The app shall present an identifiable source with any therapeutic content shown to the user. | SAFE |
| 010 | 6.2.1 | (same clause, second obligation) | The app shall present a date of last clinical review with any therapeutic content shown to the user. | SAFE |
| 011 | 6.2.2 | "Therapeutic content whose last clinical review is more than 36 months old shall be withdrawn or re-reviewed." | The app shall not present therapeutic content whose last clinical review is more than 36 months old. | SAFE |
| 012 | 7.1.1 | "The application shall conform to WCAG 2.1 Level AA." | The app shall conform to WCAG 2.1 Level AA. | ACC |

**Three I want you to look at particularly hard:**

- **003** — the clause is a *permission*, not an obligation. I inverted it into its
  proviso. That's exactly the kind of plausible strengthening the method warns about.
  If you think it over-reaches, reject it.
- **011** — the clause says "withdrawn **or** re-reviewed"; I rendered only the
  in-product outcome. It may also be an operator obligation rather than a software one
  (see scope question 3).
- **005** — filed under `PRIV`, but it's a security clause. Category question, not a
  citation question.

Reply with verdicts however suits you — "001 KEEP, 002 KEEP, 003 REJECT clause does not
support, ..." is fine. Then I'll send batch 2 (013–018: text resizing, notifications,
adaptation disclosure).

Once all 18 are verified I'll do origin tagging, assign permanent IDs, lay the catalog
out in the IEEE 29148 structure, and produce the four outputs — catalog tables,
extraction log with retention rates, audit checklist, and the prompt appendix.
