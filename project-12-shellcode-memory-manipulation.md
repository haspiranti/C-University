# Project 12: The Executable Memory Sandbox 🧪
*A controlled memory-permission experiment*

### The story
You’re testing a tiny memory lab, not attacking a machine. Your program allocates a private page, writes a harmless byte pattern into it, changes page permissions, and observes what the operating system allows. The point is to understand memory protections and why executable memory deserves careful handling.

### What you'll build
Build `memory_lab` to allocate a page with `mmap()`, fill it with a harmless data pattern, read it back, and demonstrate permission changes with `mprotect()`. For safety and portability, do not load or execute real shellcode: treat the bytes as data and use a normal C function to demonstrate program control flow. Explain page alignment and always release mappings with `munmap()`.

### Sample output

```text
$ ./memory_lab
Allocated 4096-byte private mapping
Wrote test pattern: 90 90 CC 41
Read-back matches: yes
Changed mapping to read-only: success
Write test skipped: mapping is read-only
Mapping released. Memory lab complete.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Shellcode loading (conceptual) | Represent a tiny byte sequence as data and inspect it; do not execute injected payload bytes. |
| `mmap()` | Allocate a page-sized private mapping for the experiment. |
| `mprotect()` | Change page permissions and report errors from the operating system. |
| Memory read and write | Write a known byte pattern and verify it by reading the mapped bytes. |
| `memset()` | Initialize the mapping with a known pattern. |
| `memcpy()` | Copy a test sequence into the mapping and compare it with a separate buffer. |

### Levels

**🥉 Bronze: Memory Postcard** — Allocate memory, fill it with a pattern, verify the bytes, and unmap it.

**🥈 Silver: Permission Inspector** — Switch between read/write and read-only permissions, checking every return value.

**🥇 Gold: Memory Defender** — Add a clear permission-state report and a README section explaining W^X (write XOR execute), ASLR, and why this lab deliberately never executes shellcode.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What error do you get if you request an invalid protection change or invalid address range?
2. Try to write only in a separate test after making the page read-only. Why is deliberately crashing the main program a poor test strategy, and how could a subprocess-based test isolate it?
3. Why is separating writable memory from executable memory a useful defensive design?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
