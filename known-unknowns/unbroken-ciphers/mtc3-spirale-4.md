# MysteryTwister 'Spirale Part 4' (hand 'OTP' cipher, 0 solvers)

🔐 **Unbroken ciphers** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

Spirale is a hand cipher by Philippe Allard designed to resemble a one-time pad. Part 4 is ciphertext-only: a 485-letter A-Z ciphertext (ciphertext_Spirale-04.txt) under four NEW random keys of exactly 7 letters each (lenkey=7 in the reference code, about 131.6 bits in total). K1 and K2 generate alphabet permutations; K3 and K4 generate the long key through a lagged-Fibonacci-style recurrence X_n = X_{n-d} o X_{n-k} under a generalized operator. The official zip (mtc3-allard-04-spirale-04-add.zip) contains MTC3_Spirale_Description.pdf, the ciphertext and spirale.zip with the reference implementation Spirale2.1.3.py. The MTC3 answer is the first four words of the second sentence. MTC3 Level III lists 0 solvers (published 2015-08-23). Parts 1-3 keys are not published.

## What counts as a win

CONFIRMED if four 7-letter keys and a 485-letter plaintext are given such that the unmodified Spirale2.1.3.py from the official zip encrypts the plaintext to ciphertext_Spirale-04.txt byte for byte (after whitespace normalization), and the plaintext is fluent natural language with at least 97% dictionary coverage. The human may optionally submit the first four words of the second sentence to MTC3. First-solve status is judged against the live solver count on https://mysterytwister.org/challenges/level-3/ at verification time.

## Partial wins

- **p1:** Blind full-key benchmark: the verifier encrypts a fresh ~485-letter English text with Spirale2.1.3.py (default alphabet) under four random 7-letter keys; the solver, ciphertext-only, returns all four keys and the plaintext, and the unmodified reference script reproduces the ciphertext byte for byte.
- **p2:** Blind keystream benchmark: as above, but the verifier discloses K1 and K2; the solver recovers K3, K4 and the plaintext from ciphertext only, verified by exact re-encryption with the reference script.

## How a win is checked

Download mtc3-allard-04-spirale-04-add.zip, record its SHA-256, and unzip it along with the inner spirale.zip. Run 'python Spirale2.1.3.py -e K1 K2 K3 K4' on the claimed plaintext with the default alphabet and diff against ciphertext_Spirale-04.txt. Assert 485 letters. Run a language-coverage check.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://mysterytwister.org/media/challenges/pdf/mtc3-allard-04-spirale-04-en.pdf>

## Sources

- <https://mysterytwister.org/media/challenges/pdf/mtc3-allard-04-spirale-04-en.pdf>
- <https://mysterytwister.org/challenges/level-3/>
- <https://mysterytwister.org/media/challenges/add/mtc3-allard-04-spirale-04-add.zip>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/mtc3-spirale-4.md
```

Already set up? Say `run SUET on mtc3-spirale-4`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `mtc3-spirale-4`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
