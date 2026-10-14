# Hadamard maximal determinant: new record determinants for orders n not divisible by 4

📊 **Record tables** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

For each order n not divisible by 4, find an n x n {+1,-1} matrix with |det| larger than the best known value. Many records come from Orrick's MaxDet database (pre-2012, now reachable only through the Wayback archive). Butbaia ... Gukov (arXiv:2608.22518 v3, 1 Oct 2026) improved n = 51 and the n = 3 mod 4 orders 103-119 with two-circulant-block constructions; the Math-AI-Caltech/hadamard-maxdet repo holds exact det values with prev fields from the archived database, and EinsteinArena lists 'Hadamard Maximal Determinant (order 51)'. For many orders the Barba bound (n = 1 mod 4) or the Ehlich-Wojtas bound (n = 2 mod 4) is attained (e.g. n = 25, 26, 30, 41, 42, 50), so those records are proven maximal and closed. The research pass claimed maximality is certified for all n <= 22; the auditor could not verify this, so read it from the archive. Live targets are orders whose record is strictly below the residue-class bound, notably n = 3 mod 4 in 55..99 and n = 1, 2 mod 4 above 22 not touched by learning methods.

## What counts as a win

Success means an explicit n x n +-1 matrix whose exact integer |det| (Bareiss on Python ints, cross-checked with sympy) is STRICTLY GREATER (direction: max) than the max, at verification time, of: the archived MaxDet value (Wayback copy referenced by Math-AI-Caltech), the arXiv:2608.22518 / Math-AI-Caltech CSV value, the EinsteinArena order-51 leaderboard, and any newer arXiv value. It must not exceed the residue-class upper bound (Barba for n = 1 mod 4, Ehlich-Wojtas for n = 2 mod 4, or the Ehlich n = 3 mod 4 bound in the form valid for that n range). The order must be one where the previous record was strictly below that bound.

## Partial wins

- **p1:** A maximality certificate: for some order n >= 23 whose record is strictly below its residue-class bound, a re-runnable exhaustive proof (e.g. Gram-matrix enumeration with exact arithmetic and logged case splits that the skeptic re-runs) that the current record determinant is maximal, after confirming no such proof is published.
- **p2:** A frozen Gram target: for an order n whose record is below its bound, an explicit symmetric positive-definite integer matrix G with diagonal n, off-diagonal entries obeying the parity/congruence conditions of Gram matrices of +-1 matrices of that order, det G strictly greater than the square of the live record, and passing the rational (Hasse-Minkowski) equivalence test to n*I, all checked exactly; plus at least n-2 rows of a +-1 matrix realising the leading principal block of G.

## How a win is checked

Compute |det| with fraction-free Bareiss elimination on Python ints (exact), cross-checked with sympy Matrix(...).det(method='bareiss'). Note that det is divisible by 2^(n-1), so report |det|/2^(n-1) as an integer and compare it exactly to the record value. Confirm all entries are +-1. Also compute the bound for the residue class and confirm det <= bound. Pull the record from the Orrick archive or the Math-AI-Caltech CSVs (the *_prev columns give old benchmarks).

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/Math-AI-Caltech/hadamard-maxdet>

## Sources

- <https://github.com/Math-AI-Caltech/hadamard-maxdet>
- <https://arxiv.org/html/2608.22518>
- <http://www.indiana.edu/~maxdet (Orrick archive, referenced by the 2026 paper; not opened this session)>
- <https://einsteinarena.com/>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- For n = 2 mod 4, use two-circulant D-optimal style constructions: two +-1 sequences whose periodic autocorrelations sum to a constant. Search these by SAT/compression methods (Djokovic-Kotsireas compression), which is far smaller than the general space.
- For n = 3 mod 4, use Ehlich's block structure, where the Gram matrix ideally decomposes into 7 or so blocks. Search circulant-block matrices whose Gram matrix matches a near-Ehlich target, as in 2608.22518, but for the untouched orders 55..99.
- For n = 1 mod 4, border a Hadamard or conference-type matrix, or use two-circulant sequences with periodic autocorrelation sum 1 (Barba-type). Brute-force the 'remove a row/col and add one' perturbations from Hadamard matrices of order n-1 and n+3.
- Do simulated annealing on det with rank-1 update formulas (Sherman-Morrison), so a single sign flip costs O(n^2), and run many seeds per order in parallel.
- Use a Gram-matrix-first search: pick a good positive-definite integer Gram target G with large det, then solve for a +-1 decomposition X X^T = G by backtracking.
- First compute the residue-class bound for every order 23..119 and drop orders where the record already equals it (auditor: those are closed); rank the rest by record/bound ratio.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Using floating-point det from numpy.linalg.det. Never use it for certification (n ~ 100 loses precision).
- Normalization confusion between det, det/2^(n-1), and ratio-to-bound. Compare exact integers.
- The Orrick database is archived and partly pre-2012. Check 2608.22518 and any later arXiv for the newest values.
- Order 51 and 103-119 were just improved, so beating them requires beating 2608.22518's matrices.
- Orders where the Barba or Ehlich-Wojtas bound is already attained are closed. Exceeding the bound there means a bug, and matching it is not a record.
- The Ehlich n = 3 mod 4 bound has different block counts for different n ranges (the 7-block form only for n >= 63), so use the correct form.
- The original indiana.edu/~maxdet page is only reachable via the Wayback archive.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/record-tables/hadamard-maxdet-records.md
```

Already set up? Say `run SUET on hadamard-maxdet-records`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `hadamard-maxdet-records`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
