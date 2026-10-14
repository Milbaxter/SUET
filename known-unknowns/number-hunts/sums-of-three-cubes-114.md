# Sums of three cubes: k = 114, 390, 627, 633, 732, 921, 975, and a fourth representation of 3

🔢 **Number hunts** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: needs cluster · open as of 2026-10-03

## The problem

Find integers x, y, z with x^3 + y^3 + z^3 = k for an open k < 1000 (114, 390, 627, 633, 732, 921, 975 per Wikipedia, edited 2026-09-12), or a fourth representation of 3 beyond (1,1,1), (4,4,-5) and Booker-Sutherland's 2019 solution. Epoch AI lists k = 114 and the new representation of 3 as FrontierMath open problems. Booker-Sutherland used Charity Engine with |z| <= 1e16 range bounds. Also open: primitive representations of k = 192, 375 and 600 (Wikipedia).

## What counts as a win

CONFIRMED only for explicit integers with x^3 + y^3 + z^3 = k exactly in Python big integers, where k is listed as open on https://en.wikipedia.org/wiki/Sums_of_three_cubes AT VERIFICATION TIME, or for k = 3 a triple not equal to any permutation of the representations listed there. Any claimed solution for k = 4 or 5 mod 9 is an error. Nothing else counts as full success.

## Partial wins

- **p1:** Primitive representation: integers x, y, z with gcd(x,y,z) = 1 and x^3+y^3+z^3 = k for k = 192, 375 or 600, provided Wikipedia still lists that k as having no known primitive solution at verification time (non-primitive scalings of solutions for k/8 or k/27 do not count).
- **p2:** Certified search extension: for one open k, an exhaustive search with a published, independently reimplementable algorithm proving no solution in a region strictly larger than the largest region reported searched for that k at verification time (Booker-Sutherland's |z| <= 1e16 as context), with hashed logs; the verifier reruns randomly sampled sub-ranges and audits the coverage argument.

## How a win is checked

Big-integer arithmetic, under 1 second. Compare against Wikipedia's open list and the known k = 3 triples. For p1, check gcd = 1 and Wikipedia's primitive-solution note. For p2, rerun sampled sub-ranges with independent code and audit coverage.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://en.wikipedia.org/wiki/Sums_of_three_cubes>

## Sources

- <https://en.wikipedia.org/wiki/Sums_of_three_cubes>
- <https://epoch.ai/frontiermath/open-problems/sum-of-three-cubes>
- <https://math.mit.edu/~drew/NTW2020.pdf>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Do NOT brute force (Charity Engine already covered |z| ≤ 1e16). Look instead for a structured family: search for polynomial or rational parametric curves on x^3+y^3+z^3 = k of low degree for these specific k, which would give infinitely many solutions. This is a genuinely new idea if it exists.
- Use the Heath-Brown density heuristic to estimate where the smallest solution likely lies for each k, then pick the k with the smallest expected |z| and do a congruence-restricted (mod 9, 7, 13, 27 cubic residue) search around the Booker algorithm's blind spots, if any were documented.
- Use arithmetic geometry: for the cubic surface, look for rational points via Brauer-Manin-free fibrations into conics or genus-1 curves (fix x + y = d dividing k - z^3). Search d over smooth numbers with large prime-power structure.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Repeating Booker-Sutherland's search with fewer resources.
- Sign/permutation duplicates for k = 3.
- Reported solutions for k ≡ 4, 5 mod 9 are impossible, so the computation is wrong.
- k=192, 375 and 600 have no known PRIMITIVE solution (Wikipedia). A primitive representation for these would also be new, but a non-primitive one, such as a scaling of a solution for k/8 or k/27, is not.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/sums-of-three-cubes-114.md
```

Already set up? Say `run SUET on sums-of-three-cubes-114`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `sums-of-three-cubes-114`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
