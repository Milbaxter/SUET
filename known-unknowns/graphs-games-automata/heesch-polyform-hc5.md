# Unmarked polyform with Heesch number 5 or more

🕸️ **Graphs, games and automata** · standard · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Find an unmarked polyomino, polyhex or polyiamond that does not tile the plane but admits 5 or more coronas, with Heesch number Hc >= 5 under Kaplan's hole-free-corona definition. Separately, any planar figure with Heesch number >= 7 would beat Bašić's record of 6 for general figures.

## What counts as a win

(1) A cell list defining a connected polyform on the stated grid. (2) Explicit tile placements for coronas 1..5 with no overlaps; each corona surrounds the previous patch completely and is hole-free, matching Kaplan's Hc definition. Each placement must be a genuine grid isometry. (3) A proof that the shape is a non-tiler: a machine-checked UNSAT proof (DRAT or LRAT, checked by drat-trim, lrat-check or cake_lpr) that no (m+1)-corona exists for some m >= 5. That bounds the Heesch number, so the shape cannot tile. (4) Hc STRICTLY GREATER than the best polyform Hc recorded at verification time in the Layr-Labs/heesch challenge (live, including open PRs) and the literature (4 as of 2026-10-03). (5) The Layr-Labs/heesch verifier accepts the submission. For the Hc >= 7 general-figure variant, the same structure is needed, with explicit exact geometry (rational or algebraic coordinates) and an independent overlap check. Hyperbolic-plane results do not count.

## Partial wins

- **p1:** A new polyform (polyomino, polyhex or polyiamond) larger than Kaplan's exhaustive census sizes (more than 19 cells, 17 hexes or 24 iamonds) with Hc = 4 certified exactly: explicit hole-free coronas 1..4 plus a DRAT/LRAT-checked UNSAT proof that no 5-corona exists and a checked non-tiler proof, reproduced by isohedral/heesch-sat.
- **p2:** A polykite or polydrafter with certified Hc strictly greater than the largest Hc reported for that grid in the literature at verification time (literature check required), with explicit coronas and a checked non-tiler proof.
- **p3:** A polyform with certified Hh (holes allowed) strictly greater than the largest Hh reported in Kaplan's census (arXiv 2105.09438) and any newer source, clearly labelled as Hh, with explicit coronas and a checked non-tiler proof.

## How a win is checked

Clone Layr-Labs/heesch and run its verifier, which rebuilds coronas from placements and gates on non-tilerhood with checked UNSAT proofs. Independently, build isohedral/heesch-sat (needs cryptominisat; it builds on macOS with brew), recompute the Heesch number, and require agreement. Re-check the DRAT/LRAT proof with drat-trim.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/isohedral/heesch-sat>

## Sources

- <https://github.com/isohedral/heesch-sat>
- <https://github.com/Layr-Labs/heesch>
- <https://arxiv.org/abs/2105.09438>
- <https://arxiv.org/pdf/2406.16407>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Go beyond the exhaustive sizes: mutate the seven known Hc=4 shapes (add or remove boundary cells, keep them non-tiling) and hill-climb on 'deepest corona reached', using incremental SAT. Hc=4 shapes cluster near 'almost tilers'.
- Engineer 'locally forced' boundaries: design edge words (Wang-style bumps and nicks) on the hex grid so that the first corona is nearly unique and errors propagate only at radius 5 or 6, mimicking Bašić's construction on a lattice.
- Polykites and polydrafters (other heesch-sat grids) are outside the Hc=4 census. A first record there is a meaningful partial result, but check the literature for those grids first.
- Filter candidates quickly with Kaplan's isohedral SAT check (arXiv 2406.16407) to discard tilers, then spend SAT time only on non-tilers with Hc >= 3.
- Allow holes in coronas (Hh) as a separate, clearly labelled partial result. Do not mix it with the Hc record.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Hc (hole-free coronas) and Hh (holes allowed) are different records. Label which one is meant.
- A shape that actually tiles anisohedrally or aperiodically has an infinite Heesch number. Non-tilerhood must be proven, not assumed.
- Coronas that are not simply connected, or that overlap by floating-point slivers in general-figure variants.
- Polyform sizes at or below 19-omino, 17-hex or 24-iamond were already exhaustively searched. A claimed Hc=5 there implies a bug.
- Autonomous bots are submitting to the Layr-Labs challenge. Check its open PRs before claiming.
- Hyperbolic-plane Heesch results (arXiv 2603.27827, unbounded Heesch numbers) are unrelated to the Euclidean record. Do not cite them as progress.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/graphs-games-automata/heesch-polyform-hc5.md
```

Already set up? Say `run SUET on heesch-polyform-hc5`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `heesch-polyform-hc5`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
