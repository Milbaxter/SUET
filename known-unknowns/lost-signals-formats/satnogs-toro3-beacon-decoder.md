# SatNOGS: a validated telemetry decoder for TORO-3 (PYRAS3, NORAD 68481), an in-orbit CubeSat whose beacon has no public decoder

📻 **Lost signals and formats** · standard · tractability ★★★☆☆ · compute: laptop-hours of analysis, but at least 8 days of wall clock: freeze, wait 24 h, then a 7-day held-out window of new public frames (the DB page's ~52k frames over ~198 days since launch is ~260 frames/day); corpus is a few MB · open as of 2026-10-14

## The problem

TORO-3 (alternate name PYRAS3, NORAD 68481, SatNOGS DB sat_id BMVG-9246-3923-3953-0918, Taiwan, 8U ocean-colour CubeSat, launched 2026-03-30, international designator 26067BT per the DB TLE, i.e. the same 2026-067 launch as OPTISAT 2026-067C) transmits GFSK 4800 baud on 401.580 MHz. On 2026-10-14 its SatNOGS DB page (https://db.satnogs.org/satellite/68481) showed about 52k data frames collected by SatNOGS network ground stations, 'No Decoders Found', and 'There is no decoded data for this satellite in the last 30 days'. The live satnogs-decoders ksy/ directory (169 entries, last commit 2026-10-12) has no TORO/PYRAS decoder, gr-satellites has no satyaml with NORAD 68481, and no satnogs-decoders merge request mentions TORO. Public demod files, fetched by the vetter on 2026-10-14 from two good observations (SatNOGS Network 15179717 and 15188201, 2026-10-12), are AX.25 UI frames (FCS already checked and stripped by the SatNOGS demodulation flowgraph) with source callsign PYRAS3, destination ESGS01, ctl 0x03, pid 0xF0, and three info-field lengths: 18 bytes (type byte 0x80, ASCII 'This is TORO-3'), 40 bytes (type 0x82) and 48 bytes (type 0x83). The destination ESGS01 and the 4-byte info header (u16le that varied 4545-4574 across the 9 frames, constant 0x01, type byte) match the EnduroSat-style beacon that the community decoders optisat.ksy (OPTISAT, temporary NORAD 98370, sat_id EDMF-5886-6201-4785-7103, added 2026-10-10 by Bram Van Hout, https://github.com/BramVH98/optisat-telemetry) and sledge.ksy (SLEDGE, added 2026-09-16) partly describe: optisat.ksy calls the u16le 'battery_voltage_mv', maps only its 0x33 full-telemetry frame (most fields labelled unknown/unconfirmed) and names 0x83 only as a 'sparse/status frame' with no layout; sledge.ksy decodes a different, block-fragmented frame family. The body layout of TORO-3's 0x82 and 0x83 frames is therefore not publicly documented. The task is to reverse-engineer it so that a frozen decoder makes physical predictions that hold on frames received after it was frozen. Credit: Libre Space Foundation and the SatNOGS network ground-station operators (frames; SatNOGS DB data is CC BY-SA 4.0), the satnogs-decoders maintainers and contributors (Kaitai decoders incl. OPTISAT/SLEDGE), Daniel Estevez and gr-satellites contributors (decoder catalogue checked for prior work), and the TORO-3 mission team. 401.58 MHz is not an amateur band: this target is decoding of public recordings only, never transmission or uplink.

## What counts as a win

Success means a decoder for TORO-3 AX.25 UI frames (source PYRAS3) plus a PREREG.md, frozen by recording the sha256 of both and the UTC freeze time (from `date -u`) before the held-out window starts, such that ALL of the following hold on the HELD-OUT set = every public demod frame from SatNOGS Network observations of the satellite with DB sat_id BMVG-9246-3923-3953-0918 (NORAD 68481 today; temporary NORAD ids can be reassigned) with status good, fetched from their public payload_demod URLs, whose reception time (the UTC timestamp in the demod filename; a trailing _N suffix marks extra frames in the same second and they share that timestamp) is at least 24 h after the freeze time, spanning at least 7 days, at least 3 distinct ground stations and at least 500 frames of types 0x82 and 0x83 combined: (a) COVERAGE: the decoder assigns a named field with type, scale and unit to every byte of the 0x82 and 0x83 info fields (no opaque blob longer than 1 byte; a field declared constant must be constant on held-out), declares a valid range for every non-constant field, and on >= 99% of held-out 0x82/0x83 frames parses without error with every field inside its declared range; (b) CLOCK: at least one field is declared in PREREG.md as an onboard time, uptime or counter with a stated rate (units per second, or 'strictly increasing'); for every held-out observation with >= 3 frames of that type spanning >= 60 s, the least-squares slope of the field against reception time matches the declared rate within 10% (or, for a counter, the field is strictly increasing in reception order, ties in the same second ignored) for >= 95% of such observations, with qualifying observations from >= 3 stations; (c) SUN: at least one field is declared in PREREG.md as sun-dependent (solar-array current/voltage/power or a sun sensor) with a declared direction, and using TLE snapshots of the satellite fetched by the attacker at least daily during the held-out window (from the SatNOGS DB page or CelesTrak, archived in the claim package with fetch timestamps, since historical TLEs need a Space-Track login) and the snapshot nearest each frame propagated with skyfield to label each held-out frame sunlit or umbra (frames within 60 s of a shadow boundary dropped, >= 30 frames in each class), the field's AUC for sunlit vs umbra in the declared direction is >= 0.95, while the same field with the sunlit/umbra labels randomly permuted (1,000 permutations) never exceeds 0.70; (d) NOVELTY, re-checked live before claiming: the satnogs-decoders ksy/ tree and open/merged merge requests contain no TORO-3/PYRAS3 decoder, gr-satellites has no satyaml for 68481, the DB page still shows 'No Decoders Found', and a web search finds no published TORO-3 or EnduroSat beacon specification covering the 0x82/0x83 bodies (if one exists, the result is a replication, not a win). The claim package includes a manifest of every held-out observation id, demod URL and per-file sha256. Field meanings beyond what (b) and (c) test are not part of the claim. Nothing is submitted to SatNOGS by the agent; a merge request is for the human.

## Partial wins

- **p1:** Criteria (a), (b) and (d) on the held-out set, without (c) (for example because the held-out window contains fewer than 30 umbra frames).
- **p2:** An internal checksum: a declared span of bytes in the 0x82 or 0x83 info field that validates as a stated checksum or CRC (algorithm, polynomial, init, reflection, xorout and covered byte range declared in PREREG.md before the held-out window) on 100% of held-out frames of that type and on <= 1% of decoys made by flipping one random bit in the covered range of each held-out frame; criterion (d) also required.
- **p3:** Criterion (c) alone, applied to the OPTISAT field optisat.ksy calls unknown_g1 ('unconfirmed hypothesis: sun sensor'): with that field and direction pre-registered, held-out 0x33 frames from Network observations of DB sat_id EDMF-5886-6201-4785-7103 (OPTISAT) received >= 24 h after the freeze give sunlit-vs-umbra AUC >= 0.95 and permuted-label AUC never above 0.70 (>= 30 frames per class, >= 3 stations), and no satnogs-decoders commit after 2026-10-14 already confirms it.

## How a win is checked

Skeptic re-lists SatNOGS Network observations of the satellite after freeze+24 h (slowly, per satellite, stopping on any 429) to confirm the claim manifest dropped nothing, downloads the demod files from their public S3 URLs, checks the sha256 of the decoder and PREREG.md against the recorded freeze, and checks the freeze time precedes every held-out reception time. With their own AX.25 header parser they select source PYRAS3 frames, run the frozen decoder, and recompute (a) coverage and range compliance, (b) the per-pair rate test, (c) sunlit/umbra labels with skyfield from the archived TLE snapshots (spot-checked against any public TLE of a nearby epoch), the AUC and the permutation null, and, for p2, the checksum on real frames and on bit-flipped decoys. Then they re-check novelty on the live satnogs-decoders tree/merge requests, gr-satellites and the DB page. Under an hour.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://db.satnogs.org/satellite/68481>

## Sources

- <https://db.satnogs.org/satellite/68481>
- <https://gitlab.com/librespacefoundation/satnogs/satnogs-decoders/-/tree/master/ksy>
- <https://gitlab.com/librespacefoundation/satnogs/satnogs-decoders/-/blob/master/ksy/optisat.ksy>
- <https://gitlab.com/librespacefoundation/satnogs/satnogs-decoders/-/blob/master/ksy/sledge.ksy>
- <https://github.com/BramVH98/optisat-telemetry>
- <https://github.com/daniestevez/gr-satellites>
- <https://db.satnogs.org/about/>
- <https://s3.eu-central-1.wasabisys.com/satnogs-network/data_obs/2026/10/12/1/15179717/data_15179717_2026-10-12T01-44-06>
- <https://s3.eu-central-1.wasabisys.com/satnogs-network/data_obs/2026/10/12/1/15179717/data_15179717_2026-10-12T01-44-57_1>
- <https://s3.eu-central-1.wasabisys.com/satnogs-network/data_obs/2026/10/12/1/15188201/data_15188201_2026-10-12T01-43-32>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Start from optisat.ksy: it already reads the 4-byte header (u16le battery_voltage_mv, constant 0x01, frame type) of the same EnduroSat-style beacon family; check whether its 0x33 full frame shares sub-block markers (e.g. constant tag blocks, 0x3E markers) with TORO-3's 0x82/0x83 bodies.
- Build a corpus from many observations, then for every byte offset and width (u8, u16/u32 le/be, f32) compute variability, step size between consecutive frames of a pass, and correlation with reception time; fields that advance at ~1 unit/s or a power of two per second are clock candidates.
- Label every frame sunlit/umbra from the TLE first (skyfield), then scan offsets for the best sun separation on a training window only; pre-register the winner and test on later frames, so offset scanning cannot overfit the held-out set.
- Use the same frame seen by two ground stations at once: byte-identical payloads confirm both demods and give clean duplicates to drop before rate tests.
- Try the CRC catalogue (reveng-style search over CRC-8/16/32 parameters) on trailing bytes of 0x82/0x83 bodies for p2; a hit validates the field boundaries for free.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- No CRC null test at the link layer: SatNOGS demod files contain only AX.25 frames whose FCS already passed and was stripped, so 'frames decode' or 'round-trips' says nothing; a single blob field round-trips anything. Only held-out physical predictions (b), (c) and checksum decoys (p2) count.
- Offset-scanning on the same frames you test on: any of ~100 byte offsets can look sun-correlated by chance on a small sample. Freeze field choices before the held-out window and use the permutation null.
- The SatNOGS DB frame download (/api/telemetry/) needs an API token; agents never use tokens or log in (kit/RULES.md 7). Use the Network observations' public demod files instead.
- network.satnogs.org rate-limits: bulk paging of /api/observations/ returned HTTP 429 to the vetter on 2026-10-14. Query per satellite (norad_cat_id=68481), a few pages, slowly; on 429 stop and mark the held-out fetch PENDING (kit/RULES.md 5).
- The demod filename timestamp is the ground station's reception time at 1 s resolution (several frames can share one second, distinguished by a _N suffix), with possible station clock error; use per-observation slope fits for rates and drop frames near shadow boundaries for sunlit labels.
- TORO-3 is in a ~97.8 deg sun-synchronous orbit (DB TLE inclination 97.7833); if its local time makes umbra receptions rare, (c) may be unreachable in the window; that is p1, not a reason to relax (c).
- A field named in optisat.ksy or sledge.ksy is someone else's hypothesis; reusing it is fine but must be credited, and if an EnduroSat or TORO-3 team document turns up, the result is a replication.
- Do not identify ground-station operators by name or callsign in any shared package (kit/RULES.md 12); cite observation ids.
- Historical TLEs are behind a Space-Track login, which agents never use; fetch the current TLE daily during the window and archive it, or the sunlit labels cannot be reproduced later.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/lost-signals-formats/satnogs-toro3-beacon-decoder.md
```

Already set up? Say `run SUET on satnogs-toro3-beacon-decoder`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `satnogs-toro3-beacon-decoder`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
