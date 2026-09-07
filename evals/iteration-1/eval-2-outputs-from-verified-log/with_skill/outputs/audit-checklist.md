# Audit checklist

Derived from the requirements catalog for privacy, security and accessibility in mental wellbeing apps. One question per requirement. Answer domain: **Yes / No / Partially / N/A**.

A "No" or "Partially" points back at the requirement ID, and from there at the source clause in `catalog.md`, so a finding can be traced to the authority it comes from.

**How to use:** assess one app at a time with the app in front of you. Record evidence (screen, setting path, export file, policy page) for every answer, including "Yes" answers — an unevidenced Yes is not an audit result. Use "N/A" only where the app has no feature the question could apply to, and say why in the note.

## Privacy (PRIV)

| ID | Question | Answer | Evidence | Assessor note |
|---|---|---|---|---|
| PRIV-01 | Does the app enable the user to receive their personal data in a structured, commonly used and machine-readable format? | Yes / No / Partially / N/A | | |
| PRIV-02 | Does the app erase the user's personal data on request where the data are no longer necessary for the purpose for which they were collected? | Yes / No / Partially / N/A | | |
| PRIV-03 | Does the app, by default, process only the personal data necessary for each specific purpose? | Yes / No / Partially / N/A | | |
| PRIV-04 | Does the app encrypt personal data at rest on the user's device? | Yes / No / Partially / N/A | | |
| PRIV-05 | Can a user use all self-monitoring features without creating an account? | Yes / No / Partially / N/A | | |
| PRIV-06 | Does the app present a plain-language summary of what data leave the device before the first data transmission? | Yes / No / Partially / N/A | | |

## Security (SEC)

| ID | Question | Answer | Evidence | Assessor note |
|---|---|---|---|---|
| SEC-01 | Does the app permit passwords of at least 64 characters in length? | Yes / No / Partially / N/A | | |
| SEC-02 | Does the app verify prospective passwords against a list of commonly used or compromised values? | Yes / No / Partially / N/A | | |
| SEC-03 | Does the app refrain from requiring periodic password rotation in the absence of evidence of compromise? | Yes / No / Partially / N/A | | |

## Accessibility and usability (USA)

| ID | Question | Answer | Evidence | Assessor note |
|---|---|---|---|---|
| USA-01 | Does the app support resizing of text up to 200 percent without loss of content or functionality? | Yes / No / Partially / N/A | | |
| USA-02 | Does the app render a visible focus indicator for any keyboard-operable user interface component? | Yes / No / Partially / N/A | | |
| USA-03 | Does the app provide a text alternative for each non-text content element? | Yes / No / Partially / N/A | | |

## Notes on question form

- SEC-01, SEC-02 and SEC-03 all apply only to apps that use passwords. Where an app authenticates by another means only, answer N/A and record the mechanism used.
- SEC-03 is a negative obligation ("shall not require"), so the question is phrased so that a compliant app scores "Yes". Assessors should watch that they are not scoring the presence of rotation as a positive.
- PRIV-01 carries the source's own compound adjective ("structured, commonly used and machine-readable"); this is one property of the export format, not three separate obligations, so the question is left intact rather than split.
- PRIV-05 and PRIV-06 have no source clause behind them. They are author requirements, and a failed answer traces to the author's judgement rather than to an external authority. Keep that distinction visible when reporting audit results.
