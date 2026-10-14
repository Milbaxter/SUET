# Ideal Prouhet-Tarry-Escott solution of size 11 or 13

🔢 **Number hunts** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Find two disjoint multisets A, B of n integers with sum a^k = sum b^k for k = 1..n-1 (an ideal PTE solution) for n = 11 or n = 13 (or any n ≥ 13). Ideal solutions over Z are known only for n ≤ 10 and n = 12. Status: Wikipedia lists n = 11 and n >= 13 as having no known ideal solution; the n = 12 example is Kuosa-Meyrignac-Chen Shuwen (1999). Coppersmith-Mossinghoff-Scheinerman-VanderKam (arXiv 2304.11254, 2023): no symmetric ideal solution for n = 11 with height <= 3500, n = 13 with height <= 2000, n = 15 with height <= 1100; they found n = 11 symmetric solutions over real quadratic fields. arXiv 2606.07735 (June 2026) treats only degree-3 symmetry questions.

## What counts as a win

CONFIRMED for explicit integer multisets A, B with |A| = |B| = n where n = 11 or n >= 13 is listed as having no known ideal solution on https://en.wikipedia.org/wiki/Prouhet%E2%80%93Tarry%E2%80%93Escott_problem AT VERIFICATION TIME, A and B disjoint as multisets (so the effective size after cancellation is still n), and sum a^k = sum b^k exactly for every k = 1..n-1. Solutions over Gaussian, Eisenstein or real-quadratic integers, and non-ideal solutions (degree < n-1), do not count.

## Partial wins

- **p1:** Symmetric n = 11 frontier: an exhaustive search, independently reimplemented by the verifier, proving no symmetric ideal n = 11 solution with height up to a bound strictly greater than 3500 (CMSV 2023) or the largest published bound at verification time.
- **p2:** Symmetric n = 13 frontier: as in p1 for n = 13, with height bound strictly greater than 2000 (CMSV 2023) or the largest published bound at verification time.

## How a win is checked

Python big integers: check sizes, check that the multisets are disjoint (Counter intersection empty), and compare power sums for k = 1..n-1. Equivalence to known solutions is irrelevant because none exist for these n. Under 1 second. For search-extension partial wins, the verifier reimplements the CMSV-style mod-p obstruction search, reruns it (or sampled height ranges plus the full obstruction tables), and compares the surviving-candidate lists.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://arxiv.org/pdf/2304.11254>

## Sources

- <https://arxiv.org/pdf/2304.11254>
- <https://en.wikipedia.org/wiki/Prouhet%E2%80%93Tarry%E2%80%93Escott_problem>
- <http://www.cecm.sfu.ca/~lisonek/A13.html>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Non-symmetric solutions: CMSV searched only symmetric (B = -A) solutions for odd n. Search non-symmetric n = 11 configurations with their local-solution and CRT-lifting method (required prime divisors of the constant C_n).
- Push the symmetric n = 11 search past height 3500 with their mod-p obstruction method plus more primes (29, 31, 37) and the 10 cores. Height 6000-8000 is a concrete frontier.
- Lattice approach: fix 9 of the 11 values and solve for the remaining two via the quadratic resolvent. CMSV found near-misses with irrational pairs; search nearby for rational ones with LLL.
- Build from n = 12 and n = 10 solutions using Frolov/Tarry transformations (A ∪ (B+d), B ∪ (A+d)), and look for cancellation that drops the size.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Non-ideal solutions (degree k < n-1) are plentiful and do not count.
- Solutions with common elements in A and B have smaller effective size after cancellation.
- Solutions over quadratic fields (like CMSV's α, β examples) are not integer solutions.
- Floating-point power sums.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/pte-ideal-size-11-13.md
```

Already set up? Say `run SUET on pte-ideal-size-11-13`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `pte-ideal-size-11-13`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
