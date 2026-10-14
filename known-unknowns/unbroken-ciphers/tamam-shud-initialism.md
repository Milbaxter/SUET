# Somerton Man (Tamam Shud) code: exact initialism source search

🔐 **Unbroken ciphers** · standard · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

The pencilled code from the back of the Rubaiyat in the 1948 Somerton Man case reads: W(M?)RGOABABD / [struck] MLIAOI / WTBIMPANETP / MLIABO AIAQC / ITTMTSAMSTGAB, with an 'X' over one O. Abbott's group judged it most likely the initial letters of words, while Rehling (2014) suggested shorthand that is unrecoverable. The man was identified in 2022 as Carl 'Charles' Webb, but the code remains unbroken. The target: find the exact source text, if it is an initialism of a published text, or another deterministic decoding. Lines 1, 3, 4 and 5 total 44 letters (9 + 11 + 11 + 13).

## What counts as a win

CONFIRMED only if the claim exhibits a text demonstrably published before December 1948, with exact edition, whose consecutive word initials reproduce at least 40 of the 44 letters of lines 1, 3, 4 and 5 in order, allowing only the documented M/W ambiguity plus at most 2 further mismatches, with each line mapping to a contiguous passage. In addition, the expected number of such matches in the searched corpus under a word-initial-frequency model must be below 1e-4 (report corpus size in word positions). Free-form 'phrase invention' (making up a sentence per letter) is never acceptable. If lines are matched to different passages, the chance expectation is computed per line and combined (product of per-line expectations times the number of passage combinations considered), and the combined expectation must be below 1e-4. M/W and crossed-out-line handling is declared before searching.

## Partial wins

- **p1:** One full line (line 3, 4 or 5; 11-13 letters) matched by the consecutive word initials of a single contiguous passage in a text demonstrably published before December 1948, with at most 1 mismatch, and a per-line chance expectation below 1e-4 over the reported corpus size in word positions.
- **p2:** Two different lines each matched (at most 2 mismatches each) by contiguous passages of the SAME pre-December-1948 work, with the combined chance expectation (per-line expectations multiplied, times the number of within-work position pairs considered) below 1e-4.

## How a win is checked

Obtain the source passage from an independent digitized copy (HathiTrust, Internet Archive, Trove). Compute word initials with a script and align them to the code with the allowed mismatches. Recompute the chance-match expectation from initial-letter frequencies and the stated corpus size.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://en.wikipedia.org/wiki/Somerton_Man>

## Sources

- <https://en.wikipedia.org/wiki/Somerton_Man>
- <https://trove.nla.gov.au/>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/tamam-shud-initialism.md
```

Already set up? Say `run SUET on tamam-shud-initialism`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `tamam-shud-initialism`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
