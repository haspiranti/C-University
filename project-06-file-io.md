# Project 6: The Archivist’s Lost Expedition 🧭
*A binary expedition log reader and writer*

### The story
An expedition returns with a fragile field log. You’re the archivist: preserve a record, reopen it, and prove that the saved data survived the journey. Some entries are structured binary records, so text-only assumptions won’t work.

### What you'll build
Build `expedition_log` that opens a file, writes a small array of fixed-layout records with `fwrite()`, closes it, reopens it, reads records with `fread()`, and prints a report. Check every file operation, distinguish end-of-file from read errors with `feof()`/`ferror()` where appropriate, and explain that raw structs may not be portable across compilers or machines.

### Sample output

```text
$ ./expedition_log fieldlog.bin
Writing 3 expedition records...
Saved: Ridge / 1420 m
Saved: River / 860 m
Saved: Camp / 510 m
Reopening fieldlog.bin...
Read 3 records successfully.
Highest point: Ridge (1420 m)
Archive sealed.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| File reading and writing | Save records to a named file and read them back for verification. |
| `fopen()` | Open the file in the correct binary mode (`wb` for writing, `rb` for reading) and check for `NULL`. |
| `fclose()` | Close each successfully opened stream and check for close-time write errors when relevant. |
| `fread()` | Read complete records and use its return count to detect short reads. |
| `fwrite()` | Write the intended number of records and verify the number written. |

### Levels

**🥉 Bronze: Save the Log** — Write one record and read it back.

**🥈 Silver: Full Expedition** — Handle multiple records, failed opens, short reads, and a clear report.

**🥇 Gold: Archive Specialist** — Add a versioned, field-by-field portable format or text export and test a missing or truncated file.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What is the difference between a short `fread()` result caused by end-of-file and one caused by an I/O error?
2. Truncate a copy of your log file and run the reader. How does your program respond?
3. Why is writing a C structure’s raw bytes not always a portable serialization format?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
