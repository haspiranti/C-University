# Project 3: The Recursive Recipe Vault 📜
*A recipe calculator powered by functions and recursion*

### The story
The Royal Bakery’s recipe vault stores recipes inside recipes: a festival cake needs batches of frosting, and frosting quantities scale with the number of cakes. You’re the apprentice engineer building a calculator that breaks a big order into manageable steps.

### What you'll build
Build `recipe_vault` with small functions for validating quantities, calculating ingredient totals, and computing factorials as a recursion exercise. Demonstrate declarations, parameters, return values, and `return`; make the recursive factorial function reject negative inputs and guard against integer overflow.

### Sample output

```text
$ ./recipe_vault
How many festival cakes? 3
Flour: 900 g
Sugar: 450 g
Eggs: 6
Choose a factorial demo number (0-12): 5
5! = 120
Recipe scaled. The ovens are ready!
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| Function declarations/prototypes | Declare each helper before it is called so the compiler knows its signature. |
| Parameters | Pass cake count or the number whose factorial is requested into a function. |
| Return values and `return` | Return calculated values and status information instead of relying on hidden global state. |
| Recursion | Implement factorial as `n * factorial(n - 1)` with a clear base case. |
| Factorial base case | Define `factorial(0) == 1`; reject negative input to avoid a recursion that never reaches the base case. |

### Levels

**🥉 Bronze: One Batch** — Write and call a scaling function that accepts a cake count and returns ingredient amounts.

**🥈 Silver: Festival Order** — Split calculations into focused functions and add recursive factorial with a correct base case.

**🥇 Gold: Master Baker** — Add input validation, overflow protection, and a small test mode covering 0, 1, typical values, and invalid values.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why is a function prototype useful when the function definition appears later in the file?
2. Remove or alter the factorial base case and run a small input. What happens, and why?
3. How does returning a value make a function easier to test than printing from inside it?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
