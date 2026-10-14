# Dorabella cipher (Elgar, 1897)

🔐 **Unbroken ciphers** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

An 87-character note of semicircle glyphs (24 distinct symbol types), sent by Edward Elgar to Dora Penny in July 1897. Transcribed by Schmeh as: ABCDE FGDHA IJKLJ MJJFB BJNGO GNIP / GJGFQ DHRSC JJCFN KGJIJ FTPKL QHHQI P / CPFUP CLUUN PCJFU KPNDB NPFDL ED. Modern MASC solvers that handle 87-letter English or Latin MASCs at about 98% succeed fail on it, which suggests it is not a plain monoalphabetic substitution. Find the method and plaintext.

## What counts as a win

CONFIRMED only if ALL of the following hold. (1) A method family is declared BEFORE searching, from systems Elgar is documented to have known (for example Elgar's own Pigpen-like cipher notes, Playfair, keyword substitution with transposition), with total key bits stated. (2) The method decrypts all 87 symbols to grammatical English with at most 2 exceptions. (3) Key bits are below 0.5 x 87 x 3.2 ≈ 140, or else an external corroboration such as the key written in Elgar's papers. (4) Across 1000 random 87-symbol strings with the same symbol-frequency profile, the same solver never achieves comparable fluency. The cipher must still show 0 solvers on MTC3 Level X at verification time.

## Partial wins

- **p1:** Archival corroboration: a citable document in Elgar's papers or correspondence (archive, shelfmark, scan) that gives a key, method or plaintext for the Dorabella note, which a skeptic can open and apply to the 87-symbol MTC3 transcription.
- **p2:** Over-budget candidate: a method family declared before searching and a key that decrypts all 87 symbols to grammatical English with at most 2 exceptions and passes the 1000-string frequency-matched null, but with key bits between 140 and 200 (failing only criterion (3)); reported as candidate, not confirmed.

## How a win is checked

Use Schmeh's MTC3 transcription and check it against the original image. Implement the method independently, decrypt, check grammar and word coverage, recompute key bits, and run the frequency-matched random-string null.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://mysterytwister.org/media/challenges/pdf/mtc3-schmeh-01-dorabella-en.pdf>

## Sources

- <https://mysterytwister.org/media/challenges/pdf/mtc3-schmeh-01-dorabella-en.pdf>
- <https://en.wikipedia.org/wiki/Dorabella_Cipher>
- <https://ciphermysteries.com/other-ciphers/the-dorabella-cipher>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/dorabella-1897.md
```

Already set up? Say `run SUET on dorabella-1897`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `dorabella-1897`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
