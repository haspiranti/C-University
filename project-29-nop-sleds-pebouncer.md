# Project 29: The Instruction Playground 🛝
*Tracing control flow without exploit payloads*

### The story
A tiny CPU simulator runs a printed instruction card, and you’re the instructor explaining how control flow moves through memory. You’ll model instruction behavior with a safe trace rather than constructing an exploit or a working payload.

### What you'll build
Build `instruction_playground` as a trace table or a small emulator for a carefully limited set of x86-64 instructions. Show how `nop`, `jmp`, `push`, `pop`, `ret`, `call`, and `lea` affect the modeled instruction pointer, stack, and registers. Treat NOP sleds and the course-specific term “PEbouncer” as concepts to research with your instructor; do not build an exploit or bypass for real software protections.

### Sample output

```text
$ ./instruction_playground demo.trace
IP=0000  lea rax, [data]   rax <- 0x2000
IP=0001  push rax         stack depth=1
IP=0002  pop rbx          rbx <- 0x2000
IP=0003  nop               state unchanged
IP=0004  call helper       return address saved
IP=0008  ret               IP restored
Trace complete. No executable memory modified.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| NOP sleds / `nop` | Show no-op instructions in a control-flow trace and explain their historical exploit context. |
| `jmp` | Change the modeled instruction pointer to a valid label. |
| `push` / `pop` | Model stack growth and shrinkage with bounds checks. |
| `ret` / `call` | Model saving and restoring a return address. |
| `lea` | Compute an effective address without dereferencing it. |
| PEbouncer | Confirm the intended course-specific tool/concept with the instructor; document it rather than implementing a bypass. |
| PIC / IP | Explain position-independent code and instruction-pointer-relative addressing conceptually. |

### Levels

**🥉 Bronze: Trace Three Instructions** — Model `nop`, `lea`, and a conditional or unconditional branch.

**🥈 Silver: Stack Walk** — Add `push`, `pop`, `call`, and `ret` with a bounded simulated stack.

**🥇 Gold: Control-Flow Auditor** — Add malformed-trace detection and a defensive explanation of control-flow protections and why a trace simulator is safer than an exploit.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens if `ret` is executed with an empty simulated stack? How does your emulator catch it?
2. Change a jump target to an invalid instruction index. What error should the trace report?
3. Why is understanding NOP sleds useful for defense, and why does this project avoid creating a real exploit?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
