# Project 15: The Galactic Cargo Compressor 📦
*Comparing compression formats on cargo manifests*

### The story
A space freighter has limited cargo bandwidth. You’re the manifest engineer, comparing compression tools to see which one shrinks a repetitive log the most and which one restores the exact original bytes.

### What you'll build
Build `cargo_compress`, a benchmark wrapper or comparison report for available compressors. Include zlib, gzip, bzip2, xz/LZMA, zstd, LZO, Snappy, LZ4, and the course-specified `snoopy` entry only after confirming what library/tool the syllabus means by that name. Use each library’s documented API or invoke installed command-line tools with fixed local input. Record compressed size, elapsed time, and round-trip correctness.

### Sample output

```text
$ ./cargo_compress cargo.log
Input size: 120000 bytes
Format       Output bytes   Round trip
zlib              18420     OK
gzip              18438     OK
bzip2             15110     OK
xz                10942     OK
zstd              12600     OK
lz4               29850     OK
Best size: xz   Fastest observed: lz4
All verified outputs match the original.
```

### Required ingredients

| Required concept / function | Role in the project |
|---|---|
| zlib | Compress/decompress a buffer or stream with the zlib API. |
| gzip | Compare the gzip wrapper/format and verify decompressed bytes. |
| bzip2 | Include bzip2 if its library or command-line tool is installed. |
| xz / LZMA | Compare the xz container and LZMA-family compression settings. |
| zstd | Benchmark Zstandard using documented compression/decompression APIs. |
| LZO | Include LZO when the dependency is available and initialized correctly. |
| Snappy | Measure Snappy compression and decompression with its documented API. |
| LZ4 | Compare LZ4’s speed/ratio trade-off. |
| Snoopy | Confirm the intended library or tool with your instructor before implementing this item; do not assume it is a compression format. |

### Levels

**🥉 Bronze: Pack One Crate** — Compress and decompress one local text file with one available library and compare bytes.

**🥈 Silver: Cargo Trials** — Compare at least four formats with size and timing results, verifying each round trip.

**🥇 Gold: Fleet Engineer** — Support all available course-approved formats, report settings and versions, and explain why the smallest output is not always the best choice.

### Creative freedom
Re-theme the project however you like—arcade, fantasy guild, racing team, space station, or something entirely yours—as long as every required function or concept still has a visible job in the program. Explain your function-to-feature mapping in the README. For security-focused topics, keep all experiments local, owned, and deliberately controlled; do not target real systems or third parties.

### Reflection questions
Answer all three in your `README.md`.

1. Why can a highly compressible text log produce a much smaller file than already-compressed data?
2. Deliberately corrupt a compressed output and run the decompressor. What error or mismatch does your program detect?
3. What does your benchmark measure, and what factors could make the timing unfair or non-repeatable?

### Grading rubric

| Area | Points |
|---|---:|
| Correctness and completion at the level attempted | 40 |
| Correct, purposeful use of each required concept | 25 |
| Code quality, naming, comments, and error handling | 15 |
| Reflection answers, including the deliberate-break experiment | 15 |
| Creativity and clarity of the theme | 5 |
| **Total** | **100** |
