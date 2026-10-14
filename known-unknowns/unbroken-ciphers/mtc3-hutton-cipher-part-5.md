# MysteryTwister 'The Hutton Cipher – Part 5' (4,250-letter ciphertext-only, 0 solvers since 2023)

🔐 **Unbroken ciphers** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours · open as of 2026-10-03

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

Eric Bond Hutton's 2018 pen-and-paper cipher: a repeating keyword K1 and a keyword-mixed alphabet from K2. For each letter, the shift is n = rank(K1[i mod |K1|]) + rank(current first letter of the alphabet). The plaintext letter is swapped with the letter n places to its right, and that letter is output, so the alphabet mutates every step. Part 5 is a ciphertext-only challenge with contemporary English plaintext, numerals spelled out, spaces and punctuation removed, and both keywords random strings under 10 letters. The ciphertext file hutton_ciphertext_5.txt holds 4,250 A-Z letters (4,272 bytes including 22 newlines) with IC 0.0385. Recover the plaintext and both keywords.

## What counts as a win

CONFIRMED if keywords K1 and K2 (each under 10 letters) are given such that the Hutton procedure exactly as specified in the PDF decrypts the ENTIRE 4,250-letter ciphertext to fluent contemporary English with ≥97% of letters in dictionary words and zero edits, and re-encryption with the same keys reproduces the ciphertext byte for byte. Key space is about 85 bits against about 13,000 bits of plaintext redundancy, so a fluent full decrypt is decisive. Final external confirmation comes when the human submits on MTC3. First-solve status is judged against the live solver count on https://mysterytwister.org/challenges/level-2/ at verification time. Only the human submits to MTC3.

## Partial wins

- **p1:** Reduced blind benchmark: the verifier enciphers 3 contemporary English texts of 4,250 letters with the Part 5 procedure (verified on the PDF example) under random keywords K1, K2 of fewer than 10 letters, disclosing only |K1| and |K2|; the solver recovers both keywords and the full plaintext of at least 2 of the 3, checked by exact re-encryption.
- **p2:** Full blind benchmark: as above but with keyword lengths undisclosed; the solver recovers both keywords and the full plaintext of at least 2 of the 3, ciphertext-only, checked by exact re-encryption.

## How a win is checked

Implement Hutton exactly per the PDF and check it reproduces the PDF example: MEETMEATTHEGREENMANATTHREE with FEDORA/JUPITER gives RSBIENXONGQYTMWQVWXWIOKXKU. An auditor implementation already round-trips this. Download the add.zip, strip newlines and assert 4,250 letters. Decrypt with the claimed keys, re-encrypt and diff, then run a dictionary-coverage check.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://mysterytwister.org/media/challenges/pdf/mtc3-hutton-01-hutton-05-en.pdf>

## Sources

- <https://mysterytwister.org/media/challenges/pdf/mtc3-hutton-01-hutton-05-en.pdf>
- <https://mysterytwister.org/media/challenges/add/mtc3-hutton-01-hutton-05-add.zip>
- <https://eprint.iacr.org/2023/1113>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/mtc3-hutton-cipher-part-5.md
```

Already set up? Say `run SUET on mtc3-hutton-cipher-part-5`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `mtc3-hutton-cipher-part-5`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
