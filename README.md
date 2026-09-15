# requirements-catalog-builder

A [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that guides you through building a reusable software requirements catalog for any domain, using AI to pre-extract candidate requirements from standards, with mandatory human verification of every clause citation.

The domain and the source standards are inputs. The method is fixed.

## Why

Requirements catalogs are built by harvesting obligations from standards, laws, guidelines and prior literature, then structuring them so they can be reused across products. The SIREN approach and the IEEE 29148 SRS layout give the structure. A family of published e-health catalog papers (Ouhbi, Zapata, Bachiri, Sardi, all with Ali Idri) established the pattern this skill follows.

Language models are useful for the harvesting step and dangerous in one specific way: they produce clause numbers that look correct and are not. A requirement citing `Art. 33(9)` reads as authoritative whether or not that paragraph exists, and it survives casual review. One fabricated citation in a published catalog is a retraction-class error.

So this skill is built around a gate. Nothing enters the catalog until a human has opened the source and confirmed the clause exists and says what was claimed. Everything else is bookkeeping around that gate.

## What it produces

- **Requirement tables**, one per category: `ID | Requirement | Source (with clause) | Origin`
- **An extraction log**: `Source | Candidates proposed | Kept | Rewritten | Rejected | Retention rate`, with totals, and the citation failure rate reported separately. This is a research result, not admin.
- **An audit checklist** derived from the requirements, as Yes / No / Partially / N/A questions carrying requirement IDs
- **The exact extraction prompt used**, saved for a paper appendix with the model and date

Outputs are written as markdown plus CSV, with a Word version on request.

## The workflow

| Phase | What happens |
|---|---|
| 0 | Confirm the domain scope, the source list, and the quality characteristics to cover |
| 1 | Register each source with a short code and whether the full text is available |
| 2 | Extract candidate `shall` statements from the source text, each carrying its exact clause locator and a verbatim quote |
| 3 | **Human verification.** Keep, rewrite, or reject each candidate, having opened the source |
| 4 | Tag origin: `H` (you wrote it), `AI-K` (model proposed, kept as is), `AI-R` (model proposed, you rewrote it) |
| 5 | Assign permanent IDs and organise into the IEEE 29148 SRS structure |
| 6 | Produce the four outputs |

If a source is not available as text, the skill refuses to extract from it and records it as a source to obtain. It does not produce clause numbers from recall.

## Origin tagging

The `H` / `AI-K` / `AI-R` split is reportable. It tells a reader how much of the catalog the model actually produced and how much of its wording survived contact with the sources, which is a claim catalog papers using AI assistance need to be able to make.

## Compatibility

This skill is written in the [Agent Skills](https://agentskills.io) format: a SKILL.md file with YAML frontmatter, plus progressively-loaded reference and asset files. That format is now an open, vendor-neutral standard, not exclusive to Claude. Tools with native support for loading a skill folder like this one include Cursor, GitHub Copilot, OpenAI Codex, Google Gemini CLI, JetBrains Junie, Goose, and others in the [Agent Skills client list](https://agentskills.io/home) — drop `requirements-catalog-builder/` into the tool's skills directory and it should discover and trigger on its own, the same way it does in Claude Code.

### Manual use in other AI tools

Plain chat interfaces without a skills system (a ChatGPT or Gemini web chat, a bare API call) have no folder-loading or auto-trigger mechanism. To use this skill there:

1. Paste the contents of `SKILL.md` in as a system prompt or custom instructions.
2. Upload or paste in the files under `references/` and `assets/` alongside it, since progressive disclosure (the model loading them itself, only when needed) won't happen automatically.
3. Tell the model explicitly which phase to start from, since there's no auto-trigger on a description match.

## Install

Download `requirements-catalog-builder.skill` from the [releases](../../releases) or clone this repo and copy the `requirements-catalog-builder/` directory into your skills directory:

- Claude Code: `~/.claude/skills/`
- Claude.ai and Cowork: upload the `.skill` file in settings

Then ask for a requirements catalog and the skill triggers on its own.

## Layout

```
requirements-catalog-builder/
  SKILL.md                          the workflow
  references/srs-structure.md       IEEE 29148 section layout, and how to map quality characteristics onto it
  references/extraction-prompt.md   the exact prompt, written to be publishable in an appendix
  references/validation-rules.md    keep / rewrite / reject criteria, IEEE 29148 requirement quality attributes
  assets/*.csv                      header templates for the output tables
evals/                              test prompts, fixtures, assertions and iteration-1 results
```

## Testing

The skill was benchmarked against an unassisted baseline on three tasks: extraction from a supplied source, a request to cite standards the user does not have, and output generation from a completed verification log. See `evals/` for the prompts, fixtures and results.

The gap concentrates on the case the skill exists for. Asked for "GDPR and AI Act article numbers, you know them well enough", the unassisted baseline produced a 75-requirement catalog with 50 distinct article citations. With the skill, zero requirement rows and a request for the source texts.

Assertions passed: 15/15 with the skill, 6/15 without.

## Method references

- ISO/IEC/IEEE 29148, Systems and software engineering: life cycle processes, requirements engineering
- Toval, A., Nicolás, J., Moros, B., García, F. (2002). Requirements reuse for improving information systems security: a practitioner's approach. *Requirements Engineering* 6(4). The SIREN approach.
- Ouhbi, S., Idri, A., Fernández-Alemán, J.L., Toval, A. Requirements engineering for mobile personal health applications, and the related catalog papers by Zapata, Bachiri and Sardi with Idri.

## Licence

MIT. See [LICENSE](LICENSE).
