# Greek literary papyri: identify DCLP 'unidentified' fragments as witnesses of known works via open-corpus text matching

🏺 **Ancient texts and fragments** · harvest (many cells or partial wins within reach) · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-08

## The problem

The Digital Corpus of Literary Papyri (DCLP, papyri.info; open EpiDoc XML in github.com/papyri/idp.data, DCLP/ folder) held 14,845 records at commit 67e8445 (2026-10-08), 2,276 of them with a transcription (<ab>). Re-count by the vetter on 2026-10-08: the 'unidentified' label lives in the work-level metadata, i.e. <title type="main" level="m"> elements carrying a trismegistos.org/authorwork ref that read 'Opus incertum' (about 80 transcribed records), <author>/<surname> = 'Anonymus' (about 70), <term type="overview"> 'unknown work' (4) and principal-edition titles naming unknown works; roughly 150-250 transcribed records are genuinely unidentified-work records (the stocker's 1,941 included 'unknown' inventory numbers and provenances and is not the pool). Many of these are Herculaneum (PHerc.) opera incerta of Philodemus or Demetrius Laco, i.e. lost works absent from every corpus, so the realistic pool is smaller still. Open Greek corpora exist in full text (OpenGreekAndLatin/First1KGreek, PerseusDL/canonical-greekLit; Latin: PerseusDL/canonical-latinLit), so identification can be attempted mechanically by aligning the supplement-free letters of each unidentified fragment against every open text, which scholars still do by hand (e.g. the 2024 re-identification of P.Oxy. 2258 'Unidentified Fragment 11' as Demosthenes). Status 2026-10-08 (vetter): no systematic machine identification campaign published (searches found only writer-identification, character-detection, dating and stylometric authorship work); idp.data actively maintained (last commit 2026-10-08); raw.githubusercontent.com and papyri.info/dclp return 200 to plain curl; a sparse clone of DCLP/ takes about a minute.

## What counts as a win

At least 1 DCLP record meeting ALL of: (a) at the recorded idp.data commit, every work-level author/title element of the record (the <author>/<surname> elements and the <title type="main" level="m"> elements that carry a trismegistos.org/authorwork ref, plus <term type="overview">) reads Opus incertum / Adespota / Anonymus / unidentified / unknown, and no <bibl>, <note>, <head> reference title, <term> or <change> entry in the record names the matched author or work; (b) the alignment uses ONLY letters outside editorial supplements ([ ]) and outside <supplied>/<gap> elements, with underdotted (uncertain) letters excluded from the count; (c) the fragment's stripped letters align to one passage of one open-corpus text (First1KGreek, canonical-greekLit or canonical-latinLit; repository commit hash recorded) over at least 12 consecutive legible letters spanning at least 2 papyrus lines with at most 1 letter mismatch, and the line-break positions are consistent with a plausible column width (constant +/-3 letters per line); (d) the alignment score has p < 1e-4 against a null formed by aligning the same fragment to the whole open corpus with line order shuffled, Bonferroni-corrected over all fragments searched; (e) the matched passage is not a formula or quotation attested in at least 5 distinct open-corpus works (Homeric formulae, LXX/NT verses, proverbs, gnomic sentences), verified by exhaustive corpus-wide counting; (f) the identification is not already recorded in the papyri.info HTML/XML record, in the Trismegistos/LDAB authorwork entry linked from the record's <idno type="LDAB">, or in the editions cited in the record's <head>, all re-fetched live immediately before claiming. Claim as 'candidate identification'; CONFIRMED only when a papyrologist or the papyri.info editorial board accepts it.

## Partial wins

- **p1:** A DCLP record meeting (a), (b), (d), (e), (f) whose alignment covers 8-11 consecutive legible letters over at least 2 lines with 0 mismatches, where the matched 8+ letter string occurs exactly once in the entire open corpus (rarity verified by exhaustive search) and the line-break constraint of (c) holds.

## How a win is checked

The verifier sparse-clones idp.data (DCLP/ only, about 1 minute) at the claimed commit, checks the record's work-level elements per (a) with independent code, strips supplements/gaps/underdots with independent code, re-runs the alignment of the claimed fragment against the open corpus at the recorded commit, re-runs the shuffled-line null, counts corpus-wide occurrences of the matched string, and re-fetches the papyri.info record and the LDAB authorwork entry live to confirm no prior identification. Under one hour on a 10-core Mac.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://github.com/papyri/idp.data>

## Sources

- <https://github.com/papyri/idp.data>
- <https://raw.githubusercontent.com/papyri/idp.data/master/DCLP/64/64136.xml>
- <https://github.com/OpenGreekAndLatin/First1KGreek>
- <https://github.com/PerseusDL/canonical-greekLit>
- <https://papyri.info/dclp>
- <https://github.com/PerseusDL/canonical-latinLit>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Index both open corpora as accent-stripped, lower-cased letter n-grams (n=6..8) and run seed-and-extend alignment of each unidentified fragment's supplement-free letters; score by length and corpus rarity.
- Treat papyrus line breaks as constraints: a correct match must place line ends at a near-constant letter count per line, which prunes chance hits.
- Prioritise fragments whose DCLP title says 'prose' or 'hexameter' with 3+ lines and few lacunae; verse fragments can be matched on metrical position as well.
- Run the identified transcribed records blind (identification fields hidden, supplements stripped) as a calibration set to tune thresholds before claiming any new identification (calibration is a prerequisite, not a win).
- Cross-check candidate hits against the record's own <bibl> and the TM authorwork field via the papyri.info JSON/HTML page before claiming.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- Editorial supplements in [ ] were often restored FROM a suspected source text: matching on them is circular. Strip all bracketed text and also dotted (uncertain) letters when counting.
- Homeric formulae, LXX/NT verses, proverbs, school exercises and gnomic sentences recur across many works; condition (e) must be enforced by corpus-wide counting.
- TLG is not open and First1KGreek is incomplete: absence of a match proves nothing, and a match to a fragmentary author (e.g. Menander) may reflect a quotation in a later author rather than the primary work.
- Some 'unidentified' DCLP metadata is stale: the record may have been identified in a later edition (P.Oxy. re-editions, BKT) or in Trismegistos without idp.data being updated. Check live before claiming.
- Leiden-convention markup (dots, underdots, brackets, line numbers) must be parsed carefully; a naive strip can glue letters across lacunae and produce fake 12-letter runs.
- 'unknown'/'incertum' also appears in inventory numbers, provenances and editorial notes: only the work-level author/title elements (with trismegistos authorwork ref) and the overview term define the pool.
- Lost works (Philodemus/Demetrius Laco opera incerta, lost tragedies, novels) can never match an open corpus; a null result on them is expected and is not evidence of anything.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/ancient-texts/dclp-unidentified-literary-papyri.md
```

Already set up? Say `run SUET on dclp-unidentified-literary-papyri`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `dclp-unidentified-literary-papyri`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
