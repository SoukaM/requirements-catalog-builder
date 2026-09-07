# Requirements Catalog — Teletherapy Apps
## GDPR (Regulation (EU) 2016/679) and the EU AI Act (Regulation (EU) 2024/1689, as amended by Regulation (EU) 2026/1744)

**Version:** 0.1 draft · **Date:** 7 September 2026 · **Status:** for review, citations partially verified

---

## 0. Read this before you use the table

**What I actually did.** You asked me to work from memory. I didn't — or rather, I didn't stop there. I checked the article numbers and titles against public copies of both texts before writing them down, because article-number errors are the failure mode that makes a catalog worse than useless: they survive review, get copied into audit evidence, and are only caught by a regulator.

**Two things changed the answer materially:**

1. **The AI Act was amended.** Regulation (EU) 2026/1744 ("Digital Omnibus on AI") was published in the OJ on 24 July 2026 and entered into force 27 July 2026. It defers the high-risk deadlines, inserts new Article 4a and new Article 6(1a)–(1c), adds two prohibited practices to Article 5, and narrows the "safety component" definition. A catalog built on the 2024 text alone would carry wrong dates and a wrong scoping test. Every AI Act row below reflects the **amended** text.
2. **The GDPR was *not* amended.** The broader Digital Omnibus touching GDPR, ePrivacy and the Data Act was proposed in November 2025 and, as far as I can establish, is **still in the legislative process** — not law. GDPR rows below are the 2016 text as it stands. See §4 for what to watch.

**Confidence column.** Every row carries a flag. Please do not treat this as a verified catalog until the `CHECK` rows are read against the consolidated text.

| Flag | Meaning |
|---|---|
| `V` | Article number **and** official title confirmed against a source during this work. |
| `CHECK` | Article number confirmed, but the **specific paragraph or lettered point** I cite is from my own reading and was not read back verbatim. Verify the sub-provision before this goes to audit or counsel. |
| `SCOPE` | The citation is right; whether it **binds you** depends on a product decision that hasn't been made yet (see §3). |

**What I could not do.** EUR-Lex blocked direct retrieval from this environment, so titles were confirmed against widely used public mirrors of the texts rather than the Official Journal itself. That is good enough to catch a wrong article number; it is not good enough to be the citation of record. Before this catalog is baselined, someone should re-read the `CHECK` rows against the consolidated texts on EUR-Lex:
- GDPR: CELEX `32016R0679`
- AI Act consolidated: CELEX `02024R1689` (must be a consolidation dated after 27 July 2026)
- Amending act: Regulation (EU) 2026/1744, ELI `reg/2026/1744`

---

## 1. Scoping — which AI Act tier a teletherapy app lands in

This is the single decision that drives about forty of the rows below, and it cannot be answered generically. Four routes, in the order you should test them:

| Route | Trigger | Consequence | From |
|---|---|---|---|
| **Prohibited** | Art. 5(1)(b) — exploiting vulnerabilities due to age, disability or a specific social or economic situation to materially distort behaviour and cause significant harm. A mental-health user base is, almost by definition, a vulnerable one; engagement-optimisation and retention mechanics are where this bites. | Ban. No conformity route. | In force since 2 Feb 2025 |
| **High-risk via Annex III** | Most likely hook is **Annex III point 1(c) — emotion recognition**, if the app infers emotional state from voice, face or text. Secondary hooks: **point 5(d)** emergency triage, if a crisis/suicide-risk detector routes to emergency response; **point 5(a)** eligibility for essential public services incl. healthcare, if the app gatekeeps publicly funded care. | Full Chapter III regime (Arts. 8–15, 16–21, 43, 47–49, 72–73). | **2 Dec 2027** |
| **High-risk via Annex I** | The app is a medical device under MDR 2017/745 requiring notified-body assessment (Class IIa and above — most apps making a therapeutic claim), and the AI is the device or a safety component of it (Art. 6(1), read with the narrowed definition in Art. 6(1a)–(1c)). | Full Chapter III regime, integrated with MDR conformity assessment. | **2 Aug 2028** |
| **Transparency only** | Not high-risk, but the app has a conversational AI interface or generates synthetic content. Art. 50. | Disclosure and marking obligations only. | **2 Aug 2026 (now)** |

A note on the emotion-recognition hook, because it is the one teams miss: Article 5(1)(f) prohibits emotion inference only in **workplace and education** settings. Clinical and consumer wellbeing contexts are not prohibited — they are **high-risk**. Teams read the prohibition, see it doesn't apply, and wrongly conclude the feature is unregulated.

**Also note:** an Annex III system can be argued out of high-risk under **Art. 6(3)** (narrow procedural task, improving a completed human activity, detecting decision patterns, or preparatory task) — but **never if it profiles natural persons**, and a therapeutic personalisation engine almost certainly profiles. If you rely on Art. 6(3) you must document the assessment and still register under Art. 49(2). Budget for this being a hard argument to win.

---

## 2. The catalog

### 2.1 GDPR — Regulation (EU) 2016/679

Assumes: you are a **controller** for clinical and account data; special-category health data is in scope throughout; users include minors.

| ID | Article | Official title | Requirement as it applies to a teletherapy app | Evidence artefact | Conf. |
|---|---|---|---|---|---|
| G-01 | Art. 5(1) | Principles relating to processing of personal data | Lawfulness, fairness, transparency; purpose limitation; data minimisation; accuracy; storage limitation; integrity and confidentiality. Session transcripts and affect data are the minimisation pressure point. | Data map; retention schedule | `V` |
| G-02 | Art. 5(2) | Principles relating to processing of personal data (accountability) | Demonstrate compliance, not merely achieve it. Every row below needs an artefact, not an assertion. | Accountability register | `V` |
| G-03 | Art. 6(1) | Lawfulness of processing | Identify an Art. 6 basis for each purpose. Contract (6(1)(b)) for service delivery; legitimate interests (6(1)(f)) for security/analytics with an LIA. Note 6(1)(f) is **unavailable** as the sole basis for health data — you still need Art. 9. | Lawful basis register; LIA | `CHECK` |
| G-04 | Art. 9(1) | Processing of special categories of personal data | Mental-health content, diagnoses, affect inferences and even the fact of being a therapy user are special-category data. Default prohibition applies. | Special-category inventory | `V` |
| G-05 | Art. 9(2)(h) | Processing of special categories of personal data | Preferred condition where care is delivered by or under the responsibility of a health professional: preventive/occupational medicine, medical diagnosis, provision of health care or treatment. | Clinical governance policy | `CHECK` |
| G-06 | Art. 9(3) | Processing of special categories of personal data | 9(2)(h) is conditional on the data being processed by, or under the responsibility of, a professional bound by professional secrecy. Engineering and support staff access must be governed accordingly. | Access control matrix; confidentiality undertakings | `CHECK` |
| G-07 | Art. 9(2)(a) | Processing of special categories of personal data | Explicit consent — the fallback where 9(2)(h) is unavailable (wellbeing apps with no clinician in the loop, secondary uses, research). Must be separable and withdrawable. | Consent records | `CHECK` |
| G-08 | Art. 7 | Conditions for consent | Where consent is the basis: demonstrable, freely given, as easy to withdraw as to give. Consent bundled into ToS acceptance fails. | Consent UX; consent log schema | `V` |
| G-09 | Art. 8 | Conditions applicable to child's consent in relation to information society services | Age of digital consent is 16, lowered to as far as 13 by Member State law — **it varies across the EU**. Adolescent teletherapy needs per-market age gating and verifiable parental authorisation below the threshold. | Age-gating spec; per-market age matrix | `V` |
| G-10 | Art. 12 | Transparent information, communication and modalities for the exercise of the rights of the data subject | Concise, intelligible, plain language; response to rights requests within one month. Reading level matters more than usual for a distressed user base. | Privacy notice; DSR SLA | `V` |
| G-11 | Art. 13 | Information to be provided where personal data are collected from the data subject | Full notice at collection: identity, purposes, bases, recipients, transfers, retention, rights, and — under 13(2)(f) — meaningful information about the logic of any automated decision-making. | Layered privacy notice | `V` |
| G-12 | Art. 14 | Information to be provided where personal data have not been obtained from the data subject | Applies to referral data from clinicians, insurers or employers. | Third-party source notice | `V` |
| G-13 | Art. 15 | Right of access by the data subject | Access to the record including session transcripts and model-derived inferences. Decide now whether clinician process notes are in scope — Member State health-record law modifies this. | DSAR runbook | `V` |
| G-14 | Art. 16 | Right to rectification | Correction of clinical record entries, subject to health-record integrity rules. | Record amendment procedure | `V` |
| G-15 | Art. 17 | Right to erasure ('right to be forgotten') | Erasure, materially constrained by 17(3)(b)/(c) health-record retention duties under national law. Do not build an unqualified delete button and do not promise one. | Erasure decision tree | `V` |
| G-16 | Art. 18 | Right to restriction of processing | Suspend processing pending accuracy or objection disputes. | Restriction flag in data model | `V` |
| G-17 | Art. 20 | Right to data portability | Structured, commonly used, machine-readable export of user-provided and observed data. Continuity-of-care driver as much as a compliance one. | Export format spec | `V` |
| G-18 | Art. 21 | Right to object | Absolute right to object to direct marketing; qualified for legitimate-interest processing. | Objection handling | `V` |
| G-19 | Art. 22 | Automated individual decision-making, including profiling | Engages if AI alone determines care pathway, risk tier or access. **Art. 22(4)**: automated decisions on special-category data are permitted only on 9(2)(a) explicit consent or 9(2)(g) substantial public interest, with safeguards. Human-in-the-loop must be meaningful, not a rubber stamp. | ADM inventory; human review protocol | `CHECK` |
| G-20 | Art. 24 | Responsibility of the controller | Implement and review appropriate technical and organisational measures. | ISMS / privacy programme | `V` |
| G-21 | Art. 25 | Data protection by design and by default | Pseudonymisation and minimisation by default. Default-off for optional affect analytics; no dark patterns in the consent flow. | DPbD design review gate | `V` |
| G-22 | Art. 26 | Joint controllers | Common where therapists practise independently on the platform. Requires a transparent arrangement and a published essence of it. | Joint controller agreement | `V` |
| G-23 | Art. 27 | Representatives of controllers or processors not established in the Union | Non-EU providers targeting EU users must appoint an EU representative. | Representative appointment | `V` |
| G-24 | Art. 28 | Processor | Art. 28(3) contract terms with every processor — cloud, transcription, LLM API, analytics, crisis-line integrations. Sub-processor authorisation chain must be documented. | DPA register; sub-processor list | `V` |
| G-25 | Art. 30 | Records of processing activities | ROPA. The Art. 30(5) small-organisation exemption **does not apply** — you process special categories, so it is mandatory regardless of headcount. | ROPA | `V` / `CHECK` on (5) |
| G-26 | Art. 32 | Security of processing | Encryption in transit and at rest, pseudonymisation, resilience, restore capability, regular testing. Session recordings and transcripts are the crown jewels. | Security controls doc; pen-test reports | `V` |
| G-27 | Art. 33 | Notification of a personal data breach to the supervisory authority | 72 hours from awareness. A mental-health data breach will almost never clear the "unlikely to result in a risk" bar. | IR plan; breach log | `V` |
| G-28 | Art. 34 | Communication of a personal data breach to the data subject | Communicate without undue delay where high risk. Assume high risk by default for this data class. | User notification templates | `V` |
| G-29 | Art. 35 | Data protection impact assessment | **Mandatory.** Art. 35(3)(b) — large-scale processing of special categories — is met on its own; 35(3)(a) systematic evaluation via profiling is likely met too. Do this before launch, not after. | DPIA | `V` / `CHECK` on (3) |
| G-30 | Art. 36 | Prior consultation | Consult the supervisory authority if the DPIA shows high residual risk you cannot mitigate. Adds real calendar time — plan for it. | Consultation record | `V` |
| G-31 | Art. 37 | Designation of the data protection officer | **Mandatory** under 37(1)(c) — core activities consist of large-scale special-category processing. | DPO appointment; notification to SA | `V` / `CHECK` on (1)(c) |
| G-32 | Art. 44 | General principle for transfers | General principle governing any third-country transfer. | Transfer register | `V` |
| G-33 | Art. 46 | Transfers subject to appropriate safeguards | SCCs plus a transfer impact assessment for US-hosted LLM inference, transcription or support tooling — the usual failure point in this product category. | SCCs; TIAs | `V` |
| G-34 | Art. 49 | Derogations for specific situations | Narrow, non-repetitive derogations. **Do not** build routine transfers on 49(1)(a) explicit consent. | Derogation log (should be near-empty) | `V` |
| G-35 | Art. 89 | *(safeguards for archiving/research/statistics)* | Engages for secondary use of clinical data in model training or research. Title not verified. | Research safeguards policy | `CHECK` |
| G-36 | Art. 83 | *(general conditions for imposing administrative fines)* | Up to EUR 20 000 000 or 4% of total worldwide annual turnover for Art. 5, 6, 7, 9 and rights breaches. Title not verified. | — | `CHECK` |

### 2.2 EU AI Act — Regulation (EU) 2024/1689 as amended by Regulation (EU) 2026/1744

| ID | Article | Official title | Requirement as it applies to a teletherapy app | Applies from | Conf. |
|---|---|---|---|---|---|
| A-01 | Art. 3 | Definitions | Establish role: provider, deployer, or both. Building your own model makes you a provider; substantially modifying a third-party system can also make you one. Art. 3(14) "safety component" was **narrowed** by the 2026 amendment. | In force | `V` |
| A-02 | Art. 4 | AI literacy | Ensure staff have sufficient AI literacy. The 2026 amendment softened this from "shall ensure" to a measures-based duty, but do not treat it as gone — clinicians supervising AI outputs are exactly who it targets. | 2 Feb 2025 | `V` |
| A-03 | Art. 4a | *(processing of special categories of personal data for bias detection and correction)* | **New, inserted by Reg. 2026/1744.** Permits processing special-category data strictly necessary for bias detection and correction under safeguards. Directly useful for demographic fairness testing of a therapy model — but read alongside Art. 10(5), which covers the same ground for high-risk systems. Reconcile the two before relying on either. | 27 Jul 2026 | `CHECK` |
| A-04 | Art. 5(1)(a) | Prohibited AI practices | No subliminal, purposefully manipulative or deceptive techniques materially distorting behaviour and causing significant harm. | 2 Feb 2025 | `CHECK` on point |
| A-05 | Art. 5(1)(b) | Prohibited AI practices | No exploitation of vulnerabilities due to age, disability or specific social or economic situation. **The highest-severity row in this catalog for this product category.** Review engagement loops, streaks, loss-framing and upsell timing against it. | 2 Feb 2025 | `CHECK` on point |
| A-06 | Art. 5(1)(f) | Prohibited AI practices | Emotion inference prohibited in **workplace and education** only. Relevant if you sell to employers (EAP channel) or universities — the same feature that is high-risk in the consumer app may be **prohibited** in the B2B one. | 2 Feb 2025 | `CHECK` on point |
| A-07 | Art. 5(1)(ba), (bb) | Prohibited AI practices | **New, inserted by Reg. 2026/1744.** Non-consensual intimate imagery and CSAM generation. Relevant only if you ship a generative avatar or image capability — but if you do, it is an absolute bar. | 2 Dec 2026 | `CHECK` |
| A-08 | Art. 6 | Classification rules for high-risk AI systems | Run the classification. Art. 6(1) product route; Art. 6(2) Annex III route; Art. 6(1a)–(1c) narrow what counts as a safety component; Art. 6(3) is the derogation, unavailable where you profile. | See §1 | `V` |
| A-09 | Art. 6(4) | Classification rules for high-risk AI systems | If you conclude an Annex III system is **not** high-risk, document the assessment before placing on the market and still register under Art. 49(2). | 2 Dec 2027 | `CHECK` |
| A-10 | Art. 7 | Amendments to Annex III | Watch item — the Commission may extend Annex III. | Ongoing | `V` |
| A-11 | Art. 8 | Compliance with the requirements | Umbrella obligation for Section 2 requirements. | 2 Dec 2027 | `V` `SCOPE` |
| A-12 | Art. 9 | Risk management system | Continuous, iterative risk management across the lifecycle. Must consider foreseeable misuse — for teletherapy, read that as crisis-state misuse, dependency, and off-label clinical reliance. | 2 Dec 2027 | `V` `SCOPE` |
| A-13 | Art. 10 | Data and data governance | Training/validation/test data governance; representativeness; examination for bias. Art. 10(5) permits special-category processing for bias detection. Demographic and linguistic coverage of therapeutic training data is the live risk. | 2 Dec 2027 | `V` `SCOPE` |
| A-14 | Art. 11 | Technical documentation | Annex IV technical documentation, complete before placing on market and kept current. | 2 Dec 2027 | `V` `SCOPE` |
| A-15 | Art. 12 | Record-keeping | Automatic logging over the system lifetime. Design the log schema against GDPR minimisation now — the two obligations pull in opposite directions and retrofitting is painful. | 2 Dec 2027 | `V` `SCOPE` |
| A-16 | Art. 13 | Transparency and provision of information to deployers | Instructions for use enabling deployers to interpret output. Where clinicians are the deployers, this is the clinical-use-instructions artefact. | 2 Dec 2027 | `V` `SCOPE` |
| A-17 | Art. 14 | Human oversight | Design for effective oversight by a natural person: ability to interpret, override, and disregard output. For a crisis-detection feature this must be a real clinical escalation path, staffed. | 2 Dec 2027 | `V` `SCOPE` |
| A-18 | Art. 15 | Accuracy, robustness and cybersecurity | Declared accuracy metrics, resilience, and resistance to adversarial manipulation — including prompt injection against a conversational agent. | 2 Dec 2027 | `V` `SCOPE` |
| A-19 | Art. 16 | Obligations of providers of high-risk AI systems | Consolidated provider duty list. | 2 Dec 2027 | `V` `SCOPE` |
| A-20 | Art. 17 | Quality management system | QMS. Where you are also an MDR manufacturer, integrate with ISO 13485 rather than running two systems. | 2 Dec 2027 | `V` `SCOPE` |
| A-21 | Art. 18 | Documentation keeping | Retain documentation 10 years after placing on market. | 2 Dec 2027 | `V` `SCOPE` |
| A-22 | Art. 19 | Automatically generated logs | Retain logs under provider control, at least six months unless other law requires longer. | 2 Dec 2027 | `V` `SCOPE` |
| A-23 | Art. 20 | Corrective actions and duty of information | Withdraw/recall and inform the chain when a system is non-conforming. | 2 Dec 2027 | `V` `SCOPE` |
| A-24 | Art. 22 | Authorised representatives of providers of high-risk AI systems | Non-EU providers must appoint an EU authorised representative. **Distinct from the GDPR Art. 27 representative** — you likely need both, and they need not be the same entity. | 2 Dec 2027 | `V` `SCOPE` |
| A-25 | Art. 25 | Responsibilities along the AI value chain | Substantially modifying, or putting your name on, a third-party model can make you the provider. The single most commonly missed row for teams building on a foundation-model API. | 2 Dec 2027 | `V` |
| A-26 | Art. 26 | Obligations of deployers of high-risk AI systems | If clinicians or clinics deploy your system: use per instructions, assign competent human oversight, monitor, retain logs, inform affected persons. | 2 Dec 2027 | `V` |
| A-27 | Art. 27 | Fundamental rights impact assessment for high-risk AI systems | FRIA — obligation falls on **deployers that are public bodies or private entities providing public services**, and on Annex III 5(b)/(c) deployers. Engages if you contract with public health systems. Not a general obligation. | 2 Dec 2027 | `V` `SCOPE` |
| A-28 | Art. 43 | Conformity assessment | Internal control (Annex VI) or notified body (Annex VII) depending on route. Medical-device route runs through the MDR notified body. | 2 Dec 2027 / 2 Aug 2028 | `V` `SCOPE` |
| A-29 | Art. 47 | EU declaration of conformity | Draw up and keep for 10 years. | Per route | `V` `SCOPE` |
| A-30 | Art. 48 | CE marking | Affix CE marking. | Per route | `V` `SCOPE` |
| A-31 | Art. 49 | Registration | Register in the EU database before placing on market — including, under 49(2), systems you assessed as non-high-risk under Art. 6(3). | 2 Dec 2027 | `V` `SCOPE` |
| A-32 | Art. 50(1) | Transparency obligations for providers and deployers of certain AI systems | **Disclose to the user that they are interacting with an AI system**, unless obvious. Applies to *any* conversational teletherapy agent regardless of risk tier. In an app where the user may believe they are talking to a therapist, "obvious" is not a defence you should lean on. | **2 Aug 2026 — in force now** | `V` |
| A-33 | Art. 50(2) | Transparency obligations for providers and deployers of certain AI systems | Mark synthetic audio/image/video/text in a machine-readable, detectable format. Engages for synthetic voice or avatar therapists. Systems on the market before 2 Aug 2026 have until 2 Dec 2026. | 2 Aug 2026 / 2 Dec 2026 | `V` |
| A-34 | Art. 50(5) | Transparency obligations for providers and deployers of certain AI systems | Disclosure clear and distinguishable, **at the latest at the time of first interaction**, and accessible. Not buried in a settings screen or ToS. | 2 Aug 2026 | `V` |
| A-35 | Art. 72 | Post-market monitoring by providers and post-market monitoring plan for high-risk AI systems | Post-market monitoring plan. Integrate with MDR post-market surveillance where both apply. | 2 Dec 2027 | `V` `SCOPE` |
| A-36 | Art. 73 | Reporting of serious incidents | Report serious incidents to market surveillance authorities. For teletherapy, define "serious incident" to include missed crisis detection and harmful model output — and align the clock with GDPR Art. 33's 72 hours so one incident process serves both. | 2 Dec 2027 | `V` `SCOPE` |
| A-37 | Art. 86 | Right to explanation of individual decision-making | Affected persons may obtain a clear and meaningful explanation of the role of the AI system in decisions producing legal or similarly significant effects. Overlaps GDPR Art. 22 — build one explanation capability, not two. | 2 Dec 2027 | `V` |
| A-38 | Art. 99 | Penalties | Up to EUR 35 000 000 or 7% of worldwide turnover for Art. 5 prohibitions; up to EUR 15 000 000 or 3% for most other obligations. | Per regime | `V` / `CHECK` on figures |
| A-39 | Art. 113 | Entry into force and application | Governs every date in this table. Amended by Reg. 2026/1744: Annex III high-risk **2 Dec 2027**; Annex I / Art. 6(1) high-risk **2 Aug 2028**. | — | `V` |

---

## 3. Open scoping questions — these block completion

The table cannot be finished without answers to these. They are product and clinical decisions, not legal ones.

1. **Does the app infer emotional state** from voice, facial expression or text? Yes → Annex III 1(c), high-risk, and roughly rows A-11 to A-31 activate.
2. **Does it make a therapeutic or diagnostic claim** that makes it an MDR medical device? Yes → likely Class IIa+, notified body, and the Art. 6(1) route with the 2028 date.
3. **Is there a crisis / suicide-risk detection feature**, and does it dispatch to emergency services? Yes → Annex III 5(d) becomes live and Art. 14 human oversight becomes a staffing commitment, not a design note.
4. **Is there a B2B employer or university channel?** Yes → Art. 5(1)(f) may **prohibit** emotion features that are merely high-risk in the consumer product.
5. **Are you a provider, a deployer, or both?** Building on a foundation-model API with your own system name almost certainly makes you a provider under Art. 25.
6. **Which Member States?** Art. 8 digital-consent age varies 13–16; health-record retention and professional-secrecy rules are national and will override several GDPR rows.
7. **Minors in scope?** Changes G-09, the DPIA, and the manipulation analysis under A-05.

---

## 4. Adjacent instruments deliberately excluded

You asked for GDPR and the AI Act. These will come up in review anyway, and omitting them silently would misrepresent the compliance surface:

- **MDR (Regulation (EU) 2017/745)** — determines the AI Act Art. 6(1) route and brings its own clinical evaluation and post-market surveillance regime. Not optional if you make a therapeutic claim.
- **National telemedicine and professional-secrecy law** — licensure, cross-border practice, record retention. Genuinely varies and will constrain G-13, G-15 and G-06.
- **ePrivacy Directive** — cookies and device-storage consent, separate from and additional to GDPR consent.
- **European Health Data Space (Regulation (EU) 2025/327)** — secondary use of health data and EHR interoperability. Phasing in; relevant if you train on clinical data or integrate with national health records.
- **Pending Digital Omnibus (data)** — proposed November 2025, amending GDPR and ePrivacy, **not yet law**. If adopted it may touch the special-category definition and consent rules underpinning G-04 to G-08. Track it; do not build to it.

---

## 5. Suggested next step

Answer the seven questions in §3, then I can collapse the `SCOPE` rows to a definite in/out and cut the catalog roughly in half. In parallel, someone with EUR-Lex access should read back the seventeen `CHECK` rows against the consolidated texts so the catalog can be baselined as verified.
