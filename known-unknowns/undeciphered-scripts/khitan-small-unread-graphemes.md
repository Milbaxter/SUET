# Khitan small script: phonetic values for unread graphemes from Chinese loanwords and titles

📜 **Undeciphered scripts** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Khitan small script (Liao dynasty, about 470 encoded characters, Unicode 13.0) is partly read: many phonetic values come from Chinese loanwords and official titles in the Kane/Chinggeltei tradition. A number of graphemes still have no secure value, and Khitan-Chinese parallel-text methods are reported to be at an impasse. Khitan large script is much further behind: about 10% of roughly 2,245 characters are fully read. The task is to predict values for unread graphemes and test those predictions on held-out loanword occurrences. No open machine-readable corpus of Khitan small script texts with aligned Chinese parallels was confirmed (BabelStone has only some texts), and the novelty check practically requires the Chinese-language literature (Inner Mongolia University school, Aisin-Gioro Ulhicun and others). Status as of 2026-10-03: Partly deciphered. Encoding and standardization progressed (China's 2025 large-script encoding proposal) and readings appeared in 2025 (Korean Association for Mongolian Studies). No full decipherment.

## What counts as a win

A value for a grapheme listed as unread in Kane 2009 (the BabelStone list). The value must come from a frozen procedure, for example constraint solving over clusters that transcribe known Chinese titles and names in dated epitaphs. When substituted, it must produce at least 3 readings of Chinese loanwords or names in held-out clusters (not used for inference) that match Liao-period Chinese pronunciations, and random value permutation must give p < 0.01. The value must also not already be in the literature after Kane 2009. Additionally: training and held-out clusters are listed with source inscription and line before solving; the Liao-period northern Chinese reconstruction is fixed beforehand. Claim only as 'candidate value, novelty not cleared against the Chinese-language literature' unless a Chinese-language search (CNKI titles and abstracts) is documented.

## Partial wins

- **p1:** Method calibration: the frozen constraint solver, run with one grapheme value that was published after Kane 2009 withheld (the value and its source named beforehand), recovers that value from training clusters alone and confirms it on at least 3 held-out clusters with Liao-period Chinese matches, random value permutation p < 0.01.
- **p2:** A frozen value for a grapheme listed as unread in Kane 2009 that yields at least 2 held-out Chinese loanword or name readings matching the pre-fixed Liao-period northern Chinese reconstruction, with random value permutation p < 0.01 and clusters listed with source inscription and line before solving (full criterion requires 3).

## How a win is checked

The verifier re-derives the cluster transcriptions from BabelStone Unicode texts and Kane's character list, reruns the solver on the training clusters, and checks each held-out match against a Middle or Liao Chinese reconstruction and the parallel Chinese epitaph text. Additionally, the verifier re-derives the clusters from BabelStone Unicode texts at a pinned date and checks each held-out match against the parallel Chinese epitaph text.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.babelstone.co.uk/Khitan/>

## Sources

- <https://www.babelstone.co.uk/Khitan/>
- <https://www.babelstone.co.uk/Fonts/KhitanSmall.html>
- <https://en.wikipedia.org/wiki/Khitan_Small_Script_(Unicode_block)>
- <https://www.unicode.org/wg2/docs/n5319-KhitanLargeScriptEncoding.pdf>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/undeciphered-scripts/khitan-small-unread-graphemes.md
```

Already set up? Say `run SUET on khitan-small-unread-graphemes`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `khitan-small-unread-graphemes`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
