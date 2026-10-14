# MOONSHOT: Voynich manuscript, a key that decrypts held-out folios into meaningful text

📜 **Undeciphered scripts** · moonshot (famous, long odds) · tractability ★☆☆☆☆ · compute: laptop-days · open as of 2026-10-03

## The problem

Find a key or procedure that maps Voynichese to plaintext in a natural language, and that generalizes to folios not used in building it. Status as of 2026-10-03: Unsolved as of 2026. Multiple 2026 claims (Delgado's Latin, a Galician reading) have no acceptance. The Naibbe cipher (2025) is a generation model, not a decryption.

## What counts as a win

All of these must hold. (1) The key is fully specified and deterministic, or has bounded ambiguity of at most 2 readings per token, and is frozen before testing. (2) Applied unchanged to at least 10 held-out folios chosen by the verifier, it yields text whose per-character perplexity under a period language model (for example, a 15th-century Latin or Italian corpus) is at least 1.5 bits/char better than the same key applied to glyph-shuffled versions of those folios. (3) Key description length plus plaintext entropy is less than the entropy of the Voynich text under its best compressor (an MDL check against key overfitting). (4) At least 3 plant or star names decrypted on herbal or astro folios match identifications agreed by an independent botanist or astronomer reviewer who has not seen the claimed reading. (5) The frozen key applied to (a) Naibbe-cipher output encrypting a different language and (b) an arXiv 2604.19762-style slot-generator output must give per-character perplexity at least 1.0 bits/char worse than on the held-out Voynich folios. A key that 'decrypts' generated gibberish equally well is rejected.

## Partial wins

- **p1:** A frozen key (deterministic, at most 2 readings per token) that, on at least 10 verifier-chosen held-out folios, gives per-character perplexity under an independent period language model at least 1.5 bits/char better than on glyph-shuffled versions of those folios AND at least 1.0 bits/char better than on the verifier-generated structured-gibberish controls (Naibbe output of a different language; slot-generator output), i.e. criteria (2) and (5) without (3) and (4).
- **p2:** Blind illustration match alone: a frozen key decrypts at least 3 plant or star names on verifier-chosen herbal or astronomical folios that match identifications made independently by a botanist or astronomer reviewer who has not seen the claimed reading, while the same key applied to the structured-gibberish controls yields no such matches.

## How a win is checked

The verifier selects held-out folios with its own seed, runs the frozen key, and computes the perplexity against shuffled controls with an independent language model. It checks the MDL accounting and arranges the blind illustration-match review. Additionally, the verifier generates the structured controls itself with fresh seeds and scores them under the same period language model.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.voynich.nu/data/ZL3b-n.txt>

## Sources

- <https://www.voynich.nu/data/ZL3b-n.txt>
- <https://www.voynich.nu/transcr.html>
- <https://github.com/greshko/naibbe-cipher>
- <https://arxiv.org/abs/2604.19762>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/undeciphered-scripts/voynich-plaintext.md
```

Already set up? Say `run SUET on voynich-plaintext`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `voynich-plaintext`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
