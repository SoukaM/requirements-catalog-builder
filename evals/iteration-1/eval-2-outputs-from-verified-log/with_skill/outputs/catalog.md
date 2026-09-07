# A requirements catalog for privacy, security and accessibility in mental wellbeing apps

Structured as an ISO/IEC/IEEE 29148 Software Requirements Specification, adapted for a catalog that describes a class of software rather than one product.

Built from `partial-verification-log.csv` (15 AI-proposed candidates across 3 sources, each verdict recorded against the source clause, plus 2 author-added requirements). Every citation in this catalog is marked `verified = confirmed` in that log.

> **Two things in this document are drafts awaiting the author's confirmation, and are flagged in place:**
> 1. The scope statement in 1.2 was written from the one-line domain description ("privacy, security and accessibility requirements for mental wellbeing apps"). Phase 0 of the method requires the author to fix this wording, because it is what every out-of-scope rejection points back at — and one rejection in this catalog (SEC-SRC-003) already rests on it.
> 2. The source editions in section 2 were inferred from the clause numbering used in the verification log. They must be checked against the documents actually consulted.

---

## 1. Introduction

### 1.1 Purpose

This catalog is a reusable, traceable set of requirements for the privacy, security and accessibility of mental wellbeing applications. It is not a specification for one product. It is intended for three uses: as a starting requirements set for teams building an app in this class; as an evaluation instrument for assessing an existing app (see section 4 and the accompanying audit checklist); and as a published research artefact, in which case the extraction log in Appendix C reports how the catalog was produced.

### 1.2 Scope

*Draft wording — to be confirmed by the author before publication.*

**Scope sentence.** This catalog covers the privacy, security and accessibility requirements that apply to consumer mobile and web applications intended to support the mental wellbeing of adult users, including symptom and mood self-monitoring, psychoeducation, guided self-help exercises and journalling.

**Inclusions**

- Obligations that fall on the software product itself: what the app must do, show, store, delete or permit.
- Personal data handling by the app, including collection, on-device storage, transmission, retention and erasure.
- Authentication and credential handling exposed to the end user.
- Accessibility of the user interface.
- Apps distributed direct to consumers, whether or not a clinician is involved.

**Exclusions**

- Obligations that fall on the operator or the organisation rather than the software (staff training, appointment of a data protection officer, breach notification to a supervisory authority, records of processing).
- Server-side and infrastructure controls with no user-visible or product-level manifestation.
- Clinical safety, crisis handling and safeguarding requirements. These are a distinct characteristic and are not covered by this version of the catalog. The omission is a decision, not an oversight; for an app in this domain it is the most obvious gap, and it is discussed in 1.3.4.
- Regulatory classification questions (whether a given app is a medical device).
- Apps for children and adolescents, whose consent and safeguarding regimes differ.

**Note on a rejection that depends on this wording.** Candidate SEC-SRC-004 was rejected as `out of scope` on the strength of a scope statement that the author held but that was not written down before extraction. If the confirmed scope sentence differs from the draft above, that rejection should be revisited.

### 1.3 Product overview

#### 1.3.1 Product perspective

Applications in this class run on a user's personal device and typically operate both offline and against a vendor cloud service. They commonly sit alongside: the platform's own health data store, wearables and sensors, app store distribution and payment channels, analytics and crash-reporting SDKs, and — for some products — a clinician-facing portal. The catalog assumes the app is the system under specification and the surrounding services are external interfaces.

#### 1.3.2 Product functions

Typical functions of the class: mood, symptom and habit self-monitoring; journalling and free-text entry; guided exercises and psychoeducational content; reminders and notifications; progress visualisation; optional account creation, backup and cross-device sync; optional data sharing with a clinician or a supporter.

#### 1.3.3 User characteristics

Adult users, self-selected, using the app during periods of low mood, anxiety or distress. Two characteristics shape the requirements more than technical proficiency does: users are asked to disclose unusually sensitive information about their mental state, and their capacity to attend to consent dialogues, privacy notices and complex interface flows varies with their condition. The catalog assumes a general adult population, including users of assistive technology and users with fluctuating attention, literacy and motor control.

#### 1.3.4 Limitations

- **Coverage is limited to three sources.** GDPR, NIST SP 800-63B and WCAG 2.2 were the sources verified. The catalog therefore covers data protection, password-based authentication and web accessibility well, and covers other security controls (transport security, session management, key management, secure update) and all clinical dimensions not at all.
- **Clinical safety and crisis handling are absent by decision**, as stated in 1.2. In this domain that is a substantive gap: an app that satisfies every requirement here may still handle a user in crisis badly.
- **Three SRS subsections carry no requirements** and are omitted rather than left empty: 3.1 external interfaces, 3.4 performance, 3.6 design constraints, and 3.8 supporting information. None of the three sources yielded a verified requirement in those areas. This is a property of the source set, not evidence that the class of software has no such requirements.
- **Two requirements (PRIV-05, PRIV-06) have no source clause.** They come from the author's prior fieldwork. They are marked `H` and carry no citation, and a reader assessing the catalog's evidential basis should treat them differently from the ten clause-anchored requirements.
- **Small catalog.** Twelve requirements is a first pass, not a saturated catalog. Adding sources is the obvious next step.

### 1.4 Definitions

**Origin tags.** Every requirement carries exactly one, recording how much of the catalog the model produced and how much survived contact with the sources.

| Tag | Meaning | Count in this catalog |
|---|---|---|
| `H` | The author wrote it. The model did not propose it. | 2 |
| `AI-K` | The model proposed it and the author kept it unchanged. | 6 |
| `AI-R` | The model proposed it and the author rewrote it. A cosmetic fix still counts as a rewrite, because the question the tag answers is whether the model's wording stood unchanged. | 4 |

**Category codes.** Used in requirement IDs. IDs are permanent: a retired requirement's ID is not reused.

| Code | Quality characteristic |
|---|---|
| `PRIV` | Privacy and data protection |
| `SEC` | Security (authentication and credential handling) |
| `USA` | Accessibility and usability |

**Domain terms.**

- *Mental wellbeing app*: a consumer application whose stated purpose is to support the user's mental health or wellbeing, whether or not it makes a clinical claim.
- *Self-monitoring feature*: any feature by which the user records their own state over time (mood log, symptom tracker, journal, habit tracker).
- *Personal data*, *processing*, *controller*: as defined in GDPR Art. 4.
- *Leaves the device*: any transmission of user-entered or user-derived data off the device, including to the vendor's own servers, analytics services and backup services.

---

## 2. References

*Editions inferred from the clause numbering in the verification log — confirm against the documents actually consulted.*

| Code | Full citation | Status |
|---|---|---|
| `GDPR` | Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data (General Data Protection Regulation). OJ L 119, 4.5.2016, pp. 1–88. | Full text available; verified |
| `NIST-SP-800-63B` | Grassi, P. A., Fenton, J. L., et al. *Digital Identity Guidelines: Authentication and Lifecycle Management.* NIST Special Publication 800-63B. National Institute of Standards and Technology, June 2017 (includes updates as of 2017-12-01). | Full text available; verified. **Revision to confirm:** clause 5.1.1.2 is the Revision 3 locator for memorised secret verifiers. Revision 4 renumbers this material, so the catalog must state which revision was read. |
| `WCAG-2.2` | *Web Content Accessibility Guidelines (WCAG) 2.2.* W3C Recommendation, 5 October 2023. World Wide Web Consortium. | Full text available; verified. **Date to confirm:** WCAG 2.2 has had editorial republications since the original Recommendation; cite the version consulted. |
| — | Author's prior fieldwork (unpublished). Basis for PRIV-05 and PRIV-06. | Not a citable source; see 1.3.4 |

---

## 3. Specific requirements

Subsections 3.1, 3.4, 3.6 and 3.8 carry no requirements from the current source set and are omitted; see 1.3.4.

### 3.2 Functions

| ID | Requirement | Source (with clause) | Origin |
|---|---|---|---|
| PRIV-01 | The app shall enable the user to receive their personal data in a structured, commonly used and machine-readable format. | GDPR, Art. 20(1) | AI-K |
| PRIV-05 | The app shall allow a user to use all self-monitoring features without creating an account. | Author (prior fieldwork); no source clause | H |
| PRIV-06 | The app shall present a plain-language summary of what data leave the device, before first data transmission. | Author (prior fieldwork); no source clause | H |

### 3.3 Usability requirements

Accessibility requirements are placed here, following the standard's mapping of usability and accessibility onto a single section.

| ID | Requirement | Source (with clause) | Origin |
|---|---|---|---|
| USA-01 | The app shall support resizing of text up to 200 percent without loss of content or functionality. | WCAG 2.2, SC 1.4.4 | AI-K |
| USA-02 | The app shall render a visible focus indicator for any keyboard-operable user interface component. | WCAG 2.2, SC 2.4.7 | AI-K |
| USA-03 | The app shall provide a text alternative for each non-text content element. | WCAG 2.2, SC 1.1.1 | AI-R |

### 3.5 Logical database requirements

Data the class of software must hold, retain and delete.

| ID | Requirement | Source (with clause) | Origin |
|---|---|---|---|
| PRIV-02 | The app shall erase the user's personal data on request where the data are no longer necessary for the purpose for which they were collected. | GDPR, Art. 17(1)(a) | AI-R |
| PRIV-03 | The app shall by default process only the personal data necessary for each specific purpose. | GDPR, Art. 25(2) | AI-K |

### 3.7 Software system attributes

Security, and the confidentiality of data at rest.

| ID | Requirement | Source (with clause) | Origin |
|---|---|---|---|
| PRIV-04 | The app shall encrypt personal data at rest on the user's device. | GDPR, Art. 32(1)(a) | AI-R |
| SEC-01 | The app shall permit passwords of at least 64 characters in length. | NIST SP 800-63B, clause 5.1.1.2 | AI-K |
| SEC-02 | The app shall verify prospective passwords against a list of commonly used or compromised values. | NIST SP 800-63B, clause 5.1.1.2 | AI-K |
| SEC-03 | The app shall not require periodic password rotation in the absence of evidence of compromise. | NIST SP 800-63B, clause 5.1.1.2 | AI-R |

**A category decision to review.** PRIV-04 keeps the `PRIV` code because the extraction categorised it as privacy and its source clause is a data-protection provision, but its content is a security control and it sits in the security subsection. If you would rather it read `SEC-04`, change it now: IDs are permanent once the catalog is circulated or cited.

---

## 4. Verification

Conformance to each requirement is checked by the corresponding question in the audit checklist (`audit-checklist.md`, `audit-checklist.csv`). The checklist carries one question per requirement, keyed by requirement ID, with the answer domain Yes / No / Partially / N/A. A "No" answer traces back through the ID to the requirement and from there to its source clause, so an audit finding can be stated as a departure from a named authority rather than as an opinion.

The checklist is the verification method for this catalog. It is not a scoring instrument: no weighting or total is defined, because the sources give no basis for one.

---

## 5. Appendices

### Appendix A. Assumptions and dependencies

1. The verification log is the complete record of candidates proposed. The extraction log's "candidates proposed" counts are the number of rows per source in that log. If any candidate was discarded before it reached the log, the retention rates below are overstated.
2. Every row in the log is marked `verified = confirmed`, i.e. the author reports having opened each source and checked each clause. No source in this catalog carries unconfirmed citations.
3. The two author requirements were verified as sound requirements, not as citations; they have no clause to check.
4. Requirement text is reproduced verbatim from the `final_text` column of the verification log. Nothing was reworded during catalog assembly.

### Appendix B. Acronyms and abbreviations

| | |
|---|---|
| GDPR | General Data Protection Regulation |
| NIST | National Institute of Standards and Technology |
| SC | Success Criterion (WCAG) |
| SRS | Software Requirements Specification |
| WCAG | Web Content Accessibility Guidelines |
| AI-K / AI-R / H | Origin tags; see 1.4 |

### Appendix C. Extraction log

| Source | Candidates proposed | Kept | Rewritten | Rejected | Retention rate |
|---|---|---|---|---|---|
| GDPR | 6 | 2 | 2 | 2 | 66.7% |
| NIST-SP-800-63B | 5 | 2 | 1 | 2 | 60.0% |
| WCAG-2.2 | 4 | 2 | 1 | 1 | 75.0% |
| **TOTAL** | **15** | **6** | **4** | **5** | **66.7%** |
| Author-added (outside AI extraction) | n/a | n/a | n/a | n/a | 2 requirements |

Retention rate is (kept + rewritten) / proposed.

**Rejections by reason**

| Reason | Count | Candidates |
|---|---|---|
| `clause not found` | 2 | PRIV-SRC-004 (GDPR Art. 33(9)), USA-SRC-003 (WCAG SC 3.3.9) |
| `clause does not support` | 1 | SEC-SRC-004 (NIST 4.3.1) |
| `not a requirement` | 1 | PRIV-SRC-005 (GDPR Art. 5(1)(b)) |
| `out of scope` | 1 | SEC-SRC-003 (NIST 5.2.2) |

**Citation failure rate: 3 of 15 candidates (20.0%)** — the combined `clause not found` and `clause does not support` count. This is the number a methods-minded reviewer will want, because it measures directly how often the model fabricated or misread a citation.

#### Interpretation

Two-thirds of proposed candidates survived verification, and the rate is stable across the three sources — 60% to 75% on 4 to 6 candidates each, which is well inside what those sample sizes can distinguish. The honest reading is that retention did not vary meaningfully by source type here, and the catalog is too small to claim it does. Do not write a sentence contrasting the sources; the numbers will not carry it.

The result that does carry is the citation failure rate. One candidate in five pointed at a clause that either does not exist or does not say what the requirement claimed — one in a regulation, one in a standard, one in a guideline, so the failure is not confined to any one kind of source. Both `clause not found` rejections are the dangerous kind: GDPR Art. 33 has five paragraphs and a citation to Art. 33(9) is an invention, yet the requirement attached to it would have read plausibly to any reviewer who did not open the regulation. That is the argument for the verification gate, and it is the finding worth foregrounding in the results section.

Of the ten surviving requirements, the author changed the wording of four (40%). The three rewrite notes say what was wrong: an invented deadline ("immediately" where the source gives none), a bundled obligation (encryption at rest and in transit in one sentence), a weakened modality ("should" for a "shall"), and a compound requirement. These are the model's characteristic errors in this run — strengthening, bundling and softening — and they are worth reporting alongside the citation failures, because they are the errors that survive a citation check and are caught only by reading the requirement against the clause.

A caution for the write-up: 15 candidates from 3 sources is a pilot. Report the counts as counts, give the percentages one decimal place because that is the convention, and resist the temptation to present 66.7% as a precision estimate of anything.

### Appendix D. Extraction prompts

The filled-in extraction prompts are in `appendix-prompts.md`. **The model identifier and the extraction date per source are missing and only you can supply them** — a reproducibility claim needs both, and so does the statement of whether the full source or only selected sections were given to the model.
