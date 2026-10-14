# Chinese gold bar cryptograms (Shanghai, 1933)

🔐 **Unbroken ciphers** · standard · tractability ★☆☆☆☆ · compute: laptop-minutes · open as of 2026-10-03

## The problem

Seven 'gold bars' allegedly issued to a General Wang in Shanghai (1933) carry Chinese text about a transaction over $300,000,000, unknown script, and 16 distinct Latin-letter cryptogram lines of 8-25 letters. Several lines are repeated across bars, e.g. SKCDKJCDJCYQSZKTZJPXPWIRN, MQOLCSJTLGAJOKBSSBOMUPCE, RHZVIYQIYSXVNQXQWIOVWPJO, FEWGDRHDDEEUMFFTEEMJXZR, HFXPCQYZVATXAWIZPVE, VIOHIKNNGUAB. Letter statistics are very flat. Determine what the lines encode.

## What counts as a win

CONFIRMED only if a single deterministic system and key (for example a period-appropriate polyalphabetic or commercial codebook) decodes ALL 16 lines (about 250 letters) into meaningful text (English, French, or romanized Chinese in Wade-Giles/Postal) that is coherent with the bars' Chinese inscriptions (amounts, bank, dates, names), with no per-line keys unless a documented indicator rule selects them. Alternatively, a decisive proof that the lines are produced by a specific identifiable generator, such as a published test-key or check-code scheme, where the generator reproduces all 16 lines exactly from bar data. The cryptograms must still be listed unsolved (Schmeh Top-50, IACR page) at verification time.

## Partial wins

- **p1:** A single identifiable generator (a published 1930s test-key, check-code or textbook scheme) that reproduces at least 4 distinct lines exactly from data on the bars, with the chance probability of that many exact reproductions under the searched generator space below 1e-6.
- **p2:** A single deterministic system and key, with no per-line keys, that decodes at least 4 distinct lines (at least 80 letters in total) into meaningful text coherent with the bars' Chinese inscriptions, while the same system on shuffled-letter lines yields nothing comparable.

## How a win is checked

Use the IACR transcription, cross-checked against the bar photos on the IACR page. Implement the claimed system, decode all lines, check consistency with the translated Chinese text, and run a shuffled-letter null.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.iacr.org/misc/china/cryptograms.html>

## Sources

- <https://www.iacr.org/misc/china/cryptograms.html>
- <http://cipherfoundation.org/modern-ciphers/chinese-gold-bar-ciphers/chinese-gold-bar-transcription/>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/chinese-gold-bars.md
```

Already set up? Say `run SUET on chinese-gold-bars`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `chinese-gold-bars`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
