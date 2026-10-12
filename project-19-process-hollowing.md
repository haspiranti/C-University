# Project 19: The Process Integrity Detective 🕵️
*A defensive simulation of process-hollowing indicators*

### The story
A security team suspects that a process’s reported identity and its mapped image do not match. You’re the investigator, building a local simulator and detection report to understand the evidence. You will not hollow out or replace a real process.

### What you'll build
Build `process_integrity_lab` as a harmless simulation that models the stages and telemetry associated with process hollowing using synthetic process records and a mock memory map. Explain the roles of `NtReadFile`, `NtWriteFile`, `NtUnmapViewOfSection`, `ZwCreateSection`, and `ZwMapViewOfSection` at a conceptual/API-reference level, but do not implement a workflow that unmaps or replaces another process’s executable image. Gold focuses on detecting and defending.

### Sample output

```text
$ ./process_integrity_lab scenario-hollowing.json
Scenario: simulated image replacement
Expected image: C:\Lab\viewer.exe
Observed mapped image: C:\Lab\unknown.bin
Image identity mismatch: ALERT
Executable private region: detected in synthetic telemetry
Remote image replacement executed: NO (simulation only)
Defensive report written: report.txt
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Process hollowing | Represent the technique as a sequence of simulated events and identify suspicious mismatches. |
| `NtReadFile` | Explain its role in reading file data; use ordinary file I/O for the safe simulation. |
| `NtWriteFile` | Explain its role in writing file data; do not use it to alter another process. |
| `NtUnmapViewOfSection` | Describe why unmapping an image view is a high-risk step; detect the event in synthetic telemetry only. |
| `ZwCreateSection` | Describe section-object creation and represent it as a simulated event. |
| `ZwMapViewOfSection` | Describe mapping a section into an address space and report suspicious mapping metadata without performing injection. |

### Levels

**🥉 Bronze: Spot the Mismatch** — Load a synthetic event file and flag an image path mismatch.

**🥈 Silver: Build the Timeline** — Correlate simulated section-map, memory-permission, and image-identity events into a timeline.

**🥇 Gold: Defend the Process** — Add a defensive report with detection rationale, false-positive caveats, and recommended telemetry; all process manipulation remains simulated.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Which combination of synthetic indicators caused your alert, and why is one indicator alone not definitive?
2. Modify the scenario so the expected and observed image identities match. Which alerts disappear?
3. What telemetry would help a defender distinguish legitimate section mapping from suspicious image replacement?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
