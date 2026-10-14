# New high-quality abc triples (q >= 1.4, c > 10^20) or beat Reyssat's 1.6299

🔢 **Number hunts** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

An abc triple is coprime positive a + b = c with rad(abc) < c; its quality is q = log c / log rad(abc). Bart de Smit's list has 241 known triples with q >= 1.4 (last updated 2019-03-02) and states the list of good triples is COMPLETE up to 20 digits (Demeyer, June 2007), so new ones can only have c > 10^20. The record is q = 1.6299 (Reyssat: 2 + 3^10*109 = 23^5). Target: a new record q, or new q >= 1.4 triples with c > 10^20.

## What counts as a win

CONFIRMED for coprime positive integers a + b = c with complete prime factorizations of a, b and c (every factor proven prime: BPSW plus ECPP/Pocklington above 2^64) and quality q = log c / log rad(abc), computed at 50 digits, STRICTLY GREATER (direction: max) than the highest quality on https://pub.math.leidenuniv.nl/~desmit/abc/index.php?set=2 AT VERIFICATION TIME (1.6299, Reyssat, on 2026-10-03, context only) and than any higher value found in a same-day literature check. New q >= 1.4 triples below the record are partial wins (partial win). Any 'new' triple with c <= 10^20 is a BUG (that range is complete).

## Partial wins

- **p1:** New good triple (partial win): coprime a + b = c with c > 10^20, complete proven factorizations, q >= 1.4 at 50 digits, and the sorted (min(a,b), c) pair absent from the de Smit q >= 1.4 list at verification time; labelled 'new relative to the de Smit list' unless also absent from ABC@Home and Rubin's results.
- **p2:** New top-20 triple: a triple as in p1 whose quality exceeds the 20th-highest quality on the de Smit list at verification time (about 1.55 per the researcher).

## How a win is checked

Recompute the sum and gcd, re-factor a, b and c independently (sympy.factorint, plus ECPP via PARI isprime(...,2) for large factors), check c > 10^20, compute rad and q with mpmath at 50 digits, and string-diff against the freshly scraped de Smit list (and ranking for p2).

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://pub.math.leidenuniv.nl/~desmit/abc/index.php?set=2>

## Sources

- <https://pub.math.leidenuniv.nl/~desmit/abc/index.php?set=2>
- <https://arxiv.org/pdf/1409.2974>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- LLL on polynomial identities (Dokchitser / Browkin-Brzezinski style): find polynomials f, g, h with f + g = h and small radical degree, specialize at rational points, and LLL-reduce to make the parts smooth/powerful.
- Continued fractions of n-th roots: a triple like 2 + 3^10*109 = 23^5 comes from near-equalities x^n ≈ y^m. Scan convergents of log(p)/log(q) for small primes p, q and test the error term for smoothness.
- Mason-Stothers extremal polynomial families (Davenport-Zannier pairs, Belyi maps / dessins d'enfants) specialized at integers. Search over the catalog of genus-0 dessins with few edges.
- Search S-unit equations x + y = z with x, y, z supported on the first ~12 primes with high exponents (de Weger's method). Solve with LLL and keep near-powerful solutions.
- Aim every construction at c > 10^20; anything smaller is already enumerated completely.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Incomplete factorization: a large composite cofactor treated as prime inflates rad and lowers q wrongly, or a missed square factor lowers rad and fakes high q.
- Duplicates up to swapping a and b.
- The list being stale since 2019 means a 'new' triple may be in ABC@Home or Frank Rubin's results; label carefully.
- The list is complete for c up to 20 digits (Demeyer 2007), so 'new' small triples are bugs.
- Infinite polynomial families (e.g., 1 + (x^n - 1) = x^n with smooth x^n-1) almost always give q < 1.4.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/number-hunts/abc-high-quality-triples.md
```

Already set up? Say `run SUET on abc-high-quality-triples`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `abc-high-quality-triples`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
