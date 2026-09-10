# CDL / Non-CDL Drug & Alcohol Testing Flow — v12

Live runtime update added 2026-09-10.

## Scope
The driver-classification gate applies only to incident forms that currently carry Drug & Alcohol review:
- Personal Injury
- Vehicle Incident
- Utility Strike
- Property Damage

It remains hidden/disabled for:
- 3rd Party Incident
- Vandalism / Theft
- Safety Observation & Prevention reports (Near Miss / Good Catch)

## First question
**Is the involved employee/driver a CDL driver?**

Two options only:
- CDL Driver
- Non-CDL Driver

## CDL path
Opens the existing CDL / DOT post-accident questionnaire and keeps the existing treatment/testing location finder beneath it.

## Non-CDL path
Asks:
1. Is the employee at fault for this incident?
2. Does the company’s approved non-DOT policy require post-incident testing when the employee is at fault?
3. Has Safety / the authorized employer representative directed testing?

If employee-at-fault = Yes and company-policy = Yes, the decision guide states **Testing indicated under company non-DOT policy** and directs the user to an approved testing location, subject to authorized-employer-representative direction.

Pending/unknown fault or policy-review selections route to Safety / authorized representative review.

## Runtime implementation
The v12 HTML/CSS/JS is appended as a second gzip member to `p10b.txt`. The production Safety Cage loader already uses `DecompressionStream('gzip')`, which decompresses concatenated gzip members in order. The v12 script runs on the window load event after the existing v11 patch so it can safely layer on top of the current incident logic.

Backup of the previous runtime tail:
`p10b.pre-cdl-noncdl-v12.backup.txt`
