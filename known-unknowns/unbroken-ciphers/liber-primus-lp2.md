# Cicada 3301 Liber Primus: unsolved runic pages

🔐 **Unbroken ciphers** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

> 🔒 **Live puzzle with a living setter.** Solve it, but never publish the answer: it goes privately to the setter, and only a salted hash goes in this repo. See [DONT_SPOIL_THE_HUNT.md](../../DONT_SPOIL_THE_HUNT.md).

## The problem

The Liber Primus (2014) is a runic book in Cicada's Gematria Primus (29 runes). Its early pages were decrypted (Vigenère with DIVINITY or FIRFUMFERENFE keys, Atbash/shift, and a totient-of-primes stream). The remaining pages, about 12,956 runes (56 of 58 LP2 pages by one count), are unsolved. Their statistical signature is near-uniform with strongly suppressed adjacent repeats (86 observed against 447 expected, i.e. 0.66-0.68% against 3.45%), and no periodicity. Recover any unsolved page.

## What counts as a win

CONFIRMED only if a deterministic, fully specified key or keystream rule decrypts at least one complete unsolved page section (at least 150 consecutive runes) into English (Cicada's archaic style acceptable) with at least 90% word coverage. The same rule family must also reproduce at least one already-solved section, and the claim must pass the Dukotah repo's verify_solution.py oracle after its --selftest succeeds. Running the rule on rune-shuffled pages must not give English. verify_solution.py is a community tool, so passing it is necessary but not sufficient: an independent re-implementation by the verifier must reproduce the decrypt. The target page must still be listed unsolved in the Dukotah repo at verification time.

## Partial wins

- **p1:** A deterministic, fully specified rule that decrypts 50-149 consecutive runes of an unsolved page to English with at least 90% word coverage, reproduces at least one already-solved section with the same rule family, and gives no English on rune-shuffled copies of that page.
- **p2:** A deterministic rule that decrypts at least 150 consecutive runes of an unsolved page to English with at least 90% word coverage, verified by an independent re-implementation and failing on shuffled pages, but whose rule family does not reproduce any already-solved section; reported as candidate.

## How a win is checked

Clone Dukotah/cicada3301, run verify_solution.py --selftest, then run it on the claimed key. Independently re-transcribe the target page from the byte-verified source images (SHA1 matches listed in the repo). Decrypt with the verifier's own Gematria Primus implementation and score English.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/Dukotah/cicada3301>

## Sources

- <https://github.com/Dukotah/cicada3301>
- <https://github.com/Leo-Y-Zhang/LiberPrimusAnalysis>
- <https://www.boxentriq.com/guides/cicada-3301-liber-primus>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/liber-primus-lp2.md
```

Already set up? Say `run SUET on liber-primus-lp2`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `liber-primus-lp2`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
