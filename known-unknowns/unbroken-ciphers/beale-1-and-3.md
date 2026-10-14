# Beale ciphers #1 (location) and #3 (names): book-cipher key-text search

🔐 **Unbroken ciphers** · standard · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Beale cipher #2 decodes with the Declaration of Independence (word n gives its initial letter). Ciphers #1 (about 520 numbers, max about 2906) and #3 (about 618 numbers) remain undeciphered. Either find the key text and numbering rule, or prove they are constructed nonsense. Gillogly found alphabetic runs ('abcdefghiijklmmnohpp') when B1 is decoded with the DoI, which is evidence of fabrication.

## What counts as a win

CONFIRMED only if ALL of the following hold. (1) A specific key text published before 1885 is identified, with exact edition or source, and a single deterministic numbering rule declared in advance (word-initial letter, a fixed treatment of hyphens and abbreviations, a fixed offset). (2) At least 90% of the numbers in B1 (or B3) decode under that rule to a continuous English text that is coherent and specific: B1 should describe a location, B3 should list names and residences. (3) The number of key texts times rule variants searched is reported, and the decode's English score beats the best decode over the same search applied to at least 1000 permuted copies of the cipher numbers (permutation p < 1e-6 after Bonferroni). (4) No per-number fudging beyond a declared error list of at most 3%. (5) The cipher must still be listed unsolved (Wikipedia list of ciphertexts, MTC3 Level X) at verification time. A hoax proof is NOT a confirmed solve; it is partial win p1.

## Partial wins

- **p1:** Rigorous hoax proof: a fully specified generative model of how B1 or B3 was produced (for example sequential selection from DoI word positions), with all competing genuine-book-cipher models declared before fitting, that explains the observed statistics with a likelihood ratio above 1e6 against every declared genuine model, and is a new quantitative result beyond Gillogly's runs, Nickell, and Wase's stylometry.
- **p2:** A specific pre-1885 key text (exact edition) and a single pre-declared numbering rule under which at least 300 consecutive numbers of B1 or B3 decode to coherent English, with at most 3% declared errors, and the decode beats the same search on 1000 permuted copies at p < 1e-6 after Bonferroni over all texts and rule variants searched.

## How a win is checked

Obtain the cipher numbers from the 1885 pamphlet transcription (Cipher Foundation) and cross-check them against a second transcription (GitHub cipher1.txt/cipher3.txt). Obtain the key text from an independent scan, word-index it with the declared rule using the verifier's own code, decode, score English, and rerun the permutation null.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <http://cipherfoundation.org/older-ciphers/beale-papers/beale-papers-transcription/>

## Sources

- <http://cipherfoundation.org/older-ciphers/beale-papers/beale-papers-transcription/>
- <https://gist.github.com/omaskery/010f5ab548c9c8a20bc0>
- <https://github.com/albert3su/bealecipher>
- <https://mysterytwister.org/media/challenges/pdf/mtc3-schmeh-04-beale-en.pdf>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/beale-1-and-3.md
```

Already set up? Say `run SUET on beale-1-and-3`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `beale-1-and-3`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
