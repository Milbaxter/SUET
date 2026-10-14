# The missing Moore graph (degree 57, diameter 2)

🕸️ **Graphs, games and automata** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: pure thought · open as of 2026-10-03

## The problem

Does a 57-regular graph on 3250 vertices with diameter 2 and girth 5 exist? This is srg(3250,57,0,1), the last open case of the Hoffman-Singleton theorem.

## What counts as a win

CONFIRMED only for an explicit adjacency list on 3250 vertices that is 57-regular with A^2 + A - 56I = J, checked exactly in integers. A non-existence argument is NOT a confirmed claim unless fully formalized in Lean or Isabelle and checked. Partial wins are logged, not claimed.

## Partial wins

- **p1:** A computer-verified exclusion (reproducible code, exact arithmetic; formal proof preferred) of automorphisms of a specific odd prime order p, or of a specific automorphism-group order, that is not already excluded in the literature (arXiv 2606.29183 and its references, checked fresh); if it relies on 2606.29183 (unrefereed), the dependency must be stated.
- **p2:** An independent machine-checked (Lean/Isabelle) or fully reproducible exact-computation verification of the arXiv 2606.29183 theorem that a Moore graph of degree 57 has no involutory automorphisms.

## How a win is checked

Load the adjacency matrix as a 3250 x 3250 int8 array. Check symmetry, zero diagonal and all row sums equal to 57. Compute A@A + A in int32 and compare with 56I + J exactly. For partial results, independently re-run the eigenvalue and character-table or fixed-point arguments, for example with GAP or sympy, in exact arithmetic.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/html/2606.29183>

## Sources

- <https://arxiv.org/html/2606.29183>
- <https://www.mdpi.com/2073-8994/16/12/1563>
- <https://arxiv.org/pdf/2210.09577>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Build on the 'no involutions' result: push the fixed-subgraph analysis to elements of order 3, 5, 7 and 11, using eigenvalue multiplicity (1729/1520) and trace constraints. A computer-checked exclusion of a prime order is a partial win.
- Search for constructions with large odd-order groups acting semiregularly (orbit matrices or quotient matrices over Z_{2·5^3·13} subgroups), using CP-SAT on orbit matrices.
- Mine 'potential subgraphs' work (MDPI Symmetry 16(12):1563) for forbidden configurations, and encode them as SAT on small neighbourhood structures.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Long history of incorrect non-existence claims. Treat any 'proof' with extreme suspicion.
- Floating-point eigenvalue checks are not proofs.
- 2606.29183 is a recent single-author preprint and has not been refereed. Partial results that build on it inherit that risk, so state the dependency explicitly.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/graphs-games-automata/moore-graph-57.md
```

Already set up? Say `run SUET on moore-graph-57`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `moore-graph-57`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
