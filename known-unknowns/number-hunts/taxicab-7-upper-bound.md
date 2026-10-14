# Improve the upper bound on Taxicab(7) (and higher taxicab bounds)

🔢 **Number hunts** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Ta(n) is the smallest positive integer expressible as a sum of two positive cubes in n distinct ways. Ta(1)..Ta(6) are known; Ta(6) = 24153319581254312065344. Ta(7) is unknown. The best known upper bound is Ta(7) <= 24885189317885898975235988544 (~2.49e28; Boyer 2006, OEIS A011541), which equals 101^3 * Ta(6), a pure scaling construction. Boyer's 2008 JIS paper (Article 08.1.6) gives upper bounds up to Ta(19) and for Cabtaxi(10..30). Target: a smaller N with 7 representations.

## What counts as a win

CONFIRMED if the agent gives an integer N with at least 7 pairwise-distinct unordered pairs {a,b} of POSITIVE integers satisfying a^3+b^3 = N exactly, and N is STRICTLY SMALLER (direction: min) than the best Ta(7) upper bound shown at https://oeis.org/A011541 and https://en.wikipedia.org/wiki/Taxicab_number AT VERIFICATION TIME (24885189317885898975235988544 on 2026-10-03, context only), compared as exact digit strings. Finding such N proves only an upper bound, never the value of Ta(7). Weaker results are partial wins.

## Partial wins

- **p1:** Higher taxicab bound: for some 8 <= n <= 19, an integer N with at least n distinct unordered positive-cube pairs a^3+b^3 = N, strictly smaller than Boyer's bound for Ta(n) in JIS 11 (2008) Article 08.1.6 AND than any smaller bound for Ta(n) found on OEIS A011541 or Wikipedia at verification time (exact digit-string comparison).
- **p2:** Cabtaxi bound: for some 10 <= n <= 30, an integer N with at least n distinct representations as a sum of two cubes of integers (negative or zero allowed, as in the Cabtaxi definition), strictly smaller than the Cabtaxi(n) bound in Boyer's 2008 JIS tables and than any later value found on OEIS or Wikipedia at verification time.

## How a win is checked

Python big integers: compute each a^3+b^3 (or signed cubes for Cabtaxi), check all equal N, check pairs are distinct as unordered pairs with the right sign rules, and compare N to the exact bound strings copied at verification time from OEIS A011541 / Wikipedia / Boyer's JIS tables. Seconds.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://oeis.org/A011541>

## Sources

- <https://oeis.org/A011541>
- <https://en.wikipedia.org/wiki/Taxicab_number>
- <https://cs.uwaterloo.ca/journals/JIS/VOL11/Boyer/boyer-new.pdf>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Exploit the norm-form structure: a^3+b^3 = (a+b)(a^2-ab+b^2). The representation count is governed by factorizations in Z[omega]. Build N as products of many split primes p ≡ 1 mod 3 with small exponents, then solve for representations via the divisor d = a+b and the quadratic for a,b. This searches multiplicatively structured N instead of scanning.
- Rational-point approach: representations of N correspond to rational points on the elliptic curve x^3+y^3=N. Pick cube-free kernels N0 whose curve has rank ≥ 2 and many small-height points, then scale by a common denominator cubed. Choose the denominator by an integer-program over point combinations to minimize the scale.
- Generalize Boyer's 'multiply Ta(6) by c^3' trick: search small cube multipliers c^3 times numbers with 5-6 representations whose prime structure adds representations, instead of only scaling Ta(6).
- Meet-in-the-middle over d = a+b dividing N: for each candidate N (smooth in split primes), enumerate divisors d with d^3/4 ≤ N ≤ d^3 and test discriminant squareness. Parallelize across 10 cores.
- For the partial wins, compare against Boyer's 2008 JIS tables, not Wikipedia (which stops at Ta(12)): higher-n bounds are where scaling constructions may be weakest.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Counting (a,b) and (b,a) as distinct, or allowing zero/negative cubes (that is the Cabtaxi variant).
- Comparing against a misremembered bound. Use the exact OEIS string.
- A claim of 'Ta(7) found' without exhaustive minimality proof is only an upper bound.
- Wikipedia lists only Ta(7)..Ta(12). Use Boyer's JIS tables for higher n, or a 'new' bound may already be beaten.
- OEIS attribution (Wilson v, 2012) is the date of an edit, not the discovery.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/taxicab-7-upper-bound.md
```

Already set up? Say `run SUET on taxicab-7-upper-bound`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `taxicab-7-upper-bound`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
