# Project 18: The Windows Binary Museum 🏛️
*A read-only Portable Executable file explorer*

### The story
A digital museum receives Windows executable files and needs a catalog card for each one. You’re the archivist, writing a read-only parser that identifies headers and tables without loading or executing the file.

### What you'll build
Build `pe_museum`, a read-only PE parser for files you provide locally. Parse the DOS header, locate the NT headers using `e_lfanew`, list section headers, and report import/export directory metadata and relocation entries when present. Validate every offset and length against the file size; never cast untrusted file bytes directly to a structure without checking bounds, alignment, and format assumptions.

### Sample output

```text
$ ./pe_museum sample.exe
DOS signature: MZ
PE signature: PE\0\0
Machine: AMD64
Sections: 5
  .text  RVA=0x1000  RawSize=0x2A00
  .rdata RVA=0x4000  RawSize=0x0C00
Import directory: present
Export directory: absent
Relocations: present
Parse completed with no out-of-bounds reads.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| PE header | Validate the DOS signature and use the `e_lfanew` offset to locate the NT headers. |
| Section table | Read each section’s name, RVA, raw offset, and size with bounds checks. |
| Import table | Report imported DLLs and symbols from a valid import directory. |
| Export table | Report exported names and ordinals when the export directory exists. |
| Relocations | Inspect base-relocation blocks as metadata; do not apply them to execute a file. |
| `IMAGE_DOS_HEADER` | Use the Windows SDK definition or a carefully documented layout for the DOS header. |
| `IMAGE_NT_HEADERS` | Handle PE32 and PE32+ variants rather than assuming one architecture. |
| `IMAGE_SECTION_HEADER` | Parse section metadata and validate raw ranges before reading section bytes. |

### Levels

**🥉 Bronze: Read the Cover** — Identify MZ/PE signatures and print architecture and section count for a valid sample.

**🥈 Silver: Gallery Catalog** — List sections and summarize import/export directory metadata with strict bounds checks.

**🥇 Gold: Museum Security Review** — Add PE32/PE32+ support, malformed-file tests, and a report explaining why the parser treats the file as untrusted input.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. What happens when `e_lfanew` points beyond the end of the file? Show how your parser rejects it.
2. Why can the in-memory layout of Windows SDK structures differ from the raw on-disk layout or from your host compiler’s assumptions?
3. Create a truncated copy of a sample PE file. Which validation catches the problem first?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
