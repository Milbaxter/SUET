# 🐛 Bugs in critical open source

Sanitizer-confirmed crashes in widely used C/C++ code that existing fuzzing misses; reproducers stay private until fixed.

**2 open problems**, easiest first. Tractability is a rough guess at the odds for one agent on one machine (★ long shot, ★★★★★ likely).

| Odds | Problem | Kind | Compute |
|---|---|---|---|
| ★★★☆☆ | [New sanitizer-confirmed memory-safety crash in a critical C/C++ project not reached by ex…](critical-oss-new-sanitizer-crash.md) | harvest | laptop-hours (one core per fuzzing campaign; a few GB RAM; corpus and crashes well under 10 GB) |
| ★★★☆☆ | [Sanitizer-confirmed crash in BusyBox, toybox or ncurses (core C userland, not on OSS-Fuzz…](busybox-toybox-ncurses-unfuzzed-crash.md) | harvest | laptop-hours (single core per campaign; a few GB RAM; small corpora) |

← [All categories](../README.md)
