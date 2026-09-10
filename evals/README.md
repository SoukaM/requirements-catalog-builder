# Evals

Four test prompts. The first three are run twice: once with the skill, once with no skill at all as a baseline.

| Test | What it checks | With skill | Baseline |
|---|---|---|---|
| `eval-0-extraction-with-source-file` | Clause anchoring and verbatim quoting against a supplied source, and whether the run stops at the verification gate | 6/6 | 3/6 |
| `eval-1-no-source-hallucination-gate` | Whether a request to cite standards the user does not have is refused | 3/3 | 1/3 |
| `eval-2-outputs-from-verified-log` | Origin tags, retention-rate arithmetic, audit checklist shape, SRS layout | 6/6 | 2/6 |
| `instrument-source-item-extraction` (id 3) | Whether a source carrying a validated questionnaire/instrument gets its item table extracted, instead of only the handful of normative sentences in its surrounding prose | not yet benchmarked | not yet benchmarked |

`fixtures/NSAI-DH-104-2024.txt` is a synthetic standard written for these tests. It does not exist, which is the point: any clause a run cites that is not in that file is a fabrication, and detectable.

`fixtures/partial-verification-log.csv` is a completed verification log covering three real sources, used to test the output-generation phases without re-running extraction. Two of its rows deliberately record rejections that are arguable, to see whether a run notices.

`fixtures/instrument-source-sample.pdf` is a real 44-app systematic review (Moumou & Idri) built around a 37/38-item assessment questionnaire in a table, with almost no normative prose of its own. It was added after a real run against this exact paper, using the skill's normative-only Phase 2 procedure, produced only 3 candidates from the paper's Conclusion and missed the questionnaire entirely — the failure this eval case exists to catch. The skill was then given a second Phase 2 mode (the `instrument`/`normative` extraction-type split in `01-sources.md` and the instrument variant of the extraction prompt) so that a source like this is routed to its item table instead of a verb search. This eval case has not yet been run as a scored with-skill/baseline pair; it is recorded here so the next benchmark run picks it up. Note for whoever runs it: a careful, deliberate extraction can find the item table even under the *old* (normative-only) skill wording if the prompt or the model's own diligence happens to surface it — the real-world 3-candidate failure this fixture is drawn from happened via momentum/pattern-matching without formally invoking Phase 1/2 at all, so the with-skill/baseline gap here may be smaller than it looks from the original incident. The instrument mode is still worth keeping because it makes the correct behavior explicit-by-design rather than incidental, and separates item-derived from prose-derived candidates on any instrument source, not just this one.

`benchmark.json` carries the per-assertion results, timing, token counts and the analyst notes.
