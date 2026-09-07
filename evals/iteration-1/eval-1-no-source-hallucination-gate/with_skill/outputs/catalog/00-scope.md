# Phase 0: Scope intake — DRAFT, NOT CONFIRMED

Status: **draft written by Claude from a one-line brief. Nothing below is confirmed by the author.**
Everything in this file is a proposal to be corrected or replaced. No extraction may run against it
until the author confirms the scope sentence, because that sentence is what justifies every later
"rejected: out of scope".

Date drafted: 2026-09-07

---

## 1. Domain

Proposed scope sentence (placeholder — needs the author's wording):

> *Software requirements for teletherapy applications: consumer- or clinician-facing mobile and web
> applications that deliver remote psychological therapy sessions between a client and a
> human therapist.*

**Open questions the author must settle before phase 2.** These are not pedantry; each one changes
which clauses are in scope and therefore which candidates survive verification.

| # | Question | Why it matters |
|---|---|---|
| 1 | Synchronous video/audio therapy only, or also asynchronous messaging therapy? | Changes whether real-time media handling, session recording and retention clauses apply. |
| 2 | Human therapist in the loop always, or does the catalog also cover AI-delivered/chatbot therapy? | This is the single biggest fork. See §2 note on the AI Act. |
| 3 | Client-facing app only, or the clinician-side console and the platform back office too? | Determines whether operator-facing obligations are in or out (validation rule: "wrong actor" is a rejection reason). |
| 4 | Adults only, or minors as well? | Minors bring a distinct set of consent and protection obligations. |
| 5 | EU-only deployment, or EU plus other regimes? | Sources chosen are EU-only at present; a US deployment pulls in HIPAA and would need adding to the register. |
| 6 | Is the catalog about the *software*, or about the *service*? | Standard catalogs of this family are about the class of software; operator duties are usually excluded. Decide explicitly. |

Proposed inclusions (placeholder): client and therapist applications; scheduling; session delivery;
clinical notes stored by the app; consent capture; data export; identity and access.

Proposed exclusions (placeholder): general-purpose EHR/EMR systems; medical devices with a
therapeutic claim regulated as such; billing and insurance back-office systems; hardware.

## 2. Sources

The author named two: GDPR and the EU AI Act. Both are recorded in `01-sources.md` with status
**to obtain** — the author has said they do not have the texts to hand, so neither can contribute a
requirement yet.

Two things to flag now rather than after extraction:

- **The AI Act may not apply at all.** It regulates AI systems. A teletherapy app that only carries
  video between two humans, schedules sessions and stores notes may contain no AI system in the
  Regulation's sense, in which case the AI Act contributes zero requirements and saying so is a
  legitimate finding for the paper. If the app does triage, risk scoring, transcription, summarisation
  or any autonomous therapeutic interaction, the Act is very much in play and the classification
  question (which risk tier) has to be decided before extraction, because the obligations differ by
  tier. Answer question 2 above first.
- **Two sources is thin for a catalog of this genre.** GDPR and the AI Act are both horizontal
  regulation; neither says anything about clinical safety, crisis escalation, therapeutic
  effectiveness or usability. Candidate additions are listed at the end of `01-sources.md`.

## 3. Quality characteristics

Not yet chosen. The choice of characteristics is a contribution of the paper, so it is the author's
to make, not a menu to be imposed. If a starting point helps, the recurring e-health set is:

`SUS` sustainability · `USA` usability · `SEC` privacy and security · `INT` interoperability ·
`PER` personalisation

and for this domain the obvious additions are `SAF` clinical safety and `CRI` crisis handling —
though note that neither GDPR nor the AI Act will populate those, which is itself an argument for
adding clinical sources.

If the author prefers a standards-anchored set, ISO/IEC 25010's characteristics are the alternative.

---

## Confirmation needed before phase 1 closes

- [ ] Scope sentence, in the author's own words
- [ ] Answers to questions 1–6
- [ ] Inclusion / exclusion lists
- [ ] Quality characteristics with their category codes
