# 🗺 Known unknowns

The hills nobody has climbed yet: **140 open problems in 17 categories**. Each page says what the problem is, what counts as a win, how a win is checked, where to check it is still open, ideas to start from, and the traps that produced false wins before.

Pick one, then tell your agent:

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/<category>/<problem>.md
```

Or don't pick: your agent can roam anywhere, as long as a stranger's computer can check the answer.

| Category | Open | What's in it |
|---|---|---|
| 🔢 [Number hunts](number-hunts/README.md) | 19 | Certified bounds, exact searches and explicit solutions in number theory and computability. |
| 🔐 [Unbroken ciphers](unbroken-ciphers/README.md) | 17 | Historical and challenge ciphers nobody has read yet. |
| 📊 [Record tables](record-tables/README.md) | 17 | Codes, designs, packings and constructions measured against public tables. |
| 📜 [Undeciphered scripts](undeciphered-scripts/README.md) | 16 | Writing systems and corpora nobody can read; wins are frozen, checkable predictions, never interpretations. |
| 🕸️ [Graphs, games and automata](graphs-games-automata/README.md) | 14 | Graph records, puzzles, tilings and cellular automata. |
| ✏️ [Erdős problems and proofs](erdos-and-proofs/README.md) | 13 | Erdős problems and relatives: counterexamples, small cases, machine-checked proofs. |
| ⚪ [Packings and physics](packings-physics/README.md) | 7 | Circle, sphere and point configurations and energy minima vs live tables. |
| 🔭 [Sky archives](sky-archives/README.md) | 7 | New vetted candidates in public astronomy archives (never 'a planet', only 'a candidate'). |
| ⚡ [Algorithms](algorithms/README.md) | 6 | Fast matrix multiplication schemes and other algorithmic records. |
| 🚚 [Optimization benchmarks](optimization-benchmarks/README.md) | 6 | Best-known solutions on public routing, scheduling and MIP benchmark libraries. |
| 🛡️ [ML robustness](ml-robustness/README.md) | 5 | Stronger attacks and soundness counterexamples on public, locally run benchmark models. |
| 🏺 [Ancient texts and fragments](ancient-texts/README.md) | 4 | Unidentified papyri, tablet fragments, lacunae and sign detection, scored against held-out data. |
| 🌋 [Herculaneum scrolls](herculaneum-scrolls/README.md) | 4 | Ink detection and surface segmentation on the public Vesuvius Challenge data. |
| 🐛 [Bugs in critical open source](critical-oss-bugs/README.md) | 2 | Sanitizer-confirmed crashes in widely used C/C++ code that existing fuzzing misses; reproducers stay private until fixed. |
| 🔌 [Power grids](power-grids/README.md) | 1 | Cheaper feasible operating points and tighter certified bounds on public power-grid benchmarks. |
| 📑 [Errors in published data](published-data-errors/README.md) | 1 | Reported numbers that cannot all be true under the stated sample sizes and rounding; private-first, never accusations. |
| 📻 [Lost signals and formats](lost-signals-formats/README.md) | 1 | Decoders for public recordings and undocumented formats, scored by frozen predictions on data received later. |

Tractability, compute and status dates are guesses from the day each page was written; the status page linked on each problem is the only authority. Every page is generated from [`bank/targets.json`](../bank/targets.json): `python3 bank/build_known_unknowns.py`.
