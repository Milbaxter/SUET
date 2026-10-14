# A fifth primitive solution to a^5 + b^5 + c^5 + d^5 = e^5 (or a third all-positive one)

🔢 **Number hunts** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: needs cluster · open as of 2026-10-03

## The problem

Only four primitive solutions of x1^5 + x2^5 + x3^5 + x4^5 = x5^5 in nonzero integers are known: Lander-Parkin 1966 (144^5 = 27^5+84^5+110^5+133^5), Scher-Seidl 1996 (14132^5 = (-220)^5+5027^5+6237^5+14068^5), Frye 2004 (85359^5 = 55^5+3183^5+28969^5+85282^5), and Braun 2026 (1956878^5 = 719115^5+1331622^5+(-1340632)^5+1956213^5; all four verified in Python). Target: a fifth primitive solution, or a third solution with all terms positive. J. M. Braun found the fourth (arXiv 2603.05549, 2026-03-05, revised 2026-08-21) with an optimized meet-in-the-middle search and makes no completeness claim below e = 1956878.

## What counts as a win

CONFIRMED for nonzero integers x1..x5 with x1^5+x2^5+x3^5+x4^5+x5^5 = 0 exactly (the 5.1.4 equation with signs moved across), gcd = 1, no pair x_i = -x_j, and the 5-tuple not equal, up to permutation and global sign, to any primitive solution listed on https://en.wikipedia.org/wiki/Euler%27s_sum_of_powers_conjecture or in arXiv 2603.05549 AT VERIFICATION TIME (four on 2026-10-03: 144, 14132, 85359, 1956878 as the largest absolute terms). Flag additionally if a, b, c, d are all positive (only the third such solution).

## Partial wins

- **p1:** Certified completeness bound: an exhaustive search, independently reimplemented by the verifier, proving that the known primitive solutions are the only ones with largest absolute term up to a bound B strictly greater than the largest exhaustive-search bound stated in the literature (Braun 2026 and references therein) at verification time, with hashed logs and sampled windows rerun.
- **p2:** All-positive completeness bound: as p1 restricted to all-positive a, b, c, d (only 144 and 85359 known), with B strictly greater than the largest published exhaustive bound for the all-positive case at verification time.

## How a win is checked

Python big integers: evaluate the sum of fifth powers, gcd, the trivial-pair check, and a multiset comparison (with both global signs) against the four hard-coded known tuples. Under 1 second. For completeness partial wins, the verifier reimplements the meet-in-the-middle kernel with the mod-30/11-adic/5-adic filters, reruns sampled windows and audits the coverage argument.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/abs/2603.05549>

## Sources

- <https://arxiv.org/abs/2603.05549>
- <https://en.wikipedia.org/wiki/Euler%27s_sum_of_powers_conjecture>
- <https://oeis.org/A347773>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Reproduce Braun's meet-in-the-middle with the classical filters (x ≡ x^5 mod 30 gives a+b+c+d ≡ e mod 30; 11-adic and 5-adic constraints) and extend e beyond 1956878 in a different residue class partition, coordinating on regions his paper says it covered.
- Signed-term specialization: two of the four known solutions have one negative term. Search the 2+2 split (a^5+b^5 = e^5 - c^5 + ... ) form with sorted-sum merging of a^5+b^5 and e^5-c^5-d^5 tables, which needs much less memory.
- Structural pattern: Braun notes structural regularities across known counterexamples. Test whether they predict residue or ratio constraints that shrink the search by large factors.
- Elkies-style: look for rational curves or elliptic fibrations on the 5.1.4 threefold through known points (e.g., planes x1 + x2 = λ(x3 + x4)), and search fibers with positive rank.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Permutations, global sign flips and rearrangements across the equals sign of the four known solutions are not new.
- Non-primitive multiples.
- Trivial solutions with cancelling pairs (x, -x).
- Brute force below e ≈ 2e6 likely repeats Braun's searched space.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/fifth-powers-5-1-4-new-primitive.md
```

Already set up? Say `run SUET on fifth-powers-5-1-4-new-primitive`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `fifth-powers-5-1-4-new-primitive`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
