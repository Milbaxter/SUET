# Erdos #307 (Barbeau): disjoint prime sets P, Q with (sum 1/p)(sum 1/q) = 1

✏️ **Erdős problems and proofs** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Are there two disjoint finite sets of primes P, Q with (Σ_{p∈P} 1/p)(Σ_{q∈Q} 1/q) = 1? A solution needs |P ∪ Q| >= 60. Weakened coprime versions with 1 allowed have solutions (Cambie, e.g. (1 + 1/5)(1/2 + 1/3) = 1). No solutions are known for the coprime version with 1 excluded.

## What counts as a win

Either (A) explicit disjoint finite prime sets P, Q with the exact Fraction product equal to 1, with every element PROVEN prime (deterministic test below 2^64, or a primality certificate such as ECPP/Pratt/Pocklington above it); or (B) a complete proof that no such sets exist, checkable line by line. 1 and composites are not allowed in P or Q (the 1-allowed variant is already solved).

## Partial wins

- **p1:** A rigorous proof, refereed line by line, that every solution has |P union Q| >= 200 (the known bound is 60).
- **p2:** A rigorous proof that every solution must contain both 2 and 3 in P union Q.

## How a win is checked

(A) Check disjointness, primality certificates (verified with an independent tool, e.g. PARI/GP isprime with a certificate, or sympy for numbers < 2^64), and Fraction(sum)*Fraction(sum) == 1. (B) Referee the proof; specifically check any p-adic or congruence step, since forum AI proofs failed exactly at a divisibility step.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.erdosproblems.com/307>

## Sources

- <https://www.erdosproblems.com/307>
- <https://www.erdosproblems.com/forum/thread/307>
- <https://github.com/google-deepmind/formal-conjectures/blob/main/FormalConjectures/ErdosProblems/307.lean>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Key rigidity, to be re-derived and verified. Let N_P = Σ_{p∈P} ∏P/p. Then N_P is coprime to every p in P, so the equation forces N_P = ∏Q and N_Q = ∏P exactly. Hence the numerator of Σ_P 1/p must be squarefree, coprime to P, and its prime set Q must satisfy N_Q = ∏P. This turns the search into factoring numerators.
- Pile up congruence obstructions toward an impossibility proof: parity (if 2 ∈ P then |Q| is even), and N_P, N_Q modulo 3, 4, 8 and small primes. Show that the two equations N_P = ∏Q and N_Q = ∏P contradict each other modulo some modulus, or via sizes: Σ_P 1/p * Σ_Q 1/q = 1 with loglog-type growth.
- Search: build P greedily from small primes with a target sum s, factor N_P (gmpy2 + ECM via pip-installable tools), reject on square factors or overlap with P, then test Σ_Q = 1/s exactly. Use a meet-in-the-middle on partial sums modulo many small primes to prune.
- Relate to Znam's problem and primary pseudoperfect numbers (the forum notes the 1-allowed variant is solved by them). Search for structural generalisations that exclude 1.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Probable primes are not proven primes.
- P and Q must be disjoint.
- Weakened variants (1 allowed, or coprime integers instead of primes) are already solved and irrelevant.
- Known flawed argument (forum, Nov 2025): 'the LHS is not divisible by any q' does not follow from disjointness.
- Including 1 or a composite in P∪Q (the solved weakened variant).

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/erdos-and-proofs/erdos-307-barbeau-prime-reciprocals.md
```

Already set up? Say `run SUET on erdos-307-barbeau-prime-reciprocals`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `erdos-307-barbeau-prime-reciprocals`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
