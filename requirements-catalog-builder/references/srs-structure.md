# IEEE 29148 SRS structure for a requirements catalog

ISO/IEC/IEEE 29148 gives the section layout for a Software Requirements Specification. A requirements catalog is not a specification for one product, so the structure is adapted rather than copied blindly: the catalog describes a class of software, and the sections that assume a single system under development are either generalised or dropped with a note saying why.

Use the outline below. Keep the numbering, since reviewers of catalog papers recognise it, and an unfamiliar structure invites the question "why did you not follow the standard".

## Outline

**1. Introduction**

- 1.1 Purpose. What the catalog is for and who should use it.
- 1.2 Scope. The scope sentence from phase 0, with inclusions and exclusions. This is what every "out of scope" rejection points back to.
- 1.3 Product overview. Generalised for a catalog: describe the class of software, its typical users, its operating context, and its relationship to adjacent systems (clinical records, wearables, app stores, payment providers).
  - 1.3.1 Product perspective
  - 1.3.2 Product functions
  - 1.3.3 User characteristics
  - 1.3.4 Limitations
- 1.4 Definitions. Domain terms, and the origin tags (H, AI-K, AI-R) with their meanings.

**2. References**

The source register from phase 1, as full citations, with the short codes used in the requirement tables.

**3. Specific requirements**

This is where the requirement tables live. Only the subsections that carry requirements appear; an empty subsection is dropped and noted in 1.3.4 rather than left as a heading with "None".

- 3.1 External interfaces. User interfaces, hardware interfaces, software interfaces, communication interfaces.
- 3.2 Functions. The functional requirements, grouped by functional area.
- 3.3 Usability requirements.
- 3.4 Performance requirements.
- 3.5 Logical database requirements. Data the class of software must hold, retain, and delete.
- 3.6 Design constraints. Including standards compliance and regulatory constraints that constrain the design rather than stating a behaviour.
- 3.7 Software system attributes. Reliability, availability, security, maintainability, portability, and any domain-specific quality characteristic that has no other home.
- 3.8 Supporting information.

**4. Verification**

How conformance to each requirement is checked. For a catalog this is where the audit checklist is introduced and cross-referenced: each checklist question is the verification method for its requirement.

**5. Appendices**

- A. Assumptions and dependencies.
- B. Acronyms and abbreviations.
- C. Extraction log.
- D. Extraction prompts, with model and date.

## Mapping quality characteristics onto the structure

The user chooses the quality characteristics in phase 0, and they rarely line up one-to-one with the standard's sections. Map rather than restructure:

| Characteristic | Usual home |
|---|---|
| Usability, accessibility, learnability | 3.3 |
| Performance efficiency, responsiveness | 3.4 |
| Privacy, security, confidentiality | 3.7 (security), with data retention in 3.5 |
| Interoperability, portability | 3.1 (interfaces), 3.7 (portability) |
| Reliability, availability, fault tolerance | 3.7 |
| Maintainability, modifiability | 3.7 |
| Sustainability | 3.7, with an explanatory note in 1.3.4 |
| Personalisation, adaptivity | 3.2 |
| Domain-specific (clinical safety, crisis handling, safeguarding) | 3.7, declared in 1.4 |

Say in 1.3 which characteristics were covered and which were deliberately left out. A catalog that quietly omits security reads as an oversight; one that states "security requirements were out of scope and are addressed in [prior catalog]" reads as a decision.

## Category codes

Category codes in requirement IDs come from the characteristics, not from the section numbers, because sections move between drafts and IDs must not. Three or four letters, uppercase, stable for the life of the catalog. Record the code alongside each characteristic in 1.4 so a reader can decode an ID without hunting.

Examples: `USA` usability, `SEC` security, `PRIV` privacy, `PERF` performance, `INTEROP` interoperability, `REL` reliability, `PERS` personalisation, `SUST` sustainability, `FUNC` general functional, `SAFE` clinical safety.
