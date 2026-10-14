# Erdos #506: minimum number of circles determined by n points, beating or closing the n <= 393 gap

✏️ **Erdős problems and proofs** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Find the minimum number m(n) of circles through >= 3 of n points, where the points are not all on a line or circle. For n > 393, m(n) = F(n) = C(n-1,2) + 1 - floor((n-1)/2) (Elliott 1967, corrected by Purdy-Smith; Balintova-Balint 1994). For n <= 393 it is open. Forum (mzn, 2026-08-18): m(5)=5, m(6)=8, m(7)=11, m(8)=17, with exact-arithmetic configurations (versus F = 5, 9, 13, 19), and m(9) <= 25 = F(9), with no way found to beat it. Forum (Peysakhov, 2026-06-11): 18 circles at n=8.

## What counts as a win

Confirmed: (A) exact coordinates for n >= 9 points, not all collinear and not all concyclic (exact nondegeneracy as in 506.lean), determining strictly fewer than F(n) = C(n-1,2) + 1 - floor((n-1)/2) circles (F(9)=25, F(10)=33, F(11)=41, F(12)=51) AND strictly fewer (direction: min) than the best value posted on the forum thread for that n AT VERIFICATION TIME. Or (B) a complete proof that m(n) = F(n) for every 9 <= n <= 393.

## Partial wins

- **p1:** A rigorous lower-bound proof establishing m(n) exactly for some n in {6, 7, 8} (matching the forum configuration), provided no matching lower-bound proof was already posted on the forum.
- **p2:** A complete proof that m(9) = 25.
- **p3:** A complete proof that the formula m(n) = F(n) holds for all n > N0 with an explicit N0 < 393 (lowering the Elliott/Balintova-Balint threshold), with every constant recomputed exactly.

## How a win is checked

(A) For every non-collinear triple, compute the exact circumcircle (centre and r^2 as rationals or exact field elements), deduplicate and count. Independent re-implementation: union-find on triples using the exact 4-point concyclicity determinant. Confirm the configuration is neither all collinear nor all concyclic, then compare with F(n). (B) Line-by-line refereeing of the constants in the Elliott-type argument; recompute every numeric inequality exactly.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.erdosproblems.com/506>

## Sources

- <https://www.erdosproblems.com/506>
- <https://www.erdosproblems.com/forum/thread/506>
- <https://github.com/google-deepmind/formal-conjectures/blob/main/FormalConjectures/ErdosProblems/506.lean>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Lift to the sphere by inverse stereographic projection. Circles correspond to planes not through the pole and lines to planes through the pole. So minimise (#planes containing >= 3 points) - (#those through the pole). Search orbit configurations of finite rotation groups (prisms, antiprisms, cuboctahedron, Johnson solids, two parallel regular polygons plus poles) and choose the pole on as many plane sections as possible. Use rational points on S^2 for exact arithmetic.
- Extend mzn's n=8 cube and Peysakhov's two-squares configurations by adding points lying on many existing circles, or by moving to 3-fold or 4-fold symmetric families with many concyclic 4-sets and collinear triples. Collinear triples are 'free' because they determine no circle.
- For (B): revisit Elliott's argument with modern tools. Lin-Makhul-Mojarrad-Schicho-Swanepoel-de Zeeuw ('On sets defining few ordinary circles') handles sufficiently large n. Make their constants explicit, and use inversion to turn Melchior/Csima-Sawyer-type ordinary-line inequalities into circle bounds.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Counting lines as circles.
- Floating-point concyclicity.
- n <= 9 data is already on the forum.
- The F(n) formula is proved only for n > 393, so beating it at n <= 8 is already known.
- Nondegeneracy convention: the Lean statement uses 'not all collinear and not all concyclic'; do not switch to 'no three collinear' silently.
- The forum's small-n 'exact' values may be upper bounds only; check whether a matching lower-bound proof was posted before citing them as m(n).
- Degenerate configurations (all concyclic, or all but one collinear) are excluded by the Lean statement; check the exact nondegeneracy in 506.lean.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/erdos-and-proofs/erdos-506-circles-small-n.md
```

Already set up? Say `run SUET on erdos-506-circles-small-n`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `erdos-506-circles-small-n`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
