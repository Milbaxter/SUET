# Smaller (k,g)-graph than the cage record

🕸️ **Graphs, games and automata** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

n(k,g) is the order of a smallest k-regular graph of girth g. Construct a k-regular graph of girth at least g with fewer vertices than the best known upper bound for some open (k,g), e.g. (3,13) (lower bound 202) or (4,10) (record 320 since arXiv 2511.07247).

## What counts as a win

(1) Explicit adjacency list on N vertices. (2) Simple graph, every vertex of degree exactly k. (3) Girth computed exactly is >= g. (4) N STRICTLY LESS than the best known upper bound for n(k,g) at verification time, taken as the minimum over DS16 (https://www.combinatorics.org/ojs/index.php/eljc/article/download/DS16/pdf/), the latest version of arXiv 2511.07247, and every newer source found by a fresh arXiv/Scholar search for '(k,g)-cage'. (5) N >= Moore bound for (k,g). Girth-diameter cages and mixed cages do not count.

## Partial wins

- **p1:** A k-regular girth-g graph whose order equals the live best known upper bound for an open (k,g) but which is non-isomorphic (nauty/pynauty canonical form) to every published record graph for that (k,g) that can be downloaded (House of Graphs, the 2511.07247 data, or the record authors); not claimable if no record graph is obtainable for comparison.
- **p2:** A graph strictly beating a live entry of the separate girth-diameter cage table (arXiv 2511.21144) or the mixed-cage table (arXiv 2506.20003), verified exactly against that table's own definition; logged as a partial win, never as a cage record.

## How a win is checked

In networkx, check that all degrees equal k. Compute the girth with an independent BFS-from-every-vertex shortest-cycle routine and cross-check against networkx.girth (networkx >= 3.1). Assert girth >= g. Assert the Moore bound <= N < the record. Search arXiv and Google Scholar for '(k,g)-cage' newer than the survey before claiming.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/abs/2511.07247>

## Sources

- <https://arxiv.org/abs/2511.07247>
- <https://www.combinatorics.org/ojs/index.php/eljc/article/download/DS16/pdf/>
- <https://arxiv.org/pdf/2201.07117>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Excision from generalized polygons: delete carefully chosen vertex sets from incidence graphs of generalized quadrangles and hexagons (g = 8, 12) to get g = 7, 9, 11, 13 graphs. Search excision sets with SA.
- Voltage lifts with girth constraints: base graph plus a voltage assignment in Z_n or a small nonabelian group. Girth equals the minimum length of a closed walk with net voltage zero, which is computable on the quotient. Enumerate cheaply and exhaustively for small base graphs.
- Cayley graphs of PSL(2,q), PGL(2,q) and their subgroups and extensions with generators of order 2 or 3 (the 272 record is a Cayley graph of AGL(1,17)). Do an exhaustive generator search for q up to about 50.
- Exoo-style edge-swap local search starting from the record graph with a few vertices deleted and 'deficient' vertices repaired, as in arXiv 2511.07247.
- Mixed-integer or CP-SAT completion: fix a large symmetric skeleton and let CP-SAT add edges subject to no short cycles.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Using a stale record. The 2025-2026 paper changed eleven entries, and others may have changed since.
- A graph whose girth is exactly g but which is not regular. Biregular and 'record mixed' graphs do not count.
- A girth computed on the quotient or voltage graph instead of the lift.
- Confusing girth-diameter cages or (k,g)-graphs with excess with ordinary cages.
- The attribution of rec(3,13)=272 and its 'Cayley graph of AGL(1,17)' structure was not verified. Do not rely on it, and read DS16 Table 1 directly.
- Girth-diameter cages (arXiv 2511.21144) and mixed cages (2506.20003) have separate record tables and do not count.
- The researcher's angle that the 272 record is a Cayley graph of AGL(1,17) is unverified; use it only as a search idea.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/graphs-games-automata/cage-upper-bounds.md
```

Already set up? Say `run SUET on cage-upper-bounds`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `cage-upper-bounds`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
