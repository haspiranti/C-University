# Project 4: Creature Lab: The Memory Menagerie 🧬
*Inspecting C data layouts in a tiny creature registry*

### The story
You manage a creature lab where each specimen has a name, an ID, and one active measurement: wingspan, shell width, or tail length. Your task is to catalog specimens and investigate how C arranges their data in memory.

### What you'll build
Build `memory_menagerie` using a `struct` for each specimen and a `union` for its mutually exclusive measurement. Print `sizeof` results and use `offsetof` to report member offsets. Make it clear that exact sizes and padding depend on the compiler, ABI, and target platform.

### Sample output

```text
$ ./memory_menagerie
Specimen: Glimmerwing (#17)
Active measurement: wingspan = 24.5
sizeof(char): 1
sizeof(struct Specimen): 40
sizeof(union Measurement): 8
offset(id): 0
offset(name): 4
offset(measurement): 32
Note: layout values are platform-dependent.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| `struct` | Group the specimen ID, name, and measurement into one record. |
| `union` | Store one of several measurement types in shared storage; track which member is active separately. |
| `sizeof` | Measure types and complete objects at runtime or compile time. |
| `offsetof` | Report the byte offset of a member within a structure using `<stddef.h>`. |
| Memory layout and padding | Compare member offsets and total size; explain alignment and padding without assuming a universal layout. |

### Levels

**🥉 Bronze: Catalog One** — Define a specimen `struct`, populate it, and print its fields and `sizeof`.

**🥈 Silver: Three Kinds of Creature** — Add the measurement `union`, a tag indicating the active member, and `offsetof` output.

**🥇 Gold: Layout Detective** — Compare two field orders or compile targets, document the observed padding, and explain why raw structure bytes are not a portable file format.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why can `sizeof(struct Specimen)` exceed the sum of the sizes of its members?
2. What happens if you read a different union member from the one you most recently wrote? Explain the limits of what your implementation guarantees.
3. Change the order of structure members. Which offsets or total sizes change on your machine, and why might another machine differ?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
