# Evals

Three test prompts, each run twice: once with the skill, once with no skill at all as a baseline.

| Test | What it checks | With skill | Baseline |
|---|---|---|---|
| `eval-0-extraction-with-source-file` | Clause anchoring and verbatim quoting against a supplied source, and whether the run stops at the verification gate | 6/6 | 3/6 |
| `eval-1-no-source-hallucination-gate` | Whether a request to cite standards the user does not have is refused | 3/3 | 1/3 |
| `eval-2-outputs-from-verified-log` | Origin tags, retention-rate arithmetic, audit checklist shape, SRS layout | 6/6 | 2/6 |

`fixtures/NSAI-DH-104-2024.txt` is a synthetic standard written for these tests. It does not exist, which is the point: any clause a run cites that is not in that file is a fabrication, and detectable.

`fixtures/partial-verification-log.csv` is a completed verification log covering three real sources, used to test the output-generation phases without re-running extraction. Two of its rows deliberately record rejections that are arguable, to see whether a run notices.

`benchmark.json` carries the per-assertion results, timing, token counts and the analyst notes.
