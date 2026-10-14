# Prove Lychrel numbers exist in a new base (mechanical template-closure proof)

🔢 **Number hunts** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

A Lychrel number in base b never reaches a palindrome under reverse-and-add. No base-10 Lychrel number is proven (196 iterated past a billion digits, Feb 2015). Existence is proven in bases 11, 17, 20, 26 and all powers of 2 (Wikipedia; base 2 example 10110). A 2023 paper, 'On the Construction of Some Lychrel Numbers', works in bases 3-10 with emphasis on base 4 (already a power of 2) and base 10, and appears to construct candidates rather than proofs; its novelty impact is unconfirmed. Target: a rigorous, mechanically checked proof for a base b not of the form 2^k and not in {11, 17, 20, 26}.

## What counts as a win

CONFIRMED only with: (1) a start n and templates T_1..T_k (digit strings with integer-parameter repeated blocks); (2) a proof of closure under reverse-and-add for ALL parameter values that is either formalized (Lean/Coq, no sorry) or reduced to a finite mechanical check. Acceptable reductions are a finite automaton or transducer argument, or an explicit symbolic carry computation in which every parameter-dependent block is shown to produce a constant digit/carry run, together with brute force over all parameters below the threshold; (3) a proof that no template string is a palindrome; (4) a demonstration that n's orbit enters the template set; (5) a base b not in {2^k, 11, 17, 20, 26} and not listed as proven on https://en.wikipedia.org/wiki/Lychrel_number AT VERIFICATION TIME, plus a novelty search (Wikipedia references, OEIS, arXiv, the 2023 construction paper if obtainable). If step (2) only covers parameters up to some P, report 'VERIFIED FOR PARAMETERS <= P, GENERAL CASE UNPROVEN' with no claim. Any step needing 'by inspection' fails unless formalized. A base-10 proof would be a moonshot-level event.

## Partial wins

- **p1:** VERIFIED PROOF, NOVELTY UNCONFIRMED: a proof meeting conditions (1)-(4) in full (all parameters, mechanically checked) for a base b not in {2^k, 11, 17, 20, 26}, where the novelty search cannot rule out prior work (e.g. the 2023 paper could not be obtained).
- **p2:** Audit of the 2023 construction paper: obtain 'On the Construction of Some Lychrel Numbers' and run one of its constructions for a base in 3-10 other than 4 and 8 through this target's mechanical checker, ending either in a full all-parameter proof or in an explicit instance (concrete digit string) where the claimed template closure or non-palindromicity fails.

## How a win is checked

The verifier reimplements reverse-and-add on templates symbolically: digits are run-length blocks with symbolic lengths and the carry is tracked block by block. It must show each symbolic block emits a uniform output run with a uniform outgoing carry. Separately it brute-forces every parameter tuple up to max(threshold, 200). Non-palindromicity is checked symbolically by comparing mirrored block structure. The orbit of n is simulated 1e5 steps and each iterate is matched to a template with a regex. Lean/Coq proofs are built in a clean project with an axiom audit.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://en.wikipedia.org/wiki/Lychrel_number>

## Sources

- <https://en.wikipedia.org/wiki/Lychrel_number>
- <https://oeis.org/A023108>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Automate the search: simulate orbits in base b for many n, compress each iterate with run-length encoding, and detect eventually periodic run-length 'shapes' (as in the base-2 proof for 10110). A shape cycle of period 2-4 with linearly growing blocks is a proof candidate.
- Treat reverse-and-add as a finite-state transducer on paired digit streams (outside-in) with carry states. Search for a regular language L closed under the transducer and disjoint from palindromes, using automaton learning (L*) seeded by simulation traces.
- Prioritize bases b ≡ 2 mod 3 or b = 2^k ± small and other bases close to the proven ones (11, 17, 20, 26). Look for the arithmetic property that made those bases work and generalize it to a family theorem.
- For base 10, prove a weaker statement: e.g., a positive-density set of orbit iterates of 196 lies in a regular language with no palindromes. Checkable but not a Lychrel proof, so not claimed.
- Split run-length templates by block-length parity up front; carry behavior that depends on parity is the most common hidden gap.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Mistaking 'not palindrome after 10^9 steps' for a proof.
- The closure check verified only for small block lengths (needs an argument for all lengths).
- Prior art: some bases may already be done in the 2023 paper or hobbyist sites (Walker, Van Landingham).
- Carry-boundary edge cases where block length 0 or 1 behaves differently.
- Base 4, 8 and 16 are powers of 2 and already proven, so they do not count.
- Run-length templates whose block lengths grow but whose carry behavior depends on block-length parity need a case split, which is easy to miss.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/lychrel-new-base-proof.md
```

Already set up? Say `run SUET on lychrel-new-base-proof`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `lychrel-new-base-proof`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
