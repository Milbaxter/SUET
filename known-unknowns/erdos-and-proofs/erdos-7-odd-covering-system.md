# MOONSHOT - Erdos #7 / Selfridge: a covering system with distinct odd moduli

✏️ **Erdős problems and proofs** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: needs cluster (for search); pure thought for impossibility · open as of 2026-10-03

## The problem

Is there a finite set of congruences a_i mod n_i, with distinct odd moduli n_i > 1, covering every integer? Erdos offered $25; Selfridge later offered $2000 for an explicit example. Known: impossible with odd squarefree moduli (BBMST 2022). Some modulus must be divisible by 3 (Hough-Nielsen 2019). The lcm L is divisible by 9 or 15. Forum (2026, needs re-verification): L is abundant (>= 945), L >= 11,486,475, L has >= 9 distinct prime factors, and some modulus has >= 4 distinct prime factors.

## What counts as a win

An explicit finite list of (a_i, n_i) with distinct odd n_i > 1 that covers Z, verified by two independent exact checkers. Alternatively, a complete axiom-free proof of impossibility.

## Partial wins

- **p1:** A rigorous proof, checked line by line or in Lean without extra axioms, that L = lcm(n_i) of any odd distinct-moduli covering has at least 10 distinct prime factors (the forum claims >= 9, unrefereed).
- **p2:** A rigorous proof raising the lower bound on L strictly above 11,486,475 (Egeozturk, forum Aug 2026), rechecked by independent code.
- **p3:** An axiom-free Lean formalisation of one of the forum's unrefereed necessary conditions (e.g. Schroeder's >= 9 distinct primes in L, or a modulus with >= 4 distinct primes), checked with #print axioms.

## How a win is checked

Let L = lcm(n_i). If L <= ~2e9, sieve a bitset of residues mod L. Otherwise use a recursive CRT check: process the prime-power factors of L layer by layer, tracking uncovered residue classes, as in Nielsen/Krukenberg-style verifiers. Use two independent implementations, and also check distinctness and oddness.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.erdosproblems.com/7>

## Sources

- <https://www.erdosproblems.com/7>
- <https://www.erdosproblems.com/forum/thread/7>
- <https://www.erdosproblems.com/586>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Run the BBMST distortion/sieve LP numerically to map which prime-exponent profiles of L are not excluded, then search only there.
- Nielsen-style tree search (the method that found a covering with minimum modulus 40) adapted to odd moduli: residue trees over primes 3, 5, 7, 11, ... with exact-cover/ILP at each level.
- Prove the strongest rigorous necessary conditions (e.g., >= 10 distinct primes in L) as a publishable partial result.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- The forum already has a retracted Lean 'proof' that relied on an impossible axiom.
- Moduli must be distinct.
- Odd squarefree moduli are already impossible.
- Covering 'almost all' integers is not covering all of them.
- Schroeder's prime-count papers are forum postings, not refereed; re-verify before building on them.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/erdos-and-proofs/erdos-7-odd-covering-system.md
```

Already set up? Say `run SUET on erdos-7-odd-covering-system`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `erdos-7-odd-covering-system`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
