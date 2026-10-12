# Project 10: Kitchen Rush 🍳
*A process-management restaurant simulator in C*

### The story
You run a busy restaurant. You are the Head Chef (the parent process). When orders arrive, you hire cooks (child processes) to prepare them. Cooks work independently, finish at different times, and sometimes one exceeds the time limit. At closing, every cook must be accounted for and no zombie process should remain.

### What you'll build
Build `kitchen`, which reads a small local order list, creates child processes, tracks completion, and prints an end-of-night report. A child can use `execvp()` to run a harmless local utility or a supplied helper program. Use `vfork()` only in a tightly constrained demonstration where the child immediately calls an exec-family function or `_exit()`; do not return from the child or call ordinary library routines after `vfork()` before exec/_exit.

### Sample output

```text
$ ./kitchen orders.txt
[Head Chef 4120] Kitchen is open!
[Head Chef] Hired cook 4121 for: pancakes
[Cook 4121] Boss is 4120. Starting pancakes...
[Head Chef] ✅ pancakes ready (cook 4121, exit 0)
[Head Chef] ⏰ soup is taking too long; sending cook 4122 home
[Head Chef] ❌ soup cancelled (signal 15)
--- End of Night Report ---
Dishes served: 1  Cancelled: 1  Unreaped children: 0
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| `fork()` | Hire a child process to handle an order. |
| `getpid()` | Print each cook’s process ID as its badge number. |
| `getppid()` | Have a cook report the PID of the process that launched it. |
| `execvp()` | Let a cook replace its process image with a harmless helper program. |
| `waitpid()` | Reap finished children and inspect their exit or signal status; use `WNOHANG` for nonblocking checks. |
| `kill()` | Send a signal to a timed-out child and then reap it. |
| `vfork()` | Run a separate, carefully constrained errand: child immediately execs or calls `_exit()`; the parent remains suspended until then. |

### Levels

**🥉 Bronze: Opening Night** — Fork one child per order, print PID/PPID, and wait for every child.

**🥈 Silver: Dinner Rush** — Use `execvp()`, nonblocking checks with `waitpid()`, and `kill()` for a child that exceeds a timeout.

**🥇 Gold: Michelin Star** — Add the `vfork()` errand runner under its strict rules, robust status reporting, and a final count proving all children were reaped.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens if the parent never calls `wait()` or `waitpid()` for a terminated child? Verify locally with process tools if available.
2. Why must the child after `vfork()` immediately call an exec-family function or `_exit()` rather than returning or modifying shared state?
3. If two cooks finish close together, how does your parent associate each PID with its order?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
