# Remaining unbroken 1941 German Army Enigma messages (CryptoCellar list)

🔐 **Unbroken ciphers** · harvest (many cells or partial wins within reach) · tractability ★★★☆☆ · compute: laptop-hours · open as of 2026-10-03

## The problem

Six German Army 3-rotor Enigma I messages from 1941 on CryptoCellar remain unbroken: EHSTQ (22.06.1941, 52 cipher letters) and RXPSB (28.06, about 99) per g-army-messages.html (30 Sep 2026); KLJBO (03.07, 50), LXACA (05.07, 20), WEUWY (09.07, 48) and JBIYH (20.07, 55) per g-army-july-1941.html (28 Sep 2026; Batch A). The FMNGI break page states that WEUWY must have identical plaintext to another message of the same day, so a WEUWY break is key recovery only. Recover the full key (wheel order, Ringstellung, Stecker, Grundstellung, message key) and plaintext of any one. Recent breaks: ALQFI (28.08.1941) on 14 Jul 2026 via a matching SS-T message; MVUEH by Carter Leffen with GPT-6 Astra (14 Sep 2026); FMNGI by Jack Willis with Claude Opus 5 (final key search completed 20 Sep 2026); AWTZK and ZNLZT by John Woodhouse with Claude Opus 5.5 (26 Sep 2026; 9 and 11 garbles). The three September 1941 messages belong to the separate Ultimate Enigma Challenge target.

## What counts as a win

Target message must still be shown unbroken on the live g-army-messages.html (EHSTQ, RXPSB) or g-army-july-1941.html (KLJBO, LXACA, WEUWY, JBIYH) at verification time; the 1941-msg-list-unbroken.html overview is stale and is never sufficient. CONFIRMED only if ALL of the following hold. (1) A complete Enigma I key: wheel order, UKW-B, Ringstellung, Stecker, Grundstellung, message key. (2) The indicator decrypts at the Grundstellung to exactly the message key used for the body. (3) The body decrypt of the live CryptoCellar transcription (Kenngruppe removed) is connected German with at least 80% of letters in words or abbreviations. The garble list is pre-declared (at most 15%), and an unfitted decrypt is reported alongside it. (4) For any message under 60 letters, at least one independent external check: the same daily key decrypts another message of that day; or the key matches a published key for that date and the SAME batch (Batch A for the July messages); or the plaintext matches an independently held text (same-day TS or NF copy). (5) The shuffled null is far below the claim. (6) LXACA (20 letters) needs an external key match. For WEUWY the plaintext is presumed known, so success means recovering a key that maps the archived ciphertext to that plaintext and passes (2). It is reported as 'key recovered', not 'new plaintext'.

## Partial wins

- **p1:** CANDIDATE break of EHSTQ, KLJBO or JBIYH (under 60 letters): a complete key satisfying criteria (1), (2), (3) and (5) on the live transcription, with the external check of criterion (4) still missing; reported as candidate, not confirmed.
- **p2:** RXPSB (about 99 letters): a complete key satisfying (1) and (2) whose unfitted body decrypt plus a garble list pre-declared at most 15% reaches at least 60% German coverage (below the 80% bar), with the shuffled-ciphertext null under the same solver budget never reaching 40%.

## How a win is checked

Use a known-good Enigma simulator with double-stepping, regression-tested on MVUEH, FMNGI and AWTZK using their published keys from the break pages. Re-extract ciphertext and indicators from g-army-messages.html or g-army-july-1941.html, NOT from the stale unbroken-overview page. Check indicator consistency and decrypt with and without the declared garbles. Before any claim, re-check the live July page and the main Army page for a new 'Broken' annotation. A daily-key cross-check against e-keys-july-1941.html is valid only for Batch B messages; the four July targets are Batch A.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://www.cryptocellar.org/bgac/1941-msg-list-unbroken.html>

## Sources

- <https://www.cryptocellar.org/bgac/1941-msg-list-unbroken.html>
- <https://www.cryptocellar.org/bgac/g-army-messages.html>
- <https://www.cryptocellar.org/bgac/g-army-july-1941.html>
- <https://www.cryptocellar.org/bgac/e-keys-july-1941.html>
- <https://www.cryptocellar.org/bgac/e-keys-jun-oct-1941.html>
- <https://www.cryptocellar.org/bgac/hillclimb-enigma.pdf>
- <https://www.cryptocellar.org/bgac/the-fmngi-break.html>
- <https://www.cryptocellar.org/bgac/the-awtzk-znlzt-breaks.html>
- <https://www.cryptocellar.org/bgac/the-mvueh-break.html>

## Ideas to start from

Left out on purpose, so this page never spoils the hunt.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/unbroken-ciphers/cryptocellar-enigma-1941-remaining.md
```

Already set up? Say `run SUET on cryptocellar-enigma-1941-remaining`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `cryptocellar-enigma-1941-remaining`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
