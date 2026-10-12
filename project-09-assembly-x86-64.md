# Project 9: The Tiny Robot Assembly Line 🤖
*Learning x86-64 by tracing a tiny program*

### The story
A tiny factory robot follows extremely literal instructions. You’re writing its instruction card in x86-64 assembly and then comparing the register and stack changes with a C version of the same calculation.

### What you'll build
Build a small x86-64 assembly program that computes a sum in a loop, branches when a counter reaches a limit, calls a helper function, and returns a result according to the platform’s calling convention. Include a register/stack trace in your README. Use the ABI for your actual platform (for example, System V AMD64 on many Linux systems).

### Sample output

```text
$ ./robot_sum
Input limit: 5
Trace: counter=1 sum=1
Trace: counter=2 sum=3
Trace: counter=3 sum=6
Trace: counter=4 sum=10
Trace: counter=5 sum=15
Helper returned: 15
Robot halted normally.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Registers | Use general-purpose registers for the counter, running sum, arguments, and return value. |
| Stack | Explain return addresses, saved registers, and stack alignment around calls. |
| Calling convention | Pass arguments and return values using the ABI rules for your platform. |
| Basic instructions | Use moves, arithmetic, comparisons, and a return instruction. |
| Function calls | Call a helper and preserve any caller-saved values you still need. |
| Loop and branch | Implement the repeated sum with a conditional branch back to the loop. |

### Levels

**🥉 Bronze: Move and Add** — Write a tiny assembly routine that adds two values and returns the result to C.

**🥈 Silver: Robot Loop** — Add a loop, a conditional branch, and a helper call.

**🥇 Gold: Factory Inspector** — Compare compiler-generated assembly for a C equivalent and explain register allocation, stack use, and one optimization you observe.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Which registers carry function arguments and the return value under your chosen ABI?
2. Change the loop condition so it never becomes false. What behavior do you see, and how did you diagnose it?
3. What must a function preserve or restore according to the calling convention you used?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
