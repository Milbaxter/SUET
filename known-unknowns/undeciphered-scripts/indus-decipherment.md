# MOONSHOT: Indus script, sign values or meanings that predict held-out seals

📜 **Undeciphered scripts** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: laptop-days / pure thought · open as of 2026-10-03

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

Assign phonetic or logographic values to Indus signs in a way that yields consistent readings in a specific language and predicts unseen inscriptions. Status as of 2026-10-03: Unsolved. The USD 1M Tamil Nadu prize (announced January 2025) is unclaimed and has no formal submission portal. Many 2025-2026 claims (Indo-Aryan, Dravidian, cryptanalytic) are unaccepted. paragorth/Indus- (September 2026) shows that decipherment validators accept wrong keys. Its 2026-09-25 correction found that with more than about 150 signs, wrong keys beat the true key under every objective tested; only small syllabaries (about 80 signs) let correct keys win.

## What counts as a win

All of these must hold. (1) A frozen sign-to-value table. (2) The paragorth validator plus a planted-key test on synthetic corpora matched to the Indus scale (at least 400 sign types, frequency distribution matched to M77, mean text length about 5, about 4,000 texts): the method ranks the true key first against 100 random and 100 adversarially optimized wrong keys in at least 90% of synthetic replicates. (3) On a verifier-chosen held-out set of seals, the readings produce lexicon matches in the target language beyond scrambled-sign controls with p < 0.001. (4) It predicts at least 5 field-symbol or object-type correlations that are confirmed on the held-out set.

## Partial wins

- **p1:** Indus-scale planted-key recovery alone: a frozen method that, on verifier-generated synthetic corpora with at least 400 sign types, M77-matched frequency distribution, mean text length about 5 and about 4,000 texts, ranks the true key first against 100 random and 100 adversarially optimized wrong keys in at least 90% of replicates (paragorth 2026 found no objective that does this above about 150 signs).
- **p2:** A method that passes p1 and whose frozen sign-to-value table, applied to a verifier-chosen held-out set of seals, yields lexicon matches in a named target language beyond scrambled-sign controls with p < 0.001.

## How a win is checked

The verifier runs the validators in paragorth/Indus- and the joyboseroy null suite, does the planted-key recovery on synthetic data, and computes the held-out statistics with its own seeds. Additionally, the verifier generates the scale-matched synthetic corpora itself with fresh seeds.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/paragorth/Indus->

## Sources

- <https://github.com/paragorth/Indus->
- <https://github.com/joyboseroy/indus_decipher>
- <http://www.indus.epigraphica.de>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/undeciphered-scripts/indus-decipherment.md
```

Already set up? Say `run SUET on indus-decipherment`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `indus-decipherment`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
