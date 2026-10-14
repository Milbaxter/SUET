# Erdos #287: unit-fraction representations of 1 must have a gap >= 3, for a full proof

✏️ **Erdős problems and proofs** · standard · tractability ★☆☆☆☆ · compute: pure thought (plus laptop-minutes for certificate checks) · open as of 2026-10-03

## The problem

For distinct integers 1 < n_1 < ... < n_k with Σ 1/n_i = 1, must max(n_{i+1} - n_i) >= 3? The bound 2 is Erdos's theorem. Forum progress: verified for k <= 18 (Lean, 2026-05-27). A good-prime chain (a prime p is 'good' if (p-1)/2 or (p+1)/2 is prime; chain steps p_{j+1} <= 2p_j - 3) rules out n_1 <= 4.099e17. Pr_Huang (2026-09-10) claims a Lean-formalised exclusion of maximum denominators up to ~3.74e60. Full resolution needs good primes (or another obstruction) in every dyadic-type interval, which is a prime-pair-type statement. KentaKitamura (2026-05-28): a counterexample needs k >= 68,634,921,076,157,089,631 (~6.86e19).

## What counts as a win

A complete proof for ALL k, unconditional, checkable line by line. Any analytic input must be a precisely cited published theorem with explicit constants, and the finite range must be covered by the existing (verified) forum certificates or new reproducible ones. Alternatively, an explicit counterexample verified with exact Fractions (realistically impossible given the forum bounds).

## Partial wins

- **p1:** A reproducible (ideally Lean-checked) certificate excluding every counterexample with maximum denominator up to a bound strictly larger than the best exclusion posted on the forum at verification time (~3.74e60, Pr_Huang, as of 2026-10-03), rerun by the verifier.
- **p2:** A rigorous proof raising the lower bound on n_1 strictly above the best forum value at verification time (409,938,931,585,744,826 as of 2026-10-03), with the good-prime chain or other certificate rechecked by independent code.

## How a win is checked

Referee the reduction 'counterexample implies two consecutive integers both forced-excluded'. Check that every forced-exclusion lemma (multiples of a large prime p cannot appear) is proved, including the numerator-divisibility subset check. Check that the analytic theorem's hypotheses hold in every interval with explicit constants. Rerun the gluing to the finite certificates.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.erdosproblems.com/287>

## Sources

- <https://www.erdosproblems.com/287>
- <https://www.erdosproblems.com/forum/thread/287>
- <https://github.com/google-deepmind/formal-conjectures/blob/main/FormalConjectures/ErdosProblems/287.lean>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Broaden the obstruction beyond 'good primes'. Any consecutive pair a, a+1 with a = i*p and a+1 = j*q, where p, q are primes > n_k/K and no subset of {1/i' : i' < K} has numerator divisible by p, forces a gap >= 3. Look for an admissible family of such linear forms where Maynard-Tao (which works in dyadic intervals) guarantees that ANY two primes found give a linked obstruction.
- Use Chen-type results (p prime with (p+1)/2 = P_2) and handle the P_2 case with a second-level exclusion argument for its large prime factor.
- Combine with the exact-sum constraint. The interval [n_1, n_k] with ratio between e and e^2, minus the forced exclusions (densities via Mertens-type sums), must sum to exactly 1. Look for a quantitative contradiction that avoids prime pairs entirely.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- The parity barrier: sieve methods alone cannot produce prime pairs; the verifier must check this explicitly.
- Forum certificates have conditional language; read them exactly.
- Denominators must be positive and > 1 (negative integers give trivial counterexamples).
- KentaKitamura's k >= 68,634,921,076,157,089,631 bound already exists; do not re-announce weaker k bounds.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/erdos-and-proofs/erdos-287-egyptian-gaps.md
```

Already set up? Say `run SUET on erdos-287-egyptian-gaps`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `erdos-287-egyptian-gaps`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
