# Project 17: The Bytecode Costume Shop 🎭
*Encoding and decoding harmless byte arrays with XOR*

### The story
A bytecode costume shop disguises sample byte sequences so students can see how simple encoding works. You’re building a reversible transformation tool for inert test data, not a payload launcher.

### What you'll build
Build `byte_costume` to XOR an ordinary byte array with a one-byte or multi-byte key, then decode it by applying the same key again. Use a harmless sample string or marker bytes only; do not execute the encoded output as shellcode. Show the original, encoded, and decoded bytes in hexadecimal and verify exact round-trip equality.

### Sample output

```text
$ ./byte_costume
Input bytes: 43 41 54 21
Key bytes:   2A 7F
Encoded:     69 3E 7E 5E
Decoded:     43 41 54 21
Round trip: PASS
Note: XOR encoding is not encryption.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| XOR encoding/decoding | Apply XOR to each byte and verify that applying the same key stream again restores the original. |
| Multi-byte XOR keys | Repeat a key across the input using a clearly defined index rule; handle empty keys as invalid input. |
| Shellcode (safe representation) | Treat any byte sequence as inert data and never transfer control to it. |

### Levels

**🥉 Bronze: One Key** — Encode and decode a short harmless byte array with a single-byte XOR key.

**🥈 Silver: Key Ring** — Support multi-byte keys, hex output, and round-trip validation.

**🥇 Gold: Costume Inspector** — Demonstrate why repeating XOR keys leak patterns and add a detector/report that flags suspiciously repeating key cycles in your own generated examples.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why does applying XOR with the same key twice recover the original byte?
2. Try an empty key or an out-of-range key length. What input validation is needed?
3. Why should XOR encoding not be described as secure encryption?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
