# Perfect triangle: integer sides, rational medians, integer area

🔢 **Number hunts** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Is there a triangle with rational sides, all three medians rational, and rational area (a Heron triangle with three rational medians)? It is conjectured that none exists. Buchholz-Rathbun showed infinitely many Heron triangles with two rational medians, and Hone (2024) gave explicit formulas linking these to Somos sequences and elliptic curves. 'No perfect triangle is isosceles' is proven.

## What counts as a win

CONFIRMED only for an explicit triangle with positive integer sides a, b, c satisfying the strict triangle inequality such that 2b^2 + 2c^2 - a^2, 2a^2 + 2c^2 - b^2 and 2a^2 + 2b^2 - c^2 are all perfect squares (so all three medians are rational) and 16*Area^2 = (a+b+c)(-a+b+c)(a-b+c)(a+b-c) is a perfect square. Rescalings and degenerate triangles never count.

## Partial wins

- **p1:** Non-existence on a new subfamily: a proof that no perfect triangle lies in an explicit infinite subfamily (e.g. a one-parameter family with a fixed angle, or a fiber of Buchholz's two-median elliptic family) not already treated in arXiv 1910.06888, Buchholz-Rathbun or Hone 2024, with every rank/descent/Chabauty computation rerunnable in PARI or Magma by the verifier and the written argument checked line by line.
- **p2:** New two-median family: an explicit infinite family of Heron triangles with two rational medians plus an additional rational quantity (e.g. a rational angle bisector), verified symbolically, and shown not to be a rescaling or reparametrization of the Buchholz-Rathbun or Hone families; reported without claim unless an independent expert-style check confirms novelty.

## How a win is checked

Exact integer arithmetic with isqrt on four quantities, under 1 second. For partial wins, symbolic verification of the family identities (sympy) and rerunning of the arithmetic-geometry computations.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/abs/2401.05581>

## Sources

- <https://arxiv.org/abs/2401.05581>
- <https://arxiv.org/pdf/1910.06888>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Work on Buchholz's one-parameter family of elliptic curves for two-rational-median Heron triangles. The third-median condition defines a further double cover. Search the base for parameters where the cover's fiber has rank ≥ 1, using cypari2 ellrank, instead of searching triangles directly.
- Use Hone's Somos-sequence formula to generate the two-median family to enormous height cheaply, then sieve the third-median square condition mod many primes before any big-integer test.
- Prove non-existence on a specific infinite subfamily (e.g., triangles with one angle fixed, cf. arXiv 1910.06888) by Chabauty or descent. This is a checkable partial result.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Confusing 'integer medians' with 'rational medians' (scaling by 2).
- Degenerate triangles.
- Families that are just rescalings of known two-median triangles.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/perfect-triangle.md
```

Already set up? Say `run SUET on perfect-triangle`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `perfect-triangle`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
