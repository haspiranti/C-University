# Project 23: The Windows Settings Museum 🗄️
*A safe registry reader with a disposable test key*

### The story
A Windows application stores preferences in the Registry. You’re the settings archivist, building a tool that reads known values and changes only a disposable key created for this assignment.

### What you'll build
Build `registry_museum` to read a small set of values from a course-owned test key under `HKEY_CURRENT_USER\Software\CProjectLab`. Use `RegOpenKeyEx()`, `RegQueryValueEx()`, and `RegSetValueEx()` to inspect and update your own test values. Do not modify system-wide or security-sensitive keys; document the data type and buffer-size behavior of every query.

### Sample output

```text
C:\Lab> registry_museum.exe
Test key: HKCU\Software\CProjectLab
Theme before: blue
Query status: success
Setting theme to: amber
Write status: success
Read-back theme: amber
Only the course test key was changed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| `HKEY_LOCAL_MACHINE` | Explain its machine-wide scope; do not write to it in this lab. |
| `HKEY_CURRENT_USER` | Use this user-scoped hive for the disposable practice key. |
| `RegOpenKeyEx()` | Open the course-owned key with only the access rights needed. |
| `RegQueryValueEx()` | Read a value, handle type/size metadata, and retry safely if the buffer is too small. |
| `RegSetValueEx()` | Write a known test value only under the disposable course key. |

### Levels

**🥉 Bronze: Read the Label** — Create or open the test key and query one value.

**🥈 Silver: Update the Display** — Write a test value, read it back, and handle missing values or unexpected types.

**🥇 Gold: Registry Steward** — Add a reset/cleanup option that removes only values your program created, and document why least-privilege access matters.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens if the queried value is a different registry type than you expected?
2. Change the test value to a longer string than your original buffer. How does your code handle the required size?
3. Why does the project avoid writing to `HKEY_LOCAL_MACHINE`?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
