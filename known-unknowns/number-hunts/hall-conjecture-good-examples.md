# Hall's conjecture: new good examples beyond 10^29 or beat Elkies' ratio 46.6

🔢 **Number hunts** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

A good example for Hall's conjecture is a pair of positive integers (x, y) with 0 < |x^3 - y^2| < sqrt(x); its Hall ratio is r = sqrt(x)/|x^3 - y^2|. Aanderaa-Kristiansen-Ruud (Math. Comp. 87 (2018)) found 9 new examples and verified that ALL good examples with x < 10^29 are known. The record ratio is Elkies' x = 5853886516781223, |x^3 - y^2| = 1641843, r = 46.600... (recomputed). OEIS A078933 (good-example x values) was edited 2026-10-03. Target: a new record ratio, or new good examples with x > 10^29.

## What counts as a win

CONFIRMED for positive integers x, y with d = x^3 - y^2 != 0 and Hall ratio r = sqrt(x)/|d| STRICTLY GREATER (direction: max) than the largest ratio among all examples listed in OEIS A078933, its b-file and the AKR 2018 table AT VERIFICATION TIME (46.600..., Elkies, on 2026-10-03, context only), compared exactly as rationals: x/d^2 must exceed max(x_i/d_i^2) over the listed examples; x must also be absent from those lists. A 'new' example with x < 10^29 is a BUG (that range is complete). Members of the Danilov-Elkies Fermat-Pell family (r about 1.03) never count as new.

## Partial wins

- **p1:** New good example (partial win): positive x > 10^29 and y with 0 < (x^3-y^2)^2 < x (exact), x absent from OEIS A078933, its b-file and the AKR 2018 table at verification time, and not a member of the Danilov-Elkies Fermat-Pell family.
- **p2:** Completeness extension: an exhaustive search, independently reimplemented by the verifier (AKR continued-fraction method or Elkies lattice method), certifying the complete list of good examples for 10^29 <= x < 10^30 (or a larger strictly-beyond-published range), with logs whose sampled windows the verifier reruns.

## How a win is checked

Python big integers: compute d = x^3 - y^2, check d ≠ 0 and d^2 < x, and compute r with mpmath at 50 digits. Diff x against the downloaded A078933 b-file and the AKR table. For the family check, test whether (x, y) satisfies the Danilov-Elkies parametrization (listed in AKR §table notes / Elkies 2000).

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://oeis.org/A078933>

## Sources

- <https://oeis.org/A078933>
- <https://arxiv.org/pdf/1401.4345>
- <https://arxiv.org/pdf/math/0504579>
- <https://www.ams.org/journals/mcom/2018-87-314/S0025-5718-2018-03298-7/S0025-5718-2018-03298-7.pdf>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Elkies' lattice-reduction method (rational points near the curve y^2 = x^3) applied in windows x ∈ [10^29, 10^33]. It is sub-linear in x and was designed for this.
- Extend AKR's continued-fraction algorithm for sqrt(x) ('good septuples') beyond 10^29 with parallel windows on the 10 cores.
- Search specializations of polynomial identities f^3 - g^2 = h with deg h small (Davenport bound extremals) at rational parameters, then LLL-adjust to integers.
- Use Mordell-curve integral points: for each small k, integral points on y^2 = x^3 + k with huge x give good examples. Use known rank/height data (e.g., Gebel-Pethő-Zimmer style) to find large integral points for |k| up to 1e6.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- The Danilov-Elkies infinite family gives infinitely many good examples with r just above 1. These are not interesting.
- Floating-point sqrt for y; use isqrt and check both y and y+1.
- Examples with x < 10^29 are already complete per AKR.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/hall-conjecture-good-examples.md
```

Already set up? Say `run SUET on hall-conjecture-good-examples`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `hall-conjecture-good-examples`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
