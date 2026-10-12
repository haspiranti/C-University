# Project 26: The Lab Instrumentation Detector 🧭
*A transparent environment-checking exercise*

### The story
A test application behaves differently under a microscope, and your job is to understand what environmental clues a program can observe. You’re the lab engineer, collecting transparent diagnostic signals and documenting how unreliable each clue can be.

### What you'll build
Build `environment_report` that records benign timing measurements and, where supported, queries CPU identification information. Treat VM/debugger detection as probabilistic and do not attempt to evade security products or conceal activity. Privileged instructions such as `rdmsr` and `wrmsr` can fault or require kernel privileges; discuss them in the report or use a supplied emulator rather than executing them in ordinary user mode.

### Sample output

```text
$ ./environment_report
CPU vendor: GenuineIntel
Timing sample collected: 1200 ticks (illustrative)
Debugger indicator: not determined
Virtualization indicator: possible (not conclusive)
Privileged MSR access: not attempted
Conclusion: environment clues are not proof.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Anti-VM / anti-debug / anti-analysis | Report possible indicators transparently and explain false positives; do not use them to evade analysis. |
| `cpuid` | Read supported CPU feature/vendor information where the platform and compiler permit. |
| `rdtsc` | Measure a short timing interval where supported, documenting serialization and measurement noise. |
| `rdmsr` / `wrmsr` | Explain their privileged nature and risks; do not execute them from ordinary user-mode code. |

### Levels

**🥉 Bronze: System Clues** — Print CPU vendor/features and a clearly labeled timing sample.

**🥈 Silver: Evidence Report** — Compare several benign indicators and describe their confidence and limitations.

**🥇 Gold: Analyst’s Notes** — Add repeatable measurements and a false-positive analysis; document why the tool reports evidence rather than trying to hide from analysis.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Repeat the timing test under different workloads. How much does the result vary, and why?
2. What happens if you treat a single VM indicator as proof? Give a realistic false-positive example.
3. Why can `rdmsr` or `wrmsr` fault in user mode, and how did you keep the lab safe?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
