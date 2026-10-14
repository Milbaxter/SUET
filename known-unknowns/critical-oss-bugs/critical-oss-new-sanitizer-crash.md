# New sanitizer-confirmed memory-safety crash in a critical C/C++ project not reached by existing OSS-Fuzz fuzzing

🐛 **Bugs in critical open source** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours (one core per fuzzing campaign; a few GB RAM; corpus and crashes well under 10 GB) · open as of 2026-10-14

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

Google's OSS-Fuzz (github.com/google/oss-fuzz, continuous fuzzing started 2016 by the OSS-Fuzz team; the projects/ directory holds one subfolder per integrated project, >1000 of them on 2026-10-14, with 385+ entries omitted from GitHub's first listing page) fuzzes the C/C++ projects that opted in, and finds thousands of bugs a year with libFuzzer (Kostya Serebryany and the LLVM sanitizer-coverage authors), AFL++ (Andrea Fioraldi, Dominik Maier, Heiko Eissfeldt, Marc Heuse) and Honggfuzz, under AddressSanitizer / UndefinedBehaviorSanitizer / MemorySanitizer (the LLVM/Clang sanitizer team). Two large gaps remain on 2026-10-14. (1) Many widely-deployed, parser-heavy C/C++ projects are NOT integrated into OSS-Fuzz at all: on 2026-10-14 the path projects/<name>/project.yaml returns HTTP 404 for, among others, busybox, toybox, ncurses, mutt, htop, nanomsg, dash and mksh (each probed with one plain curl), while tmux, neomutt, coreutils, util-linux and jq are integrated (HTTP 200). (2) Even inside an integrated project, OSS-Fuzz only exercises the entry points its registered fuzz harnesses call; code paths behind a different CLI mode, file format, option combination or decoder that no harness wires up are effectively unfuzzed, which the OSS-Fuzz Introspector (introspector.oss-fuzz.com) reports as uncovered reachable functions. This target asks for ONE fresh, sanitizer-confirmed memory-safety crash in such code: a reproducer input that makes the latest commit of a critical C/C++ project abort under ASan, UBSan or MSan, where 'critical' is pinned to a public measure (an OpenSSF Criticality Score, github.com/ossf/criticality_score, >= 0.6 for the project's canonical GitHub repo, OR the project ships in Debian 'important'/'required' priority or in the Android/busybox base userland) and where the crash is not a duplicate of any already-public bug. The find is the reproducer plus the sanitizer stack; it is judged mechanically by rebuilding and rerunning. Disclosure is commit-only: reporting the bug to the project (its SECURITY.md, security mailing list or private channel) is a human-only action and nothing about the bug is made public until a fix ships.

## What counts as a win

Success is a saved reproducer file (the exact bytes, sha256 recorded) plus a one-line command, such that an independent skeptic who (1) git-clones the project's canonical upstream repository, checks out the default-branch HEAD commit named in the claim (full 40-hex sha recorded; it must be <= 7 days older than status_checked and must be reachable on the real upstream default branch, not a fork), (2) builds it UNMODIFIED with the project's own build system and only the sanitizer flags added (CFLAGS/CXXFLAGS += '-g -fno-omit-frame-pointer -fsanitize=address,undefined -fsanitize-address-use-after-scope' for the ASan/UBSan build, or '-fsanitize=memory -fsanitize-memory-track-origins' built with clang and an MSan-instrumented libc++ for an MSan claim; no source edits, no added asserts, no custom allocator), (3) runs the project's real released binary / library through its ordinary interface on the reproducer (the documented CLI with the input as a file or on stdin, or a <= 15-line driver that calls only public library entry points and does no parsing of its own), observes under ASAN_OPTIONS=abort_on_error=1:detect_leaks=0 / UBSAN_OPTIONS=halt_on_error=1 / MSAN a sanitizer error report whose error class is one of: heap-buffer-overflow, stack-buffer-overflow, global-buffer-overflow, heap-use-after-free, stack-use-after-return, use-after-scope, double-free / invalid-free, wild/misaligned pointer deref (SEGV inside instrumented code), uninitialized-value use (MSan), or a signed-overflow / shift / invalid-cast UBSan diagnostic reached in library code, AND (4) confirms the top of the sanitizer stack (the faulting frame plus its two callers, function names after demangling) does NOT match any entry the skeptic can find, re-searched live at claim time, in: the project's own public issue tracker and commit log, the oss-security list archive (openwall.com/lists/oss-security), the CVE/NVD and GitHub Advisory databases, and the OSS-Fuzz public issue tracker (issues.oss-fuzz.com, formerly bugs.chromium.org/p/oss-fuzz) for that project. The reproducer, the exact commit sha, the build command, the sanitizer output (pasted verbatim), and the four novelty searches (with dates) are saved together. NOTHING is reported upstream or published by the agent; the write-up, including which private channel to use, goes to the human.

## Partial wins

- **p1:** A reproducer that triggers an ASan/UBSan/MSan memory-safety report of one of the listed error classes on the latest commit of an integrated OSS-Fuzz project, via a code path that NO registered OSS-Fuzz harness for that project reaches (demonstrated: the OSS-Fuzz Introspector marks the faulting function as unreached, or the project ships no fuzz harness that calls it), with the same novelty check passing. Counts because the bug was outside OSS-Fuzz's reach even though the project is integrated.
- **p2:** A reproducer that triggers a sanitizer report whose top-of-stack DOES match a bug already fixed upstream but where the named latest commit still crashes (an incomplete or regressed fix), with the upstream fix commit and the still-crashing HEAD sha both recorded. A regression, independently checkable, but not a brand-new defect.

## How a win is checked

Skeptic reproduces from scratch without reading the finder's build scripts: clone the named upstream repo, `git checkout <sha>`, confirm the sha is on the real default branch and its commit date is within 7 days of status_checked, build with the project's own system plus only the stated sanitizer flags, run the binary/driver on the reproducer file under the stated *SAN_OPTIONS, and require a sanitizer error report of one of the enumerated memory-safety classes with a non-zero (sanitizer-raised) exit. Then confirm it is a genuine defect, not an artefact: re-run with sanitizers OFF to show the input is otherwise accepted input to that interface (not a deliberately malformed internal API misuse), confirm the crash is NOT a plain failed assert()/abort() with no sanitizer finding, NOT an out-of-memory or run-time timeout, and NOT inside a test harness or the <=15-line driver itself. Finally run the four live novelty searches and record them. Fifteen minutes to about an hour per candidate, all on the skeptic's own machine; no network service is ever contacted beyond cloning the source and reading public trackers.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/google/oss-fuzz/tree/master/projects>

## Sources

- <https://github.com/google/oss-fuzz>
- <https://github.com/google/oss-fuzz/tree/master/projects>
- <https://google.github.io/oss-fuzz/getting-started/bug-disclosure-guidelines/>
- <https://introspector.oss-fuzz.com/>
- <https://issues.oss-fuzz.com/>
- <https://github.com/ossf/criticality_score>
- <https://github.com/AFLplusplus/AFLplusplus>
- <https://github.com/llvm/llvm-project/tree/main/compiler-rt/lib/fuzzer>
- <https://clang.llvm.org/docs/AddressSanitizer.html>
- <https://www.openwall.com/lists/oss-security/>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Pick a critical, parser-heavy C project that OSS-Fuzz does NOT integrate (verified live: projects/<name>/project.yaml is 404), write a small libFuzzer or AFL++ harness around its real input-parsing functions, seed with a corpus of valid inputs for that format, and run a laptop-hours campaign under ASan+UBSan; the absence of any prior continuous fuzzing is the whole edge.
- For an integrated project, read the OSS-Fuzz Introspector reachability report, find a public reachable function no harness covers (a secondary file format, an option-gated mode, a decoder), and write a harness that reaches it; novel coverage is where novel crashes live.
- Use AFL++ with CMPLOG/redqueen and a dictionary built from the format's magic bytes and keywords to get past checksums and length fields; libFuzzer with -use_value_profile=1 for the same effect.
- Build the ENTIRE project (not just one file) with -fsanitize=address,undefined so overflows in rarely-exercised helper code are caught, and keep an MSan build with an instrumented libc++ around for uninitialised-read bugs that ASan cannot see.
- Minimise every crash with afl-tmin / libFuzzer -minimize_crash to a tiny deterministic input before claiming, then re-run on a clean checkout to be sure it is the committed code and not a local edit that crashes.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- DUPLICATES are the main failure: a crash that already sits in the project's tracker, in a CVE/GHSA, on oss-security, or in the OSS-Fuzz issue tracker is not a win. Search all four live at claim time by the faulting function, not just by a generic title.
- A plain assert()/abort() firing, or a crash that only happens in a debug/assertions build, is not a sanitizer memory-safety finding; require an actual ASan/UBSan/MSan report of an enumerated class on a normal (non-assert) build.
- OOM and timeouts DO NOT count: libFuzzer 'out-of-memory' / 'timeout' and AFL++ hangs are resource exhaustion, not memory-safety bugs. Cap the allocator (rss_limit) only to keep the campaign alive, never report the cap being hit as a bug.
- A bug in the fuzz HARNESS or the small driver (it passes a bad pointer, frees twice, reads past a buffer it owns) is not a bug in the project. The driver must only call public entry points with well-formed arguments; the crash must be inside project code.
- UBSan noise: some projects knowingly rely on behaviour UBSan flags (e.g. unsigned-looking signed arithmetic, intentional type punning). A UBSan diagnostic only counts if it is a real defect reached through a normal input path, not a documented, benign pattern the project disables in its own suppressions.
- Stale HEAD: fuzzing an old checkout and claiming on today's commit. The crash must reproduce on the exact recent default-branch sha named in the claim; re-pull and re-check before claiming (statuses go stale).
- Non-upstream code: the crash must be in the project's own source at its canonical repo, not in a vendored third-party library, a distro patch, or a fork; a bug in a bundled dependency belongs to that dependency's project and tracker.
- Disclosure discipline: do not open an issue, email a maintainer, post to oss-security, or publish the reproducer. Reporting through the project's SECURITY.md / private security channel is the human's action; OSS-Fuzz-style practice is 90 days or until a fix ships (google.github.io/oss-fuzz bug-disclosure-guidelines), and this target keeps everything commit-only until then.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/critical-oss-bugs/critical-oss-new-sanitizer-crash.md
```

Already set up? Say `run SUET on critical-oss-new-sanitizer-crash`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `critical-oss-new-sanitizer-crash`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
