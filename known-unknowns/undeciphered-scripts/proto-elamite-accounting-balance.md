# Proto-Elamite: numeral-system and commodity assignments checked by tablet arithmetic

📜 **Undeciphered scripts** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Proto-Elamite (Susa and the Iranian plateau, c. 3100-2900 BCE; about 1,400-1,700 tablets) is only partly deciphered. Its numerical systems (sexagesimal, bisexagesimal, decimal, capacity, etc., following Englund and Damerow) are mostly understood. Three things are still open. (a) The same numeral signs can be read in up to four systems, so the system meant on a given entry is ambiguous (Born, Monroe, Kelley & Sarkar 2025). (b) Most non-numeric signs (ideograms, 'header' signs, complex graphemes) have no known commodity or meaning. (c) Many tablets with a reverse-side total do not reconcile with their obverse entries under the current readings. The task is to find new, falsifiable assignments of the form 'sign X is counted in system Y', 'sign X denotes commodity class Z' or 'unit U = k x unit V' that the tablets' own arithmetic confirms. Status as of 2026-10-03: Partly deciphered (numerical systems largely understood); no accepted reading of ideograms as of 2026-10-03. Latest: Born et al. arXiv 2502.00090 v2 (2025-04-25); Monroe/Kelley/Born/Sarkar NEA 88(4) Dec 2025; Kelley, Cambridge Element (2026-07-18). Amateur repo MahmoodKhalil57/ProtoElamite (created 2026-06-17, 1,467 tablets, '9 falsifiable claims') is not peer-reviewed.

## What counts as a win

All of the following must hold. (1) Before any evaluation, freeze in a timestamped, hashed file: (i) the rule, as a deterministic function of observable context only (numeral sign identity, accompanying ideogram/header sign, position, obverse/reverse), with a declared count k of free parameters; and (ii) a seeded 30% held-out split of P-numbers. Choosing the system per entry, or per tablet, to maximize balance is forbidden. (2) A tablet's total is identified only by the pre-registered layout convention (reverse-side numeral after the entries), never by which number equals the sum. (3) Eligible held-out tablets have an intact total and every entry intact (no [ ], #, ? or x in any numeral). Report N_eligible and the baseline count of unbalanced tablets first. (4) The baseline is the best of two readings: Born et al. 2025 v2 sign values plus their published disambiguation, and Englund-convention readings. The new rule must balance at least max(5, 15% of baseline-unbalanced eligible held-out tablets) more held-out tablets exactly (Fraction equality), and break at most 1 tablet the baseline balanced. (5) The gain has permutation p < 0.01 against 1,000 alternative rules with the same k and the same form. (6) A literature check of Born/Kelley/Monroe/Sarkar 2019-2025, NEA 2025, Kelley 2026 and Englund 2004 shows the rule is unpublished. Claim only as 'arithmetic-confirmed reading rule (candidate)'. Results that only improve classifier accuracy without arithmetic closure do not satisfy the full criterion.

## Partial wins

- **p1:** Cross-tablet record linkage: a pre-registered search finds at least one pair or set of Proto-Elamite tablets in which one tablet's layout-defined total (or its full entry list) equals exactly (Fraction equality) the sum of the layout-defined totals or entries of the other tablet(s) under the baseline readings, all numerals intact (no [ ], #, ? or x). The number of such exact links must exceed the 99th percentile of the same search run on 1,000 random re-pairings of tablets with matched entry-count and value distributions, and the links must be absent from Born/Kelley/Monroe/Sarkar 2019-2025, NEA 88(4) 2025, Kelley 2026 and Englund 2004.
- **p2:** A frozen, deterministic unit-ratio or system-assignment rule ('unit U = k x unit V', or 'numeral sign N under header/ideogram H is read in system S') with declared k free parameters, not published in the sources above, that balances at least 3 more eligible held-out tablets exactly than the best baseline (Born et al. 2025 v2 pipeline or Englund-convention readings), breaks none, and has permutation p < 0.05 against 1,000 same-form, same-k alternative rules. (Weaker than the full bar of max(5, 15%) and p < 0.01.)
- **p3:** A model or rule trained without the Born et al. 2025 v2 released numeral-disambiguation test set (no test items in training, checked by the verifier) that strictly exceeds the best accuracy published on that test set at verification time, with paired bootstrap p < 0.01 over test items.

## How a win is checked

The verifier obtains the ATF in one of two ways: (a) git-lfs clone of cdli-gh/data, checking the LFS oid sha256 of each file against the claim; or (b) the current CDLI framework export from cdli.earth with a recorded download date and hash. It filters period = Proto-Elamite and parses numerals with independent code using a published system table (Englund 2004 / Born v2 corrected decimal). It applies the frozen rule mechanically (no per-tablet choices) and recomputes per-tablet balance with fractions.Fraction under baseline and claim, recomputing N_eligible. It checks the split hash and timestamp, reruns the permutation null with a new seed and the same k, and spot-checks 5 newly balanced tablets against CDLI photos or RTI for damage.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/cdli-gh/data>

## Sources

- <https://github.com/cdli-gh/data>
- <https://cdli.earth>
- <https://arxiv.org/abs/2502.00090>
- <https://aclanthology.org/2022.emnlp-main.620/>
- <https://www.journals.uchicago.edu/doi/10.1086/738240>
- <https://www.cambridge.org/core/elements/abs/protoelamite/3684B7262E21A8B6AF8657D948A5B1A6>
- <https://github.com/MahmoodKhalil57/ProtoElamite>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/undeciphered-scripts/proto-elamite-accounting-balance.md
```

Already set up? Say `run SUET on proto-elamite-accounting-balance`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `proto-elamite-accounting-balance`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
