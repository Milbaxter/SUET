# Unbroken German Army Truppenschlüssel (TS) hand-cipher messages, 1941 (CryptoCellar)

🔐 **Unbroken ciphers** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Frode Weierud's CryptoCellar (g-army-ts-messages.html, updated 27 Jul 2026) lists about 40 German Army Truppenschlüssel (TS) messages from June to September 1941. TS is a hand substitution cipher using two 5x5 squares (25-letter alphabet, J written as II), described in Ostwald and Weierud's Cryptologia article 'Modern Cryptanalysis of the Truppenschlüssel'. 11 are marked broken (10 on 22.01.2022, TUNYA on 26.01.2022); about 29 carry no 'Broken' marker, e.g. YSGSS (28.06.1941, 13 letters), FCVHR/HKMZI/FBOIQ (03.07; FBOIQ 38), KVLIG/SGOXX/UBYVQ/HFEYY/LICUD/DSZPZ/DEZPS/TKYKJ (04.07; TKYKJ 35), SSKFV/HOHOX (06.07), IABZV/EHNPZ/IASRZ (08.07; IASRZ appears twice, 90 and 52 letters), XWFEC (12.07), AFUVO (13.07, 14), DOLHA, CPUDN (32), NEUEM, LSSLG, CFQIB, VHRNE, ZUBZE, MZXNX, AAXYN, AOXST. The page publishes NO keys or plaintexts for the broken messages and attributes the failures to unfavourable plaintext, garbles or ciphering errors, and short messages. Break any one qualifying unbroken message: recover its key and plaintext. Context: TS plaintexts for 10-11 July 1941 were supplied privately by Olaf Ostwald (requested by Sean Harrington) for the Sept 2026 AWTZK/ZNLZT Enigma attack; none of the Sept 2026 breaks touched TS.

## What counts as a win

Target message must still carry no 'Broken' marker on https://www.cryptocellar.org/bgac/g-army-ts-messages.html at verification time (otherwise the result is reported as a non-first re-break). CONFIRMED only if ALL of the following hold. (1) The full key (both 5x5 squares) and the exact TS procedure are given, with the procedure cited to Ostwald and Weierud's Cryptologia article 'Modern Cryptanalysis of the Truppenschlüssel' (section and page). (2) Deterministic decryption of the CryptoCellar transcription (re-extracted fresh) gives connected German military text, with at least 85% of letters inside German words or standard Wehrmacht abbreviations. (3) A garble list is declared BEFORE scoring: at most 8% of letters, each Morse-plausible, with red J positions treated as unknown symbols. (4) Length gate: only messages of at least 80 cipher letters qualify alone. A shorter message qualifies only if the SAME key also decrypts another same-date message to German meeting (2), AND the Cryptologia description confirms that same-day messages share a key. Messages under 40 letters are never CONFIRMED. (5) A shuffled-ciphertext null: 200 shuffles, same pipeline and budget, best score at least 5 SD below the claim. (6) Historical coherence with June to September 1941 traffic of the same net. A custodian 'Broken' marker counts as final external confirmation.

## Partial wins

- **p1:** Blind garble-tolerance benchmark: the verifier enciphers 3 period-style German military texts of 60-100 letters with the TS procedure as implemented from the Cryptologia paper (validated on its worked example), using random squares and injecting about 8% Morse-plausible garbles; the solver, given only the ciphertexts, recovers at least 95% of the plaintext letters of all 3 within a declared compute budget.
- **p2:** A pair of 5x5 squares under which a contiguous run of at least 70 cipher letters of one unbroken message (at least 80 letters long) decrypts to German with at least 85% word/abbreviation coverage, with a garble list declared before scoring and the 200-shuffle null at least 5 SD below, even if the rest of the message exceeds the 8% garble cap.
- **p3:** Same-key evidence: one pair of squares decrypts two unbroken messages of the same date to German meeting criterion (2) on each, with the null at least 5 SD below on each; this counts as a partial win when the Cryptologia description does not confirm daily key sharing (so the full criterion's same-day clause cannot be invoked).

## How a win is checked

Implement TS from the Cryptologia paper's description and worked example. No broken keys are public, so validate the implementation by encrypting and decrypting the paper's own example, and if possible ask the custodian (a human action) for one broken key. Re-scrape the page with a script and assert each message's length against the page's stated length. Apply the claimed key and declared garbles, compute German coverage with a lexicon plus an abbreviation list, rerun the shuffled null with the verifier's own solver, and check same-day key consistency where it is used.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.cryptocellar.org/bgac/g-army-ts-messages.html>

## Sources

- <https://www.cryptocellar.org/bgac/g-army-ts-messages.html>
- <https://www.cryptocellar.org/bgac/1941-msg-list.html>
- <https://www.cryptocellar.org/bgac/the-fmngi-break.html>
- <https://www.cryptocellar.org/bgac/>
- <https://www.cryptocellar.org/bgac/the-awtzk-znlzt-breaks.html>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/cryptocellar-truppenschluessel-1941.md
```

Already set up? Say `run SUET on cryptocellar-truppenschluessel-1941`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `cryptocellar-truppenschluessel-1941`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
