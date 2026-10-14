# Conway's 99-graph, srg(99,14,1,2)

🕸️ **Graphs, games and automata** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Does a strongly regular graph with parameters (99,14,1,2) exist? Equivalently: is there a 99-vertex graph in which every edge lies in exactly one triangle and every non-adjacent pair has exactly two common neighbours? Conway offered $1000 for an answer.

## What counts as a win

CONFIRMED only for an explicit 99 x 99 symmetric 0/1 adjacency matrix with zero diagonal satisfying A^2 = 14I + A + 2(J - I - A), checked exactly in integers. Non-existence requires a formal (Lean/Isabelle) proof or a fully reproducible exhaustive computation with UNSAT certificates checked by drat-trim/cake_lpr and an independently re-derived encoding; never a confirmed claim without that. Near misses (any fraction of constraints satisfied) are never results.

## Partial wins

- **p1:** A DRAT/LRAT-checked (independently re-encoded) proof that no srg(99,14,1,2) admits a specified automorphism (stated prime order and fixed-point/cycle structure) that is not already excluded by arXiv 2308.02978, its refinements, or arXiv 2608.11211 (literature check at verification time).
- **p2:** An independent machine-checked re-derivation (Lean/Isabelle, or SAT with DRAT-checked proofs from an independent encoding) of the forced-structure reduction of arXiv 2608.11211.

## How a win is checked

Exact integer matrix identity check in numpy (int32). For non-existence or UNSAT claims, require DRAT/LRAT proofs checked by drat-trim or cake_lpr, together with an independent re-derivation of the encoding.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/abs/2608.11211>

## Sources

- <https://arxiv.org/abs/2608.11211>
- <https://arxiv.org/pdf/2308.02978>
- <https://github.com/tonykoval/hunting-srg99>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Prescribe automorphism groups not yet excluded by the 2308.02978 analysis (orders 3 and 11 actions) and solve the orbit-matrix SAT problem.
- Local structure: each vertex neighbourhood is 7 disjoint edges, and the graph contains 693 triangles that form a partial geometry or linear space. Search for the corresponding pg(2,6,1)-like geometry with exact cover.
- Use the 2608.11211 forced-structure reduction as a starting point with a different SAT encoding (pysat with cadical, cube-and-conquer over 10 cores).

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Many repos claim 'near misses'. A near miss is not a result.
- Do not confuse it with Conway's other $1000 problems or with srg(99,...) relatives.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/graphs-games-automata/conway-99-graph.md
```

Already set up? Say `run SUET on conway-99-graph`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `conway-99-graph`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
