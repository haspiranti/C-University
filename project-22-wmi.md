# Project 22: The Windows Spaceship Status Console 🛰️
*A read-only Windows inventory report using WMI*

### The story
Your spaceship’s maintenance crew needs a quick status report before launch. You’re the systems officer, collecting basic operating-system and hardware information through Windows Management Instrumentation (WMI).

### What you'll build
Build a Windows C++ helper or C program using a small C++ COM/WMI bridge to query local read-only system classes and print a status report. Because WMI is exposed through COM and is not a native plain-C API, document the interop layer or use a supplied course wrapper. Query only the local machine and handle COM initialization, security, and cleanup correctly.

### Sample output

```text
C:\Lab> ship_status.exe
Computer: LAB-DESKTOP
OS: Microsoft Windows 11
BIOS vendor: Example Vendor
Logical processors: 16
WMI query status: OK
No settings changed; inventory only.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| WMI | Use Windows Management Instrumentation for local system inventory. |
| `Win32_Process` | List a limited set of process names and IDs, avoiding sensitive command-line data in the default report. |
| `Win32_ComputerSystem` | Read the system manufacturer/model and computer name. |
| `Win32_OperatingSystem` | Read OS caption and version information. |
| `Win32_BIOS` | Read BIOS manufacturer and version metadata. |
| `Win32_LogicalProcessor` | Report logical processor information, or explain the related processor class/query used by your Windows version. |

### Levels

**🥉 Bronze: Launch Checklist** — Query local OS and computer-system metadata.

**🥈 Silver: Full Status Board** — Add BIOS, processor, and process inventory with COM/WMI error handling.

**🥇 Gold: Fleet Engineer** — Add a clean structured output format, timeouts, and a note on data minimization and WMI permissions.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens when WMI returns no rows or an access error? How does your program distinguish these cases?
2. Deliberately query a class/property that is unavailable on your system. What diagnostic does your program show?
3. Why should an inventory tool collect only the system information it actually needs?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
