# Rectilinear crossing number of K_n: resolve n=28 (7233 vs 7234) or beat a best-known drawing

🕸️ **Graphs, games and automata** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

The rectilinear crossing number cr(K_n) is the minimum, over n points in general position in the plane, of the number of 4-point subsets in convex position (each one gives exactly one crossing of straight-line edges). Exact values are known for n<=27 and n=30. For n=28 the value is 7233 or 7234, and for n=29 and n=31..99 there are gaps between the lower and upper bounds. The goal is a point set with fewer crossings than the best known for some n; a 28-point set with 7233 crossings would settle cr(K_28).

## What counts as a win

(A) Upper bound: (1) n distinct points with integer coordinates and no three collinear, checked exactly. (2) The exact number of convex-position 4-subsets (= crossings) is STRICTLY LESS than the best known upper bound for that n at verification time: the minimum of Aichholzer's table (http://www.ist.tugraz.at/aichholzer/research/rp/triangulations/crossing/), OEIS A014540, and any newer paper found by a fresh search. (3) The count is at least the table's lower bound (below it means a bug). For n=28, a set with 7233 crossings resolves cr(K_28). (B) A rigorous proof that cr(K_28) = 7234 also resolves n=28, but only if formally verified or machine-certified (e.g. DRAT-checked) with an independently re-derived encoding. Abstract/pseudo-line order types never count for (A).

## Partial wins

- **p1:** A machine-certified (exhaustive arrangement-cell enumeration in exact arithmetic, independently reproduced, or DRAT-checked) proof that no 28-point set obtained by adding one point to a specified published optimal 27-point set (bestNNN.asc) has 7233 crossings, or the same for a precisely stated symmetric class.
- **p2:** An abstract order type (pseudo-configuration / CC-system) on n points, axioms checked exactly, whose crossing count is strictly below the live best upper bound for that n, with a documented realizability attempt; logged as a stepping stone only, never as a record.

## How a win is checked

Use exact integer orientation tests in Python (arbitrary-precision ints). Assert there are no collinear triples (O(n^3)). Count convex 4-subsets: a 4-set is convex exactly when no point lies inside the triangle of the other three. Brute force is C(n,4), at most 3.9M for n=100, which is trivial. Cross-check with an independent method that counts crossing segment pairs directly, and confirm the checker reproduces the exact counts of downloaded bestNNN.asc files.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <http://www.ist.tugraz.at/aichholzer/research/rp/triangulations/crossing/>

## Sources

- <http://www.ist.tugraz.at/aichholzer/research/rp/triangulations/crossing/>
- <http://www.ist.tugraz.at/aichholzer/research/rp/triangulations/crossing/data/best028.asc>
- <https://oeis.org/A014540>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Start from Aichholzer's bestNNN.asc sets. Do local moves (single-point relocation over the arrangement cells of the other points' lines) and simulated annealing on the exact crossing count with O(n^2) incremental updates.
- Halving-line/k-edge-guided construction: the crossing count is determined by the k-edge vector. Optimize the <=k-edge profile directly, which also matches the lower-bound proof technique, then realize it geometrically.
- Recursive 'double-chain' or 3-fold-symmetric constructions (the records for large n use 3-fold rotational symmetry). Search symmetric configurations, which divides the variables by 3.
- For n=28: start from the n=27 and n=30 optimal sets. Delete or add points and run exhaustive arrangement-cell placement for the last 1-2 points.
- Order-type space search: work combinatorially with abstract order types (CC-systems), then realize them. A non-realizable abstract order type is not a solution.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Collinear triples or floating-point orientation tests. Use exact integers only.
- Counting crossings of K_n in a non-straight-line (topological) drawing. The topological crossing number is a different problem.
- Abstract or pseudo-line order types that are not realizable do not count; an explicit coordinate set is required.
- The table was last modified in 2015. Search the literature for later improvements before claiming.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/graphs-games-automata/rectilinear-crossing-kn.md
```

Already set up? Say `run SUET on rectilinear-crossing-kn`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `rectilinear-crossing-kn`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
