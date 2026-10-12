# Project 21: The Function Detour Test Track 🏁
*A safe function-pointer and detour simulation*

### The story
A racing team wants to time a function without rewriting the whole program. You’re the instrumentation engineer, comparing a normal function pointer, a wrapper, and a trampoline-like call path in code you own.

### What you'll build
Build `detour_track` with a local function, a function pointer, and a wrapper that records calls before invoking the original function. Use `GetProcAddress()` to resolve an exported function from a DLL you control. Explain inline hooking, detours, and trampolines conceptually, but do not patch executable code pages or hook unrelated processes.

### Sample output

```text
C:\Lab> detour_track.exe
Resolved function: lap_time
Wrapper: call #1
Original lap_time(3) -> 300 ms
Wrapper: call #2
Original lap_time(5) -> 500 ms
Total calls recorded: 2
Code pages modified: 0
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Inline hooking (concept) | Describe how an inline hook redirects control flow; keep implementation to a normal wrapper in owned code. |
| Detour | Route calls through a wrapper that logs arguments and results. |
| Trampoline (concept) | Model a trampoline as a normal function that calls the original implementation, without modifying machine code. |
| `GetProcAddress()` | Resolve a known exported function from a DLL the student builds. |
| Function pointer | Store and call a function through a correctly typed pointer. |

### Levels

**🥉 Bronze: Timed Lap** — Call a function through a function pointer.

**🥈 Silver: Wrapper Detour** — Add a wrapper that records call count and delegates to the original function.

**🥇 Gold: Instrumentation Engineer** — Add timing and error handling, then write a defensive note about code integrity, control-flow monitoring, and the risks of patching executable memory.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens if your function pointer has the wrong signature? Why is that undefined or otherwise unsafe behavior?
2. Change the wrapper so it accidentally calls itself instead of the original. What happens?
3. What additional risks appear when a detour modifies executable bytes instead of using an ordinary wrapper?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
