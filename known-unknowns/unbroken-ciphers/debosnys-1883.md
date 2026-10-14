# Henry Debosnys cryptograms (1882-83)

🔐 **Unbroken ciphers** · standard · tractability ★☆☆☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Henry Debosnys, executed in 1883 for murdering his wife in Essex County NY, left several enciphered documents and poems in a symbol script. One transcription counts 1,188 glyph instances of 425 glyph types; another treats glyphs as composed of subglyphs (possibly syllables). Nobody has decrypted a single word. It is #3 on Schmeh's Top-50.

## What counts as a win

CONFIRMED only if a single subglyph or glyph-to-sound/letter mapping, fixed across ALL documents, yields readable text in a natural language (French, English, Portuguese or Spanish, all plausible for Debosnys) over at least 300 consecutive glyph instances, with at least 85% word coverage. Any poem must keep plausible meter or rhyme, and a held-out document never used in fitting must decode with the same mapping. All decoding is against a transcription frozen with a SHA-256 hash BEFORE any fitting (Sektu's if obtainable, or a new one from Cipher Foundation scans, made blind to the solver), and the cryptograms must still be listed unsolved at verification time.

## Partial wins

- **p1:** A glyph or subglyph mapping fitted on one document that, frozen and applied to a held-out document of the hashed transcription, decodes at least 100 consecutive glyph instances to a natural language with at least 85% word coverage and beats a mapping-shuffle null at p < 1e-4.
- **p2:** Identification of a specific published 19th-century shorthand system (e.g. Duployé, Prévost-Delaunay, Pitman) whose direct transliteration, with the sign table taken from a cited manual and not fitted, yields readable text for at least 50 consecutive glyph instances of a held-out document, beating a sign-shuffle null at p < 1e-4.

## How a win is checked

First freeze a transcription with its SHA-256: either Sektu's, if obtainable, or a new one from Cipher Foundation scans made before any decipherment attempt and blind to the solver. Fit on one document, apply the frozen mapping to a held-out document, measure language coverage, and compare against a mapping-shuffle null.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <http://cipherfoundation.org/older-ciphers/debosnys-ciphers/>

## Sources

- <http://cipherfoundation.org/older-ciphers/debosnys-ciphers/>
- <https://sektu.blogspot.com/2017/08/debosnys-cipher-transcription-revision.html>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/debosnys-1883.md
```

Already set up? Say `run SUET on debosnys-1883`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `debosnys-1883`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
