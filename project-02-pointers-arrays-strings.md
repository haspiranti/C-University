# Project 2: Message in a Bottle 🏴‍☠️
*A pirate message-repair workshop for arrays, pointers, and strings*

### The story
A pirate crew has recovered a water-damaged message. You’re the ship’s codebreaker, and you must inspect its characters, repair a phrase, and assemble a readable transmission before the tide carries the bottle away.

### What you'll build
Build `bottle_code`, which stores a message in a character array, walks through it using both array indexing and pointer arithmetic, measures it with `strlen()`, copies a safe-sized phrase with `strcpy()`, and appends a suffix with `strcat()`. Print the original and repaired messages and show how each operation changes the string.

### Sample output

```text
$ ./bottle_code
Recovered: meet at dawn
Length: 11
Pointer scan: m e e t   a t   d a w n
Copied clue: meet at dawn
Final transmission: meet at dawn, bring the map
Transmission length: 27
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Pointers and pointer arithmetic | Walk through the character array by advancing a `char *` and stop at the terminating `\0`. |
| Arrays | Store the original message and any working buffers with explicitly known capacities. |
| Strings and `\0` | Treat C strings as null-terminated character sequences, not length-tracked objects. |
| `strlen()` | Report the message length excluding the terminating null byte. |
| `strcpy()` | Copy the message into a destination buffer proven large enough for the text plus `\0`. |
| `strcat()` | Append a suffix only after verifying the destination has enough remaining capacity. |

### Levels

**🥉 Bronze: Bottle Found** — Print a message and its `strlen()` length; inspect characters using array indexing.

**🥈 Silver: Decode the Clue** — Use pointer arithmetic to traverse the message, copy it, and append a suffix.

**🥇 Gold: Captain’s Cipher Desk** — Support several messages and demonstrate a safe capacity check before every copy or append; explain why `strcpy()` and `strcat()` do not check buffer sizes.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What is the difference between the address stored in a pointer and the character stored at that address?
2. Try appending a suffix that will not fit in the buffer. What goes wrong, and how does your capacity check prevent it?
3. Why does `strlen()` not include the terminating null byte?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
