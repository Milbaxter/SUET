# Langton's ant highway conjecture

🕸️ **Graphs, games and automata** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Conjecture: from every finite initial configuration of black cells, Langton's ant eventually builds the period-104 diagonal highway. It is proven that the ant's trajectory is always unbounded (Cohen-Kong), but not that it always reaches the highway.

## What counts as a win

CONFIRMED only for (a) a finite initial configuration of black cells together with a machine-checkable proof that the ant never produces the highway (e.g. a proven different eventual behaviour verified by exact simulation to a provably repeating state), or (b) a formal (Lean/Isabelle) proof of the conjecture. Long transients without the highway are never counterexamples.

## Partial wins

- **p1:** Exhaustive verification of all initial configurations in a 6x6 (or larger) box under a stated symmetry reduction, each with a highway-capture certificate (window at t equals window at t+104 shifted by (+-2,+-2), ant beyond all black cells, and no initial black cell anywhere in the future sweep of the highway) re-checked by an independent simulator on a random 1% sample plus all hard cases.
- **p2:** A rigorous highway-capture lemma (formal proof, or proof reduced to an exhaustively checked finite case analysis re-run independently) stating exactly when a highway, once formed with a given local pattern and no black cells in its future sweep, persists forever.

## How a win is checked

Exact integer simulation by an independent implementation. For highway detection, verify that the ant's local window at time t equals the window at time t+104 shifted by (+-2,+-2), and that the ant is beyond all initial black cells in the drift direction, so the future is provably periodic. For exhaustive claims, re-run a random 1% sample plus all hard cases with the independent simulator.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/pdf/2505.05426>

## Sources

- <https://arxiv.org/pdf/2505.05426>
- <https://en.wikipedia.org/wiki/Langton%27s_ant>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Prove a rigorous 'highway capture lemma': once the ant is beyond the convex hull of the debris in the highway direction with a specific local pattern, it is locked in forever. This turns finite simulation into proof for bounded boxes.
- Exhaustive 6x6 (2^36, about 6.9e10, reduced by 8-fold symmetry) with bit-parallel simulation on 10 cores using the capture lemma.
- Study the generalized ants of arXiv 2505.05426 and look for an obstruction mechanism that could appear in LR (Langton) rules from engineered initial patterns, for example highway-colliding 'eaters'.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Simulation without a proven capture lemma is not a proof that the highway persists.
- Claims of counterexamples based only on long transients (the ant's chaotic phase can last 10^4 or more steps).
- The highway-capture certificate must also show that no initial black cell lies anywhere in the future sweep of the highway, not only ahead of the ant at the moment of detection.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/graphs-games-automata/langton-ant-highway.md
```

Already set up? Say `run SUET on langton-ant-highway`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `langton-ant-highway`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
