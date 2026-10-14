# MOONSHOT: Linear A, identifying the Minoan language with predictive translations

📜 **Undeciphered scripts** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: laptop-days / pure thought · open as of 2026-10-03

## The problem

Identify the language of Linear A and produce translations that predict unseen data. Phonetic values are approximately known via Linear B, but the language (Semitic, Luwian, Hurrian, Tyrsenian, isolate, or other) is unknown. Status as of 2026-10-03: Unsolved. The 2026 claims (Di Mino 'Ya Diktu', Tinitic Semitic, 508-entry lexicon, a September 2026 preprint) are unverified, and the independent check found that Hebrew-root matches are no better than scrambled controls. No accepted decipherment. kbennett2000/linear-a-check found that scrambled words match Hebrew roots nearly as well as real words for Di Mino's Sept 2026 preprint, holding across Hebrew, Ugaritic and invented root lists. Navarre-AI carries RILA Supplement 1 provenance on only 25 records.

## What counts as a win

All of these must hold. (1) A lexicon and grammar frozen with a hash before testing; every gloss tested against logogram adjacency must have been derived without any logogram-context information, documented in the frozen lexicon's provenance. (2) On a held-out set chosen by a third-party seed as a 30% document split stratified by site (not just the 25 RILA records), the frozen grammar predicts morphology and logogram-consistent meanings. Example: words glossed as 'wine' precede the VIN logogram at least 80% of the time on held-out tablets. (3) Lexicon matches to the claimed language exceed all kbennett2000 cycle 6-8 controls (scrambled words, alternate root lists, invented roots, latitude count) with p < 0.001 after correcting for phonological latitude. (4) The translations of held-out accounting tablets are numerically coherent with KU-RO totals. Anything less is not a claim.

## Partial wins

- **p1:** A frozen lexicon of at least 3 commodity glosses derived without any logogram-context information (provenance documented) whose held-out logogram-adjacency predictions (e.g. 'wine' word precedes VIN) hold at least 80% of the time on the third-party-seeded, site-stratified 30% document split, with p < 0.001 against glosses permuted among the same words.
- **p2:** A frozen lexicon whose matches to a single named candidate language exceed every kbennett2000 cycle 6-8 control (scrambled words, alternate root lists, invented roots, latitude count) with p < 0.001 after phonological-latitude correction, on held-out documents.

## How a win is checked

The verifier runs the kbennett2000/linear-a-check-style staged tests on the frozen lexicon, checks the hash and timestamp, applies the grammar to held-out documents itself, and scores logogram consistency automatically. Additionally, the verifier checks the provenance of each gloss for logogram-context leakage.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/Navarre-AI/linear-a>

## Sources

- <https://github.com/Navarre-AI/linear-a>
- <https://sigla.phis.me>
- <https://github.com/ftamburin/CSA_OptMatcher>
- <https://github.com/kbennett2000/linear-a-check>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/undeciphered-scripts/linear-a-language-identification.md
```

Already set up? Say `run SUET on linear-a-language-identification`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `linear-a-language-identification`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
