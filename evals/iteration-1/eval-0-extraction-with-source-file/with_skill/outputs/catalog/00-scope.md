# 00 — Scope

**Status: DRAFT — not confirmed by the author.**
The scope sentence, the inclusions/exclusions and the category codes below were
drafted by the assistant from a one-line brief and have **not** been confirmed.
Phase 0 of the method requires explicit author confirmation of this wording,
because this sentence is what justifies every later rejection for "out of scope".
Everything marked **[ASSUMPTION]** needs a yes/no from the author before the
catalog is built.

---

## 1. Domain

### Scope sentence (draft)

> This catalog specifies requirements for **mobile applications intended for use by
> adults to self-manage their mental wellbeing**, including apps that support
> self-monitoring, self-directed therapeutic content, and behavioural
> self-management, delivered directly to the user on a consumer mobile device.

### In scope **[ASSUMPTION]**

- Native and hybrid mobile applications on consumer smartphones and tablets.
- Adult users (18+) acting on their own behalf, without a clinician in the loop.
- Self-monitoring of mood, symptoms, activity and free-text journalling.
- Self-directed therapeutic or psychoeducational content delivered in-app.
- Data the app holds about the user, including its retention, export and transmission.
- Behaviour of the app towards the user: notifications, adaptation, crisis signposting.

### Out of scope **[ASSUMPTION]**

- Apps intended for children or adolescents.
- Clinician-facing tools, care-team dashboards, and remote monitoring products whose
  primary user is a professional.
- Regulated medical devices making a diagnostic or treatment claim (a separate
  regulatory regime with its own requirements set).
- Desktop and web-only products.
- Obligations that fall on the *operator or organisation* rather than on the
  *software* (e.g. staffing a clinical review board). **[ASSUMPTION — see Q3 below]**
- Crisis-line and emergency-service integration beyond signposting.

## 2. Sources

One source supplied, full text available. See `01-sources.md`.

## 3. Quality characteristics and category codes

Chosen by the author: privacy, safety, accessibility, personalisation.
Category codes drafted by the assistant **[ASSUMPTION]**:

| Characteristic | Code | Usual SRS home (per `references/srs-structure.md`) |
|---|---|---|
| Privacy (incl. data retention, deletion, portability, transmission) | `PRIV` | 3.7 security, with retention/deletion in 3.5 |
| Safety (clinical safety, crisis handling, content provenance) | `SAFE` | 3.7, declared as domain-specific in 1.4 |
| Accessibility | `ACC` | 3.3 usability |
| Personalisation | `PERS` | 3.2 functions |

**Deliberately not covered** (to be stated in SRS 1.3.4 so it reads as a decision,
not an oversight): performance efficiency, interoperability, sustainability,
maintainability, reliability.

## 4. Open questions for the author (phase 0 is not closed until these are answered)

1. **Scope wording.** Is the scope sentence above right, and are the inclusion and
   exclusion lists complete? In particular: does "mental wellbeing" include
   diagnosed anxiety and depression, or only sub-clinical wellbeing?
2. **Security as a separate characteristic.** NSAI/DH-104 clause 5.3.1 (transport
   encryption) is a *security* obligation, not strictly a privacy one. It is
   currently filed under `PRIV`. Do you want a fifth characteristic `SEC`, or is
   privacy-as-umbrella the intent?
3. **Operator obligations.** Some clauses (e.g. 6.2.2, withdrawing stale content)
   arguably oblige the publisher rather than the software. Should the catalog carry
   operator obligations, or software behaviour only? This is a phase 0 decision, not
   a per-candidate judgement call.
4. **Full citation.** The supplied text is an excerpt (clauses 5–7 plus one
   definition) of NSAI/DH-104:2024 Part 2. Please confirm the exact publisher,
   publication date and title wording for the reference list, and confirm that
   clauses 1–4 and 8+ contain no further product requirements — otherwise the
   catalog must record this source as *partly extracted*.
5. **Further sources.** A single-source catalog is thin for publication. Which other
   sources do you intend to include (GDPR? WCAG 2.1 itself? NICE guidance? ISO/IEC
   25010? WHO guidance?), and do you have the full text of each?
