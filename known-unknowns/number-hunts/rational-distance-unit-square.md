# Rational distance problem for the unit square (four-distance problem)

🔢 **Number hunts** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Is there a point (x, y) in the plane with rational distances to all four vertices of the unit square? Points on a diagonal, midline or edge are proven impossible (Yang Ji, arXiv 2105.05250), along with some prime-related cases. An unreviewed 2026 GitHub project (Mulatram-UwU, AI agent with human GPG-signing) claims an exhaustive search ruling out common denominators Q <= 5e10 (headline 2e10), with Lean checks of the reduction and search logic, and states it is not a solution.

## What counts as a win

CONFIRMED only for explicit rationals x, y (exact fractions) such that x^2+y^2, (x-1)^2+y^2, x^2+(y-1)^2 and (x-1)^2+(y-1)^2 are all squares of rationals: each value in lowest terms has a perfect-square numerator and denominator, checked with fractions.Fraction and math.isqrt. Three-distance points never count.

## Partial wins

- **p1:** New impossible family: a complete proof that no point on an explicit infinite rational curve (e.g. a line through the center with a fixed non-axis, non-diagonal slope t, or a whole one-parameter family of such lines) has rational distances to all four vertices, beyond the diagonal/midline/edge cases of arXiv 2105.05250, with all genus/rank/Chabauty computations rerunnable by the verifier and the written argument checked line by line (Lean preferred).
- **p2:** New local obstruction: an extension of the congruence condition of arXiv 1904.12097 to additional primes, with a complete proof and a brute-force check over residues that the verifier reruns, ruling out a stated positive proportion of height-bounded candidates not excluded by the published condition.

## How a win is checked

Python fractions.Fraction exact computation and isqrt square tests on reduced numerator/denominator. For partial wins, line-by-line proof check plus rerun of all computer-algebra steps.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/pdf/1904.12097>

## Sources

- <https://arxiv.org/pdf/1904.12097>
- <https://arxiv.org/abs/2105.05250>
- <https://github.com/Mulatram-UwU/rational-distance-problem>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Three-distance solutions form a known parametrized surface (infinitely many points rational to three vertices). Parametrize it via a K3/elliptic fibration and search for fibers where the fourth distance condition gives an elliptic curve of positive rank, which is far more efficient than denominator scanning.
- Use symmetry: impose the point on a rational line through the center with slope t (not the diagonals/midlines already excluded). Each t gives a curve. Compute genus and use Chabauty on low-genus cases to prove impossibility families.
- Use local-global obstructions: extend the 2019 congruence condition (arXiv 1904.12097) to more primes to rule out larger fractions of height-bounded candidates.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Only three of four distances rational: infinitely many such points are known.
- Floating-point near-misses.
- Trusting the unreviewed 5e10 bound as established fact.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/rational-distance-unit-square.md
```

Already set up? Say `run SUET on rational-distance-unit-square`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `rational-distance-unit-square`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
