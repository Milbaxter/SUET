# Antihydra (BB(6) Cryptid): prove non-halting (Collatz-like / Mahler 3/2 problem)

🔢 **Number hunts** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: pure thought · open as of 2026-10-03

## The problem

Antihydra (1RB1RA_0LC1LE_1LD1LC_1LA0LB_1LF1RE_---0RA) halts iff an iterated map halts: per the bbchallenge wiki, iterate H(n) = floor(3n/2) starting from 8, halting iff the number of odd iterates exceeds twice the number of even ones (exact definition and start state must be quoted from the wiki). Proving non-halting requires showing the parities of the iterates are never too odd-heavy, closely related to Mahler's 3/2 problem. Simulated to 2^38 rule steps without halting; heuristic halting probability about 2.884e-28,723,042,565. Public AI autoresearch repos (mfornet/antihydra-autoresearch; golirt1/antihydra-notes, which states 'not a proof') exist; no 2026 proof is known.

## What counts as a win

CONFIRMED only with a complete proof of non-halting (or an explicit halting step count) that is (a) formalized in Lean or Rocq with no sorry/admit and an axiom audit showing only standard axioms, with the formal statement shown to match the Turing machine semantics or the wiki's proven-equivalent reformulation (equivalence proof included or cited from the Rocq repo); or (b) for halting, an exact step count reproduced by two independent accelerated simulators AND a naive spot-check of the rule translation. Heuristic, probabilistic or 'verified up to N' arguments never count. Any proof that would also resolve Mahler's 3/2 problem gets extra scrutiny.

## Partial wins

- **p1:** Simulation frontier: an independently reproducible simulation of the Antihydra map strictly beyond the depth stated on https://wiki.bbchallenge.org/wiki/Antihydra at verification time (2^38 rule steps as context), with no halt, publishing checkpoint values (iterate hash and counter) at fixed step indices that a second, independently written simulator reproduces exactly.
- **p2:** Formal reduction: a Lean/Rocq-checked theorem (no sorry, clean axiom audit) reducing Antihydra non-halting to a strictly different explicit statement (e.g. about the binary/3-adic digits of the orbit, or a specific automatic/morphic sequence), where the reduction is not already stated on the wiki page or in the mfornet/golirt1 repos at verification time.

## How a win is checked

The verifier runs lake build / coqc in a clean environment, prints axioms, and diffs the top-level theorem statement against the wiki's formal definition. For p1 it reruns the published checkpoints with its own simulator.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://wiki.bbchallenge.org/wiki/Antihydra>

## Sources

- <https://wiki.bbchallenge.org/wiki/Antihydra>
- <https://github.com/mfornet/antihydra-autoresearch>
- <https://github.com/golirt1/antihydra-notes>
- <https://benbrubaker.com/why-busy-beaver-hunters-fear-the-antihydra/>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Look for a proof of a weaker but sufficient statement: Antihydra only needs the running count (2*#even - #odd) to stay ≥ 0 from a SPECIFIC start, not equidistribution. Explore 2-adic structure: the parity sequence of floor((3/2)^n * x) is determined by binary digits of x * 3^n. Seek a combinatorial invariant on 3-adic/2-adic expansions for that one orbit.
- Automaton approach: test whether the parity sequence from this start is (provably) a morphic/automatic sequence on some subsequence, which would give a closed-form count. Searching for this computationally is fast; finding it would be a new idea.
- Transfer from known results: Dubickas/Flatto-Lagarias-Pollington bounds on fractional parts of ξ(3/2)^n give partial distribution results. Check whether any known bound on lim sup/lim inf of the parity density already suffices for a tail version, leaving a finite check.
- Read the existing autoresearch repos first and document their negative results to avoid repeating dead ends.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Confusing simulation depth with proof.
- Subtle off-by-one in the counter or start state when reformulating.
- A purported proof that would also prove Mahler's 3/2 conjecture outright is almost certainly wrong.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/antihydra-collatz-cryptid.md
```

Already set up? Say `run SUET on antihydra-collatz-cryptid`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `antihydra-collatz-cryptid`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
