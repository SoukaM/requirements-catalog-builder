# AD-CAT: results

This folder holds the data behind the paper *A Requirements Catalog on Functional Suitability, Interaction Capability, Security, Safety and AI for Anxiety and Depression Apps* (Moumou and Idri). AD-CAT was built with the `requirements-catalog-builder` skill in this repository.

## What is here

| Folder | File | What it contains | Paper |
| --- | --- | --- | --- |
| `catalog/` | `AD-CAT-catalog.csv` | All 120 entries (115 requirements and 5 sub-requirements), with characteristic, source clause or item, origin tag, scope and who can check it | Tables 5 to 9 |
| `catalog/` | `AD-CAT-catalog.md` | The same catalog as readable tables, one per characteristic | Tables 5 to 9 |
| `extraction/` | `candidates-and-decisions.csv` | All 164 rows: the 161 candidates the model proposed, plus the 3 requirements the author added. For each one: source, clause or item, the proposed wording, the decision (kept, rewritten, merged, rejected or added) and the ID it became in the final catalog | Section 3.2.3 |
| `extraction/` | `extraction-log.csv` | Candidates proposed, kept, rewritten, merged and rejected for each of the ten sources | Table 2 |
| `audit/` | `applicability-gates.csv` | The gates answered for each app before scoring | Section 5.1 |
| `audit/` | `checklist-answers.csv` | The 30-item checklist: each question, the requirement it checks, the criteria for Yes, Partially and No, and our answer and evidence for each app | Table 13 |
| `audit/` | `hr-supplement.csv` | The 11 extra items for high-risk AI systems. Neither app is high-risk, so they were not scored | Section 5.3 |
| `audit/` | `coverage-by-section.csv` | Coverage of each app by catalog section | Table 15 |
| `audit/` | `app-characteristics.md` | Characteristics of Wysa and MindDoc at the time of the audit | Tables 11 and 12 |
| `audit/` | `audit-report-summary.md` | Summary of the two audit reports | Table 14 |

## How the data was produced

- **Sources.** Ten sources were given to the skill: five standards (IEC 82304-1:2016, ISO/IEC 25010:2023, ISO/IEC 25059:2023, ISO/IEC 25023:2016 and ISO/IEC 25040:2024), the EU AI Act, and four instruments (Moumou and Idri 2026, Rickard et al. 2022, Wu et al. 2021, Qu et al. 2020). ISO/IEC 25023 and ISO/IEC 25040 produced no candidates.
- **Extraction.** Claude Sonnet 5 proposed the candidate requirements and Claude Opus 5 organised the kept ones into the IEEE 29148 structure. The prompts are in `requirements-catalog-builder/references/extraction-prompt.md` and in Appendix A of the paper.
- **Verification.** The first author checked every candidate against its source clause or item. No candidate cited a clause that does not exist, and none misquoted its clause.
- **Origin tags.** `H` = written by the author (3), `AI-K` = proposed by the model and kept as is (93), `AI-R` = proposed by the model and then rewritten or merged (24).
- **Audit.** One auditor answered the checklist on 16 September 2026, on a fresh install of Wysa 7.0.1 and MindDoc 4.18.32, using an iPhone 14 Pro (iOS 26) and a Huawei P30 Lite (Android). Coverage = Yes / (Yes + No + Partially). Weighted coverage counts Partially as half a Yes.

## Scope and "Checked by" columns in the catalog

- `All apps`: applies to every anxiety or depression app.
- `AI`: applies only to apps with AI features. Scored N/A otherwise.
- `HR`: applies only when the AI system is high-risk under the EU AI Act.
- `Manufacturer only` in the "Checked by" column (marked (M) in the paper): can only be checked by the manufacturer, because it depends on internal records such as the risk management file or the security logs. These six requirements were left out of the audit, but they stay in the catalog for manufacturers who use it to build an app.

## Licence

Same licence as the rest of this repository (see `LICENSE`).
