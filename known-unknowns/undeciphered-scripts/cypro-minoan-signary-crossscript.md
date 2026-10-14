# Cypro-Minoan: sign-inventory merges and Cypriot-syllabary value transfer tested on held-out inscriptions

📜 **Undeciphered scripts** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Cypro-Minoan (Late Bronze Age Cyprus and Ugarit; about 250 objects; inventory estimates of 88 to 112 or more signs; Donnelly 2025 gives an integrated signary of 112 signs plus variants) is undeciphered. About 9-11 signs have plausible phonetic values via Linear A/B and the Iron Age Cypriot syllabary, but none of these is definitive. Two things are open. First, whether CM1/CM2/CM3 are one script or several; Corazza et al. (PLoS ONE 2022) used deep learning to argue for reclassification. Second, which variants are distinct signs. The task is a sign-merge and value-transfer hypothesis that makes checkable predictions on held-out inscriptions. There is no authoritative open machine-readable corpus (Olivier 2007 HoChyMin and Ferrara 2012-13 are print), so data entry is the binding constraint. Tamburini's CSA_OptMatcher (Frontiers in AI, 2025-05-30) has NOT been applied to Cypro-Minoan; its 86.3% figure is on the Cypriot Syllabary/Greek benchmark. Status as of 2026-10-03: Undeciphered as of 2026-10-03 (Donnelly 2025 monograph). CM1/2/3 classification is debated (Corazza et al. PLoS ONE 2022). No accepted phonetic values beyond plausible Cypriot and Linear A homomorph transfers.

## What counts as a win

There are two possible outcomes. (A) A sign-merge set: fixed using at most 70% of inscriptions, then on the held-out inscriptions it must raise cross-inscription sequence recurrence (repeated sign-groups at least 3 long) by at least 25% over the raw signary. The null is a matched random merge set, and the gain must have p < 0.01. (B) A value transfer: Cypriot-syllabary values applied to CM homomorphs that produce at least 3 sign-groups which match independently attested Cypriot or Ugaritic personal names or toponyms from a list fixed in advance. The phonological-latitude-adjusted null (random value permutations) must give p < 0.01. Outcome (B) must also report how many matches random assignments produce. Both outcomes are subject to these conditions. Every inscription used must be transcribed from or checked against Olivier 2007 (HoChyMin) or Ferrara 2012-13, with sign IDs mapped to the Donnelly 2025 integrated signary; the hawkinsnick corpus cannot be the sole source. For (B), the name list (Ugaritic and Cypriot prosopography) and the phonological-equivalence rules are frozen and hashed before any reading is produced. Report the full null distribution of match counts from random value permutations. The p < 0.01 must survive Bonferroni correction over all sign-group lengths tried.

## Partial wins

- **p1:** Outcome (A) at a weaker threshold: a sign-merge set fixed on at most 70% of inscriptions (all transcribed from or checked against HoChyMin/Ferrara, sign IDs mapped to the Donnelly 2025 signary) that raises held-out cross-inscription recurrence of sign-groups of length at least 3 by at least 15% over the raw signary, with p < 0.01 against matched random merge sets.
- **p2:** Outcome (B) at a weaker threshold: Cypriot-syllabary (or CSA_OptMatcher-derived) values applied to CM homomorphs give at least 2 sign-groups matching a frozen, hashed list of independently attested Ugaritic or Cypriot personal names or toponyms under frozen phonological-equivalence rules, with p < 0.01 against random value permutations after Bonferroni correction over all sign-group lengths tried, and the full null distribution reported.
- **p3:** A sequence-only (no sign-shape features) classifier, frozen before evaluation, that separates CM1 from CM2 inscriptions on held-out inscriptions with label-permutation p < 0.01 after controlling for text length, a distributional result not reported by Corazza et al. 2022 or Donnelly 2025.

## How a win is checked

The verifier checks a random 10% of the claimed corpus against HoChyMin or Ferrara images, then recomputes recurrence (A) or name matches (B) and the nulls with its own seed. For (B) it builds its own name list from Ugaritic prosopography before seeing the matches.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/hawkinsnick/Cypro-Minoan>

## Sources

- <https://github.com/hawkinsnick/Cypro-Minoan>
- <https://github.com/ashmikuz/sign2vec_d>
- <https://github.com/ftamburin/CSA_OptMatcher>
- <https://journals.plos.org/plosone/article?id=10.1371%2Fjournal.pone.0269544>
- <https://bmcr.brynmawr.edu/2025/2025.11.24/>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/undeciphered-scripts/cypro-minoan-signary-crossscript.md
```

Already set up? Say `run SUET on cypro-minoan-signary-crossscript`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `cypro-minoan-signary-crossscript`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
