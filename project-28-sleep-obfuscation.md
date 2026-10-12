# Project 28: The Night-Shift Timing Lab 🌙
*Comparing sleep calls and measuring elapsed time*

### The story
A night-shift robot must pause between rounds, but its clock readings sometimes differ from the requested delay. You’re the timing engineer, comparing sleep APIs and measuring actual elapsed time without hiding activity from monitoring.

### What you'll build
Build `night_shift` to wait for requested intervals using `sleep()`, `usleep()` where available, and `nanosleep()`, measuring elapsed time with `clock_gettime()` and `gettimeofday()`. Explain that sleep duration is a minimum-ish scheduling request, not a precise guarantee, and that interrupted sleeps may need to resume using the remaining time.

### Sample output

```text
$ ./night_shift
Requested delay: 500 ms
sleep(): requested 1 s, observed 1.001 s
usleep(): requested 200 ms, observed 0.203 s
nanosleep(): requested 500 ms, observed 0.501 s
Wall-clock sample: 2026-10-11 20:00:00
Timing varies with scheduler load.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Sleep obfuscation (concept) | Discuss how sleep patterns can be observed by defenders; do not implement concealment or evasion. |
| `sleep()` | Demonstrate whole-second delay behavior. |
| `usleep()` | Demonstrate microsecond-requested delay where supported, noting portability/deprecation concerns. |
| `nanosleep()` | Request a higher-resolution delay and handle interruption/remaining time. |
| `clock_gettime()` | Measure elapsed time with an appropriate clock such as `CLOCK_MONOTONIC`. |
| `gettimeofday()` | Compare wall-clock readings and explain that wall time can jump. |

### Levels

**🥉 Bronze: One Pause** — Measure one delay with `nanosleep()` and a monotonic clock.

**🥈 Silver: Clock Comparison** — Compare several delay APIs and handle interruptions and errors.

**🥇 Gold: Scheduler Scientist** — Run repeated trials, report min/median/max, and explain why timing jitter is normal and why timing-based detection can be noisy.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Interrupt a `nanosleep()` with a signal in a controlled test. What does the return value and remaining-time structure tell you?
2. Compare `CLOCK_MONOTONIC` elapsed time with `gettimeofday()` wall time. Why are they meant for different jobs?
3. Why can the observed sleep duration be longer than the requested duration?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
