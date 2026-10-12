# Project 5: The Infinite Quest Board 🗺️
*A dynamically growing linked-list quest tracker*

### The story
Your adventuring party keeps accepting quests, and a fixed-size quest array is no longer enough. Build a quest board that can grow as new missions arrive and clean up every allocation when the tavern closes.

### What you'll build
Build `quest_board`, a singly linked list of dynamically allocated quests. Let the user add, list, and remove quests. Use `malloc()` for nodes and `free()` when a node is removed or the program exits; check allocation failures and update head pointers correctly.

### Sample output

```text
$ ./quest_board
1 Add quest  2 List quests  3 Remove first  4 Exit
Choice: 1
Quest title: Find the Moon Key
Added: Find the Moon Key
Choice: 1
Quest title: Rescue the Cartographer
Added: Rescue the Cartographer
Choice: 2
- Find the Moon Key
- Rescue the Cartographer
Choice: 4
Freed 2 quest nodes. Board closed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| `malloc()` | Allocate each quest node at the time the user adds a quest; check for `NULL`. |
| `free()` | Release removed nodes and every remaining node during shutdown. |
| Dynamic allocation | Size nodes with `sizeof *node` and never use a node after freeing it. |
| Linked-list nodes and pointers | Connect each node to the next; correctly handle empty lists, the head node, and tail traversal. |

### Levels

**🥉 Bronze: Pin the First Quest** — Allocate and display one node, then free it.

**🥈 Silver: A Growing Quest Board** — Add multiple quests, traverse the list, remove the head, and free all remaining nodes.

**🥇 Gold: Guild Master** — Support removing a quest by ID, report allocation failures cleanly, and use a memory checker such as AddressSanitizer or Valgrind if available.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What bug appears if you call `free(node)` before saving the pointer to the next node?
2. Deliberately introduce a leak in a local test branch and use a memory checker to identify it. What evidence does the tool show?
3. How does a linked list behave differently from a fixed-size array when adding an item?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
