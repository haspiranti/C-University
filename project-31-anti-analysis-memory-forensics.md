# Project 31: The Page Table Detective 🔎
*A defensive report on CPU state and virtual memory*

### The story
A memory-forensics team has a fictional incident dump and a list of CPU-state observations. You’re the analyst, building a report that explains virtual-memory concepts and flags unsupported or suspicious claims instead of trying to bypass analysis.

### What you'll build
Build `page_table_report` using a supplied synthetic dataset to describe memory pages, page-table entries, and CPU register fields. Implement only safe, documented user-mode `cpuid`/timing demonstrations where supported. Treat control registers and privileged MSRs as offline data fields in the simulation; do not attempt to read or write `cr0`, `cr3`, `cr4`, `dr7`, `efer`, or privileged MSRs from user mode.

### Sample output

```text
$ ./page_table_report lab-dump.json
Virtual address: 0x00007FF600001000
Page size: 4096 bytes (scenario metadata)
PTE present: yes
PDE present: yes
PAE mode: enabled (scenario metadata)
CR3: reported by supplied dump; not read live
DR7 / EFER: offline fields only
Finding: mapping is internally consistent in this scenario.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Anti-VM / anti-debug / anti-analysis | Interpret synthetic indicators as evidence with uncertainty, not as a reason to evade monitoring. |
| `cpuid` / `rdtsc` | Collect supported CPU identification and a timing sample in ordinary user mode where available. |
| `rdmsr` / `wrmsr` | Document privileged MSR semantics; use supplied data instead of executing privileged instructions. |
| `cr3` / `cr4` / `cr0` / `dr7` / `efer` | Explain their architectural roles using offline scenario fields; do not read/write them directly from a normal user process. |
| Memory pages / PTE / PDE | Parse the synthetic virtual-memory records and check present bits, page sizes, and address consistency. |
| PAE / PSE / PAT | Explain their relationship to address translation and memory attributes as represented in the scenario data. |

### Levels

**🥉 Bronze: One Page** — Parse one synthetic page-table record and report page size and present status.

**🥈 Silver: Trace the Mapping** — Validate a chain of virtual-address translation records and identify inconsistencies.

**🥇 Gold: Forensics Report** — Add a clear confidence-rated findings report, explain architecture-specific assumptions, and document why live privileged register access is out of scope.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Modify a synthetic PTE so its present bit conflicts with the scenario’s mapping. Which validation catches the inconsistency?
2. Why can’t an ordinary user-mode program safely read or write control registers such as CR3 directly?
3. Which conclusions can you draw from the supplied memory metadata, and which would require additional evidence?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
