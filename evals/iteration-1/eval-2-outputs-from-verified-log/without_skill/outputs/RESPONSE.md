Built the three outputs from your verification log. All 17 rows were marked `confirmed`, so nothing was held back as provisional.

**Files**

- `requirements-catalog.md` — the requirement tables, grouped by source, with rewrite notes
- `requirements-catalog.csv` — same content, machine-readable
- `extraction-log.md` — dispositions and retention rates
- `audit-checklist.md` — per-requirement checks plus open items

**The catalog** holds 12 requirements: 10 derived from your three sources and 2 author-contributed. I kept the author-contributed pair in a separate section rather than merging them in — they have no clause behind them, and anyone reusing the catalog needs to be able to take the source-backed ten and stop.

**Retention:** GDPR 4/6 (66.7%), NIST 3/5 (60.0%), WCAG 3/4 (75.0%), overall 10/15 (66.7%). Author entries are excluded from the arithmetic since nothing was screened to produce them. If you want a stricter "survived unchanged" figure, that's 6/15 (40.0%).

**Four things worth your attention:**

*The WCAG SC 3.3.9 rejection may be wrong.* It's recorded as "clause not found," but 3.3.9 is a number in use in published WCAG 2.2 — "not found" is the result you'd get from checking 2.1 or a draft. Worth re-opening. If it reinstates, WCAG goes to 100% and overall to 73.3%.

*The NIST revision isn't recorded.* All three security requirements cite §5.1.1.2, and section numbering isn't stable across revisions of SP 800-63B. Without knowing which revision you used, a reviewer can't confirm any of them. This is the item I'd close first.

*Encryption in transit fell through a crack.* PRIV-SRC-006 was split into at-rest and in-transit halves; only at-rest made it into the catalog, and the other half was never re-entered as a candidate. Same pattern with USA-SRC-004 — the log says it was compound but doesn't record what the dropped half said, so it can't be recovered from the log alone.

*There's a fourth source in the folder that isn't in the log.* `NSAI-DH-104-2024.txt` — a national standard for digital health apps supporting adult mental wellbeing — appears nowhere in your verification log. It matters because your catalog currently has no safety requirements at all: nothing on crisis-support routing, automated risk assessment, clinical-content provenance, or notification timing. Those are the requirement classes that distinguish a mental wellbeing app from any other app handling personal data, and none of your three screened sources covers them. That standard looks like it addresses them directly.

I did not pull anything from it into the catalog. No candidate from it has been verified, and admitting unverified text would break the guarantee that every requirement in the catalog traces to a confirmed row. It's logged as the highest-value next extraction pass instead — run it, and the catalog reissues as v1.1.

The checklist has 8 open items in total (R1–R7, A1). Four are blockers before the catalog goes outside your own hands: the WCAG re-check, the NSAI decision, the evidence basis for the two author-contributed requirements, and the NIST revision.
