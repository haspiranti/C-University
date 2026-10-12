# Project 1: The Midnight Snack Shack 🥪
*A menu-driven snack stand built with basic C*

### The story
You’re running the Midnight Snack Shack during a busy game night. Customers need to choose a snack, enter quantities, and see a clear bill. Your job is to keep the menu moving without letting invalid choices or weird quantities ruin the order.

### What you'll build
Build `snack_shack`, a terminal ordering program that displays a menu, reads a customer’s choice and quantity, calculates the total, applies a simple discount with `if/else`, and loops so several orders can be handled. Use `switch` for menu selection and report the final takings when the cashier closes the stand.

### Sample output

```text
$ ./snack_shack
=== MIDNIGHT SNACK SHACK ===
1. Pretzel  $3.00
2. Nachos   $5.00
3. Cocoa    $2.00
4. Close register
Choose: 2
Quantity: 2
Added 2 Nachos: $10.00
Another order? (1=yes, 0=no): 1
Choose: 3
Quantity: 1
Added 1 Cocoa: $2.00
Another order? (1=yes, 0=no): 0
Orders: 2  Items: 3  Total: $12.00
Register closed. Thanks!
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Syntax and program structure | Organize the program into readable statements, blocks, and a `main` function. |
| Data types and variables | Represent menu choices, quantities, item counts, prices, and totals with suitable types. |
| Operators | Calculate line totals, grand totals, and optional discounts. |
| `if` / `else` | Reject zero or negative quantities and apply a discount when the order meets your rule. |
| `switch` | Translate the selected menu number into a snack and its price. |
| `while` | Keep taking orders until the customer or cashier chooses to stop. |
| `for` | Print the numbered menu or summarize a known number of items. |
| `printf()` | Display the menu, prompts, receipt, and final totals. |
| `scanf()` | Read menu choices and quantities; check its return value before using input. |

### Levels

**🥉 Bronze: First Shift** — Print the menu, accept one item and quantity, and calculate a correct total.

**🥈 Silver: Game-Night Rush** — Use `switch`, `if/else`, and a loop to process multiple orders and reject invalid input.

**🥇 Gold: Legendary Snack Shack** — Add a discount rule, itemized receipt, and robust handling of non-numeric input without getting stuck in an input loop.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Which C data types did you choose for quantities and prices, and what trade-offs did you make?
2. Deliberately enter a letter when the program expects a number. What happens to `scanf()` and how did you recover safely?
3. Trace one order by hand and show how the operators produce the final total.

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
