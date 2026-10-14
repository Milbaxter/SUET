# Lehmer's totient problem: composite n with phi(n) | n - 1

🔢 **Number hunts** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: pure thought · open as of 2026-10-03

## The problem

Is there a composite n with phi(n) dividing n - 1? Any such n is odd and squarefree. Known computational bounds: omega(N) >= 15 and N > 10^26 (Renze, computational notebook, cited in Yamada arXiv 2303.16853); Pinch claims N > 10^30. If 3 | N: omega(N) >= 4*10^7 and N > 10^(3.6*10^8) (Burcsi-Czirbusz-Farkas 2011). A 2025 preprints.org paper claiming elimination of 14-prime composites and a 'GRH-density resolution' is unreviewed and treated as unverified.

## What counts as a win

Full resolution CONFIRMED only with a Lean-formalized proof (no sorry, clean axiom audit), or an explicit composite n with phi(n) | n-1 verified via a complete prime factorization (every factor proven prime). Computational bound improvements are partial wins, judged against the best bounds stated at https://arxiv.org/pdf/2303.16853 and https://en.wikipedia.org/wiki/Lehmer%27s_totient_problem AT VERIFICATION TIME; reproducing omega >= 15 is a regression test, not a result. Unreviewed preprints claiming resolution never count.

## Partial wins

- **p1:** omega(N) >= 16: a rigorous, exhaustive computer proof, independently reimplemented by the verifier with identical branch-closure reasons on every branch, using exact rational arithmetic for every product p/(p-1) bound.
- **p2:** Certified N > 10^30: a rigorous, exhaustive, independently reimplemented computer proof that any Lehmer number exceeds 10^30 (certifying Pinch's uncertified claim), or a strictly larger bound, with a published branch log.

## How a win is checked

The verifier first reproduces Cohen-Hagis omega >= 14 and Renze's omega >= 15 as regressions. It then independently reimplements the branch-and-bound over increasing prime tuples using the Lehmer constraints (N odd and squarefree, p_i does not divide p_j - 1, and the condition on prod p/(p-1) with exact rationals) and diffs the branch-closure logs. For a counterexample: factor n, compute phi(n) exactly, and check divisibility.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://en.wikipedia.org/wiki/Lehmer%27s_totient_problem>

## Sources

- <https://en.wikipedia.org/wiki/Lehmer%27s_totient_problem>
- <https://math.dartmouth.edu/~carlp/Carmichael_giuga.pdf>
- <https://arxiv.org/pdf/2303.16853>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Branch-and-bound over increasing prime tuples in the style of Cohen-Hagis/Renze (N odd, squarefree, p_i not dividing p_j - 1, exact-rational bounds on prod p/(p-1)), parallelized on the 10 cores, aiming at a reproducible full branch log for omega = 15 -> 16.
- Combine with Carmichael structure: any Lehmer number is a Carmichael number with extra constraints. Use Pinch's Carmichael tables to test structural conjectures quickly (sanity, not proof).
- Use p-adic overflow constraints (as in the 2025 preprint) but derive them rigorously and check every claimed lemma symbolically.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Unreviewed preprints claiming resolution.
- Floating-point products of p/(p-1) in branch bounds; use exact rationals.
- Confusing Lehmer's totient problem with Lehmer's Mahler-measure problem.
- ω ≥ 15 / N > 10^26 is already known (Renze), and Pinch claims N > 10^30.
- arXiv 2003.13055 (Agama) is not a usable branch-and-bound method. Do not build on it.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/lehmer-totient.md
```

Already set up? Say `run SUET on lehmer-totient`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `lehmer-totient`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
