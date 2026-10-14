# 3x3 magic square with >= 7 square entries (second example) or nine squares

🔢 **Number hunts** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

Does a 3x3 magic square of nine distinct perfect squares exist? Only one fully magic 3x3 square of distinct positive integers with 7 square entries is known: Bremner (1999), [[373^2,289^2,565^2],[360721,425^2,23^2],[205^2,527^2,222121]] with magic sum 541875. (Sallows' 1997 8-square square has a failing diagonal and is not fully magic.) Christian Boyer offers prizes for a second 7-square example or for a 9-square example. Rome-Yamagishi (2024) settled all n >= 4. Searches: Buell (center up to 25e24), Boyer (~2.5e27); Wikipedia: any solution has entries > 10^14. A Sept 2026 GitHub project (Kepler71) handled 11 sections by 2-descent/Chabauty, left the (11,4) and (15,8) parameter pairs unresolved, and states the problem is not solved.

## What counts as a win

CONFIRMED if the agent gives a 3x3 matrix of nine distinct positive integers with all 8 line sums equal (exact integer arithmetic), and either (a) at least 7 entries are perfect squares (math.isqrt) and the square is NOT equivalent to Bremner's square [[373^2,289^2,565^2],[360721,425^2,23^2],[205^2,527^2,222121]] (magic sum 541875), nor to any other 7-square fully magic square listed on https://en.wikipedia.org/wiki/Magic_square_of_squares or Boyer's prize pages at verification time; equivalence is tested under the 8 dihedral symmetries after dividing by the largest square common factor; or (b) all 9 entries are distinct squares (prize-level). Semi-magic squares, repeated entries, and zero or negative entries never count.

## Partial wins

- **p1:** Kepler71 open sections: a complete, machine-reproducible determination (rank and generators with a PARI/Magma-checkable certificate, plus descent or Chabauty output) of the rational points relevant to 7-square squares on the (11,4) or (15,8) section that the Kepler71 repo left unresolved, ending either in a new 7-square square or in a proof that the section yields none beyond known ones.
- **p2:** New placement pattern: a machine-reproducible proof that an explicit infinite family/section for a 7-of-9 placement pattern not treated in Kepler71's 11 sections or Bremner's work contains no fully magic 7-square square (or exhibits one), with all rank/descent computations rerunnable by the verifier.

## How a win is checked

Exact integer check of the 8 line sums, distinctness, positivity and isqrt squareness. Normalize by the square part of the gcd and compare all 8 symmetries against the hard-coded Bremner square (already verified magic with sum 541875). For partial wins, rerun the rank/descent computations in PARI (cypari2) or Magma from the stated curve equations and check that the section matches the Kepler71 parametrization.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://en.wikipedia.org/wiki/Magic_square_of_squares>

## Sources

- <https://en.wikipedia.org/wiki/Magic_square_of_squares>
- <https://github.com/Kepler71/magic-square-of-squares>
- <https://arxiv.org/abs/2406.09364>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Use the parametrization: a 3x3 magic square with center e has entries e ± x, e ± y, e ± (x+y), e ± (x-y). With squares, this is a system of arithmetic progressions of three squares (congruent-number curves). Search for 7-square configurations as rational points on a specific genus-1 fibration, using point addition on each fiber instead of brute force.
- Avoid the 11 sections already treated in the Kepler71 repo; the (11,4) and (15,8) parameter pairs are the unresolved ones. Target the other 7-of-9 placement patterns (which two cells are non-square) and compute ranks of the corresponding elliptic fibers with pari (pip cypari2) to find rank ≥ 1 fibers with small-height points.
- Use Bremner's original method (rational points on a quartic surface) to generate infinitely many 7-square candidates in a family, then check distinctness/positivity. Most 'new' finds are scalings, so normalize aggressively.
- Use a modular sieve over center values with residue-class precomputation (mod 2^k, 3, 5, 7, 13) to prune 9-square configurations, as a sanity-limited search, not a frontier push.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Scalings or symmetries of the known Bremner/Sallows square count as the same square.
- Semi-magic (diagonals failing) or repeated entries (Parker Square) do not count.
- Negative or zero entries do not count.
- Floating-point square tests.
- Sallows' 1997 square has a failing diagonal and is NOT the 7-square magic square. Only Bremner's is fully magic.
- Kepler71 handled 11 sections. The (11,4) and (15,8) parameter pairs were left unresolved there, and those are the only sections with a fresh angle.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/magic-square-squares-7.md
```

Already set up? Say `run SUET on magic-square-squares-7`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `magic-square-squares-7`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
