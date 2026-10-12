# Project 11: The Bitwise Treasure Map 🧩
*A binary flag and endianness explorer*

### The story
A treasure map encodes doors, traps, and keys in compact bit flags. You’re the map’s decoder, building a tool that converts decimal values to hex, toggles flags, and shows how bytes appear in memory on the current machine.

### What you'll build
Build `bit_map` to set, clear, test, and toggle flags using bitwise operators; show left and right shifts with unsigned values; and print numbers in decimal and hexadecimal. Inspect a multi-byte integer’s byte order through an `unsigned char` view of its object representation, then identify whether the host is little- or big-endian.

### Sample output

```text
$ ./bit_map
Flags start: 0x05 (decimal 5)
Set KEY flag: 0x0D
Clear TRAP flag: 0x09
Toggle SECRET flag: 0x19
KEY flag set? yes
0x03 << 2 = 0x0C
Bytes of 0x12345678: 78 56 34 12
Host byte order: little-endian
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Bitwise operators | Use `&`, `\|`, `^`, and `~` to inspect and modify flags. |
| Left and right shift | Shift unsigned values to demonstrate bit positions without relying on undefined behavior from invalid shifts. |
| XOR | Toggle selected flags and demonstrate that XORing the same mask twice restores the original value. |
| `&` and `\|` | Test, clear, or set chosen flag bits. |
| `~` | Show bitwise complement while explaining that the result depends on the integer width and type. |
| Endianness | Inspect bytes through an `unsigned char` pointer to the object representation. |
| Hex and decimal | Print the same value with `%x`/`%X` and decimal format specifiers. |

### Levels

**🥉 Bronze: Find the Key** — Print a value in decimal and hex and test one flag with `&`.

**🥈 Silver: Decode the Map** — Add set/clear/toggle operations, shifts, and a multi-flag display.

**🥇 Gold: Bitwise Cartographer** — Detect host byte order at runtime and show the byte sequence of a 32-bit value; explain why endianness differs from the order of bits within a byte.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why should bit masks usually use unsigned integer types?
2. Try shifting by the width of the type or using a negative signed value in a shift test. What rule did you violate, and how did you correct it?
3. How can the same integer value be stored with different byte sequences on different architectures?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
