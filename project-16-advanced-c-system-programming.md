# Project 16: The Emergency Control Room 🚨
*Signals, alternate stacks, and nonlocal recovery*

### The story
A monitoring console watches a local simulation and must react when it receives a signal. You’re the control-room engineer, adding a signal handler, an alternate signal stack, and a carefully bounded recovery demonstration without pretending signal handlers are ordinary functions.

### What you'll build
Build `control_room` to demonstrate `sigaction()`, `sigaltstack()`, and a controlled `sigsetjmp()`/`siglongjmp()` recovery path. Use `signal()` only for a comparison with its portability caveats. Explain `setjmp()`/`longjmp()` and `sigreturn` conceptually; `sigreturn` is normally a kernel-mediated mechanism, not a portable application function to call directly. In signal handlers, do only async-signal-safe work and avoid jumping into a function whose stack frame has returned.

### Sample output

```text
$ ./control_room
Alternate signal stack installed.
Handler registered with sigaction().
Simulation running; press Ctrl-C to request shutdown.
Signal received; shutdown flag set.
Main loop noticed shutdown request.
Resources released. Control room closed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| `setjmp()` / `longjmp()` | Demonstrate nonlocal control flow in a contained example with valid live stack frames. |
| `sigsetjmp()` / `siglongjmp()` | Show the signal-mask-aware variants and document the `savesigs` behavior. |
| `signal()` | Compare its simpler interface with `sigaction()` and note portability/semantics concerns. |
| `sigaction()` | Install a handler with explicit flags and a defined signal mask. |
| `sigaltstack()` | Configure an alternate stack for signals that request it, such as with `SA_ONSTACK`. |
| `sigreturn` | Explain how the kernel restores interrupted context when a handler returns; do not call it as an ordinary portable C API. |

### Levels

**🥉 Bronze: Signal Flag** — Install a `sigaction()` handler that sets a `volatile sig_atomic_t` flag; let the main loop do the actual cleanup.

**🥈 Silver: Alternate Stack** — Add `sigaltstack()` and `SA_ONSTACK`, plus a contained `sigsetjmp()`/`siglongjmp()` demonstration.

**🥇 Gold: Systems Investigator** — Document async-signal-safety, signal-mask restoration, and the risks of jumping across stack frames or bypassing cleanup.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why should a signal handler generally set a flag rather than call `printf()` or free memory?
2. Trigger the controlled signal path and explain which code runs in the handler and which runs later in the main loop.
3. What can go wrong if `longjmp()` transfers control into a function that has already returned?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
