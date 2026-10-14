# Sanitizer-confirmed crash in BusyBox, toybox or ncurses (core C userland, not on OSS-Fuzz) from a crafted input

🐛 **Bugs in critical open source** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours (single core per campaign; a few GB RAM; small corpora) · open as of 2026-10-14

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

Three C projects sit in the base userland of enormous numbers of devices yet are NOT integrated into Google's OSS-Fuzz on 2026-10-14 (projects/<name>/project.yaml returns HTTP 404 for each, one plain curl): BusyBox (busybox.net, the single-binary userland of most embedded Linux and many containers; maintained by Denys Vlasenko and contributors; bug tracker bugs.busybox.net), toybox (github.com/landley/toybox, Rob Landley; the default toolbox shipped in Android; contact via lists.landley.net), and ncurses (invisible-island.net/ncurses, Thomas E. Dickey; the terminal library behind most TUIs, with the tic/infocmp terminfo compiler as a notorious parser). All three are heavy parsers of untrusted-ish input: BusyBox applets parse archives (tar, cpio, gzip, bzip2, lzma), config and text formats; toybox mirrors them; ncurses' tic/infocmp and terminfo-reading code parse compiled and source terminfo, and ncurses has a history of terminfo-parsing CVEs (e.g. the 2017 and 2023 rounds found by hand and by fuzzing). Because no continuous fuzzer runs on them, their rarely-exercised applets and format branches are plausibly reachable ground for a fresh memory-safety bug. This target asks for ONE reproducer input that crashes the latest commit of BusyBox, toybox or ncurses under AddressSanitizer / UndefinedBehaviorSanitizer / MemorySanitizer (LLVM/Clang sanitizer team) through the tool's normal interface, not matching any already-public bug. The win is the reproducer plus the sanitizer stack, judged by rebuilding and rerunning. Disclosure is commit-only: notifying the project through its own channel is a human-only step and nothing is public until a fix ships.

## What counts as a win

Success is a saved reproducer (exact bytes, sha256 recorded) and the exact command, such that an independent skeptic who (1) clones the canonical upstream source (git.busybox.net/busybox or its GitHub mirror github.com/mirror/busybox for BusyBox; github.com/landley/toybox for toybox; the official ncurses git / invisible-island.net release matching a named commit or snapshot for ncurses) and checks out the default-branch HEAD named in the claim (full commit id / snapshot date recorded, <= 7 days older than status_checked), (2) builds it UNMODIFIED with the project's own build (BusyBox: `make defconfig` then enable the relevant applet, CC='clang', CFLAGS += '-g -fno-omit-frame-pointer -fsanitize=address,undefined'; toybox: `make` with the same CFLAGS; ncurses: `./configure --with-debug` plus CFLAGS/LDFLAGS carrying '-fsanitize=address,undefined'; an MSan claim uses '-fsanitize=memory -fsanitize-memory-track-origins' with clang) with NO source edits and NO added asserts, (3) runs the real applet/binary on the reproducer through its documented interface (e.g. `busybox tar -xf repro`, `toybox tar xf repro`, `tic repro`, `infocmp -A repro ...`, or feeding the input on stdin where that is the tool's normal mode), under ASAN_OPTIONS=abort_on_error=1:detect_leaks=0 / UBSAN_OPTIONS=halt_on_error=1, and observes a sanitizer error report whose class is one of heap-buffer-overflow, stack-buffer-overflow, global-buffer-overflow, heap-use-after-free, stack-use-after-return, use-after-scope, double-free/invalid-free, wild-pointer SEGV in instrumented code, or (MSan) use-of-uninitialized-value, or a genuine UBSan diagnostic (signed overflow, out-of-bounds shift, invalid cast, misaligned access) reached in project code, AND (4) confirms the faulting frame plus its two callers (demangled function names) do NOT match anything found, searched live at claim time, in the project's own tracker/commit log, the oss-security archive (openwall.com/lists/oss-security), CVE/NVD and GitHub Advisories, and the OSS-Fuzz public tracker (issues.oss-fuzz.com). The reproducer, commit id, build command, verbatim sanitizer output and the four dated novelty searches are saved together. The agent reports upstream to NO ONE and publishes nothing; the write-up and the suggested private channel go to the human.

## Partial wins

- **p1:** A reproducer that produces one of the listed sanitizer memory-safety reports but whose faulting frame matches a bug ALREADY FIXED in a later upstream commit or distro patch, while the named latest commit still crashes (an incomplete fix or a reintroduction); the fix commit and the crashing HEAD id both recorded. A real still-live crash, but a regression, not a new defect.
- **p2:** A reproducer that reliably triggers an ASan/UBSan report only in a NON-default configuration of BusyBox or toybox (an applet not in defconfig but shipped enabled by common distributions/Android builds, config recorded), with the exact .config / build flags saved and the same novelty check passing. Narrower because it depends on a build option, but still a genuine bug in shipped code paths.

## How a win is checked

Skeptic rebuilds from scratch without the finder's scripts: clone the named upstream repo, check out the exact commit, confirm it is on the real default branch and dated within 7 days of status_checked, build with the project's own system plus only the stated sanitizer flags, and run the named applet/binary on the reproducer under the stated *SAN_OPTIONS; require a sanitizer error report of an enumerated memory-safety class. Then rule out artefacts: re-run with sanitizers off to confirm the input is handled by that interface normally (not an internal-API abuse), confirm it is not a bare assert()/abort(), not OOM, not a timeout/hang, and the crash is inside project code not in libc or a vendored dependency. Finally run the four live novelty searches and record them. Under an hour per candidate, entirely on the skeptic's machine; nothing beyond cloning source and reading public trackers is contacted.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/google/oss-fuzz/tree/master/projects>

## Sources

- <https://busybox.net/>
- <https://bugs.busybox.net/>
- <https://github.com/mirror/busybox>
- <https://github.com/landley/toybox>
- <https://invisible-island.net/ncurses/>
- <https://github.com/mirror/ncurses>
- <https://github.com/google/oss-fuzz/tree/master/projects>
- <https://issues.oss-fuzz.com/>
- <https://www.openwall.com/lists/oss-security/>
- <https://clang.llvm.org/docs/AddressSanitizer.html>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- BusyBox/toybox archive and compression applets (tar, cpio, unzip, gunzip, bunzip2, unlzma, rpm, dpkg-deb) parse attacker-chosen headers and streams; build a corpus of small valid archives, mutate with AFL++ (CMPLOG on for magic/length fields) against `busybox <applet>`, and watch for overflow in header parsing.
- ncurses terminfo path: fuzz `tic` and `infocmp` on compiled-terminfo and source-terminfo inputs (the historical bug class); a crafted compiled terminfo entry with inconsistent string/offset tables is the classic trigger. Thomas Dickey's code is careful, so look at less-trodden branches (extended capabilities, -x, screen/padding capabilities).
- Write a thin libFuzzer harness around the project's real parsing function where one is cleanly callable (e.g. ncurses' _nc_read_entry / read_termtype internals, BusyBox's archive 'get_header_*' routines) to fuzz faster than through the CLI, but reproduce and CLAIM through the normal binary so the skeptic's check is simple.
- Build with -fsanitize=address,undefined across the whole tree so arithmetic/overflow bugs in rarely-run helpers surface; keep an MSan build (clang + instrumented libc++) for uninitialised reads in parsers that copy partially-initialised structs.
- Minimise each crash with afl-tmin / libFuzzer -minimize_crash and re-run on a fresh clone to confirm it is the committed code that crashes, before writing anything down.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- DUPLICATE risk is high on these mature projects: a crash may already be in the project's tracker, a past CVE, oss-security, or a Debian/Android patch. Search by faulting function live at claim time; a decades-old tool has many closed reports that look similar.
- BusyBox and toybox deliberately favour small code over hardening and sometimes document that malformed input to a given applet is out of scope; a crash is still a sanitizer memory-safety finding, but check the project's stated threat model before calling it security-relevant, and let the human judge the channel.
- A bare assert()/abort() or a debug-only check firing is not a sanitizer memory-safety bug; require an actual ASan/UBSan/MSan report on a normal (non-assert) build of an enumerated class.
- OOM and timeouts/hangs are not memory-safety bugs; BusyBox decompressors can be made to allocate or loop a lot. Resource exhaustion does not count under this target.
- Crashing the fuzz driver, not the tool: if you fuzz an internal function directly, the bug must be in that function given well-formed arguments, not in the harness passing garbage the CLI could never produce. Prefer to claim through the real binary.
- ncurses builds can pull in a system terminfo database and wide/narrow variants; make sure the crash is in the built-from-source library/tool at the named commit, with TERMINFO pointed at your own built tree, not in a distro-installed ncurses.
- Stale HEAD: reproduce on the exact recent default-branch commit named in the claim; re-pull before claiming. For ncurses, record the precise snapshot (Dickey ships dated patch snapshots) the skeptic must fetch.
- Disclosure discipline: do NOT file a bugs.busybox.net ticket, post to the toybox list, email Thomas Dickey, or publish the reproducer. Reporting through the project's own security/bug channel is the human's action; everything stays commit-only until a fix ships.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/critical-oss-bugs/busybox-toybox-ncurses-unfuzzed-crash.md
```

Already set up? Say `run SUET on busybox-toybox-ncurses-unfuzzed-crash`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `busybox-toybox-ncurses-unfuzzed-crash`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
