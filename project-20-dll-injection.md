# Project 20: The Plugin Security Workshop 🧰
*Understanding DLL loading through a local plugin host*

### The story
A desktop app accepts plugins, but the team needs to understand exactly when a library is loaded and which functions it exposes. You’re building a controlled plugin host and a defensive report—not injecting code into unrelated processes.

### What you'll build
Build a Windows program that loads a DLL you compile yourself into its own process using `LoadLibrary()`, resolves a documented plugin entry point with `GetProcAddress()`, calls it, and unloads it with `FreeLibrary()`. Explain how cross-process DLL injection differs, but do not implement injection into a separate process.

### Sample output

```text
C:\Lab> plugin_host.exe demo_plugin.dll
Loaded owned plugin: demo_plugin.dll
Entry point found: plugin_start
Plugin says: Hello from the lab plugin!
Plugin completed successfully.
Library unloaded.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| DLL loading concept | Demonstrate dynamic library loading inside the program that owns the plugin. |
| `LoadLibrary()` | Load the student-built DLL and check the returned module handle. |
| `GetProcAddress()` | Resolve a known exported function and validate the result before calling it. |
| `FreeLibrary()` | Release the module handle after all calls and pointers into the DLL are no longer used. |

### Levels

**🥉 Bronze: Load a Plugin** — Build a DLL with one exported function and load it into the host process.

**🥈 Silver: Plugin Contract** — Add error handling, version checks, and safe cleanup when an export is missing.

**🥇 Gold: Plugin Defender** — Add an allowlist or signature/hash check for plugins and explain why loading a DLL into your own process is different from cross-process injection.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens if `GetProcAddress()` returns `NULL` and the program calls the result anyway?
2. Rename or remove the expected export and run the host. How does your error path behave?
3. What security checks would you add before loading a third-party plugin?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
