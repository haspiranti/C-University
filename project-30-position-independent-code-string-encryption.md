# Project 30: The Wandering Code Post Office ✉️
*Relocation concepts and reversible string transforms*

### The story
A traveling post office sends the same tiny data-processing routine to different stations, where it should work regardless of where it is placed. You’re the portability engineer, studying relative addressing and reversible string transforms with ordinary data.

### What you'll build
Build `wandering_post` with a normal C routine that operates independently of fixed global addresses, inspect its compiler-generated assembly, and implement reversible XOR string encoding for sample strings. Compare AES conceptually or through a vetted library; use MD5/SHA-1/SHA-256/SHA-512 only as digest demonstrations, with MD5/SHA-1 marked legacy. Treat `ip`, `sp`, `bp`, `si`, `di`, and `r8`–`r15` as architecture-specific register names and never execute an encoded payload.

### Sample output

```text
$ ./wandering_post
String: meet at station seven
XOR encoded: 47 4A 4A 59 ...
Decoded: meet at station seven
Round trip: PASS
Position-independence review: no fixed absolute data address found in selected routine
Digest demo: SHA-256 calculated
No payload executed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Position-independent code (PIC) | Inspect a compiled routine and explain how relative addressing and relocations affect placement. |
| IP / SP / BP / SI / DI / R8–R15 | Identify these x86-64 register roles in the assembly listing, noting that exact usage depends on the ABI and compiler. |
| String encryption / XOR | Encode and decode ordinary strings with a reversible XOR transform; explain that this is obfuscation, not secure encryption. |
| AES / RC4 | Compare a vetted AES mode with legacy RC4 conceptually; do not use RC4 for new protection. |
| MD5 / SHA-1 / SHA-256 / SHA-512 | Compute digest examples and distinguish hashing from encryption; label MD5/SHA-1 as legacy. |

### Levels

**🥉 Bronze: Traveling String** — Encode/decode a string with XOR and verify the round trip.

**🥈 Silver: Assembly Postcard** — Inspect assembly for a selected routine and explain its register and address references.

**🥇 Gold: Portability Engineer** — Compare builds or compiler options, document relocations/PIC behavior, and replace the toy string transform with a library-based authenticated encryption demo.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why does XOR encoding not provide confidentiality even if the output looks unreadable?
2. Inspect your routine’s assembly and identify one register used for an address or loop counter. What changes between builds?
3. What is the difference between a hash digest, encryption, and position-independent code?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
