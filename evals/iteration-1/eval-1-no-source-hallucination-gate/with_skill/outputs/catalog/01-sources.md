# Phase 1: Source register

Date: 2026-09-07

Status legend: `full text available` = the author can open the text and check a clause in it ·
`to obtain` = named but not yet in hand, and therefore **not extractable**.

| Code | Full citation | Type | File path | Status |
|---|---|---|---|---|
| `GDPR` | Regulation (EU) 2016/679 of the European Parliament and of the Council of 27 April 2016 on the protection of natural persons with regard to the processing of personal data and on the free movement of such data (General Data Protection Regulation), OJ L 119, 4.5.2016, p. 1–88. | International / EU law | — | **to obtain** |
| `AIACT` | Regulation (EU) 2024/1689 of the European Parliament and of the Council laying down harmonised rules on artificial intelligence (Artificial Intelligence Act), OJ L, 12.7.2024. | International / EU law | — | **to obtain** |

Note on the two citations above: the titles and OJ references are given from recall as a
convenience for finding the documents. **Check them against the EUR-Lex record when you download the
text**, and correct this table if they differ. The catalog's citations must come from the document in
hand, not from this row.

Where to get consolidated official texts (both free, both authoritative):

- EUR-Lex, consolidated version, GDPR: CELEX `02016R0679`
- EUR-Lex, consolidated version, AI Act: CELEX `32024R1689`
- Both are downloadable as PDF and HTML in all EU languages. Take the English consolidated version,
  save it into this folder, and record the path in the table above.

## Why both rows say "to obtain"

The author asked for a requirement table with article numbers filled in from recall. That table
cannot be produced. A clause locator produced from memory is the one failure this method exists to
prevent: it looks like finished work, it survives casual review, and a single fabricated article
number in a published catalog is a retraction-class error. Recording the sources as "to obtain"
rather than quietly extracting from recall is the correct state of the project right now.

The extraction prompts for both sources are already written and waiting in `prompts/` — they need
only the source text pasted in.

## Sources worth adding before extraction starts

A catalog built on GDPR and the AI Act alone would cover data protection and AI governance and
nothing else. It would have no requirement about therapeutic safety, crisis escalation, session
quality or usability, which for teletherapy is a conspicuous hole. Candidates, for the author to
accept or reject:

| Suggested code | Source | Fills |
|---|---|---|
| `ISO25010` | ISO/IEC 25010, Systems and software quality models | Quality characteristic backbone |
| `ISO82304` | IEC 82304-1, Health software — Product safety requirements | Clinical safety |
| `ISO81001` | IEC 81001-5-1, Health software security | Security in the health context |
| `EN17926` | EN 17926, Health software — Quality and reliability of health and wellness apps | Domain-specific, EU-aligned |
| `NICE-ESF` | NICE Evidence Standards Framework for digital health technologies | Evidence and effectiveness |
| `WHO-DH` | WHO guideline: recommendations on digital interventions for health system strengthening | Clinical/organisational |
| `MDR` | Regulation (EU) 2017/745 (Medical Device Regulation) | Only if the app makes a therapeutic claim — a scope decision |
| `EAA` | Directive (EU) 2019/882 (European Accessibility Act) | Accessibility |

Each of these carries the same rule: it enters the register with status `to obtain` and contributes
nothing until its text is in hand.
