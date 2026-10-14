# PGLib-OPF v23.07: an AC-feasible operating point strictly cheaper than the published baseline AC-OPF solution

🔌 **Power grids** · standard · tractability ★★☆☆☆ · compute: laptop-hours · open as of 2026-10-14

## The problem

PGLib-OPF (github.com/power-grid-lib/pglib-opf), curated by the IEEE PES Task Force on Benchmarks for Validation of Emerging Power System Algorithms (lead curator Carleton Coffrin; report arXiv:1908.02788), is the standard AC-OPF benchmark set: MATPOWER-format cases in three groups, typical (root *.m), congested (api/) and small angle difference (sad/). HONEST STATUS (checked 2026-10-14): PGLib does NOT publish a maintained best-known-solution or best-bound table. The only per-case numbers it publishes are BASELINE.md: a single run of PowerModels.jl v0.19.9 + Ipopt v3.14.4 (local NLP solver, HSL ma27) on v23.07. For each case it reports the DC and AC objectives in $/h to 5 significant figures (e.g. pglib_opf_case14_ieee AC 2.1781e+03, case118_ieee 9.7214e+04, case1354_pegase 1.2588e+06), plus root QC and SOC relaxation gaps. The gap is a relaxation gap, not a proven optimality gap. Some are large: case8387_pegase 54.61% QC; case6495_rte 15.09%; case30_as__api 44.61%; case1803_snem__api 39.54%; case3970_goc__api 38.76%; case8387_pegase__sad 47.49%. The repo was last pushed 2023-07-24 (tag v23.07). Gap-closing work since then is scattered over papers that use different versions, so their numbers do not transfer: Gopinath, Hijazi, Weisser, Nagarajan, Yetkin, Sundar and Bent (LANL; arXiv:1910.03716) closed gaps with SDP bound tightening on PGLib 19.05 and NESTA 0.3 cases up to 300 buses. Wang, Magron and Lasserre (CS-TSSOS; arXiv:2109.10005) certified 1% optimality on many PGLib v20.07 cases, e.g. case5_pjm AC 1.7552e4 with a 1.5th-order bound of 1.7534e4 (0.10% gap). They left gaps on others, e.g. their v20.07 2312_goc api row: AC 5.7152e5, bound 5.2710e5, 7.77%. Iranpour and Narimani (arXiv:2505.18435) ran QC branch-and-bound on cases up to 57 buses. Whether the BASELINE Ipopt points are globally optimal is therefore open for most v23.07 cases, especially the large ones. This target asks for the only thing that can be checked mechanically against a published number: a feasible point that is cheaper than the published v23.07 reference solution. The BASELINE value is a reference local solution, NOT a best-known value or a proven bound; the bar is low but unambiguous. Credit: the IEEE PES task force and Carleton Coffrin for the dataset; the PowerModels.jl team (LANL) for the baseline.

## What counts as a win

Success means a solution file for one case file taken unmodified from tag v23.07 of https://github.com/power-grid-lib/pglib-opf (root, api/ or sad/, with sha256 recorded). The file gives, per bus, Vm (p.u.) and Va (deg or rad, stated), and per in-service generator, Pg and Qg (MW, MVAr). It must satisfy all of the following. (a) A standalone checker written from the PGLib model (README/MODEL.tex) and the MATPOWER format computes branch flows from the full Pi-model: r, x, b charging, tap ratio (0 read as 1), phase shift, bus shunts Gs/Bs, status = 1 elements only. With that, it finds: nodal P and Q balance at every bus with absolute mismatch <= 1e-6 p.u. on baseMVA; Vmin <= Vm <= Vmax, Pmin <= Pg <= Pmax and Qmin <= Qg <= Qmax with violation <= 1e-6 p.u.; angmin <= Va_f - Va_t <= angmax on every branch; |S| <= rate_a at BOTH branch ends, violation <= 1e-6 p.u. (rate_a only, never rate_b/rate_c); the reference bus angle = 0. (b) Generation cost is the MATPOWER gencost polynomial in $/h evaluated at Pg in MW, summed over in-service generators. It is strictly less than the case's AC ($/h) entry in the live BASELINE.md (https://raw.githubusercontent.com/power-grid-lib/pglib-opf/master/BASELINE.md, re-fetched before claiming) minus half a unit in its last printed digit (e.g. for 1.2588e+06, cost < 1,258,750). (c) Robustness against tolerance gaming: fix every non-slack generator's Pg and every generator bus's Vm from the file and run a Newton AC power flow in a second, independent tool (MATPOWER runpf or pandapower). It converges; the resulting point satisfies every limit in (a) with violation <= 1e-4 p.u., including the slack generator's P and Q; and the cost recomputed from the power-flow result still meets (b). (d) Calibration: before any claim, the same checker, run on a reference solution the skeptic produces themselves with PowerModels.jl + Ipopt (ACPPowerModel) on v23.07, reproduces the BASELINE AC value to its printed 5 significant figures for pglib_opf_case14_ieee (2.1781e+03), pglib_opf_case118_ieee (9.7214e+04) and pglib_opf_case1354_pegase (1.2588e+06). (e) A live literature search (arXiv, IEEE Xplore, Google Scholar for the case name plus 'v23.07' or the cost value) finds no published feasible point for the same v23.07 case at or below the claimed cost; if one exists, the claim is a replication. Nothing is submitted to the PGLib repo by the agent; any issue or PR is for the human.

## Partial wins

- **p1:** A certified lower bound for one v23.07 case whose BASELINE QC gap is >= 5%, closing at least half of that gap: bound L >= AC_baseline * (1 - QCgap/200). Certified means a dual solution of a convex relaxation (SOC, QC, SDP or a moment/SOS level) of that exact v23.07 case. A skeptic's script checks it independently: verify dual feasibility, then compute a rigorous bound that subtracts the residual times the variable bounds (Jansson-style), in interval or rational arithmetic. A solver-reported relaxation objective without such a certificate does not count. (e) applies with 'bound' in place of 'point'.

## How a win is checked

The skeptic downloads the named v23.07 .m file and checks its sha256. They write their own MATPOWER parser and AC-OPF feasibility checker from the format spec, without reading the claimant's code. First the calibration in (d): run PowerModels.jl + Ipopt on the three named cases, feed those points to the checker, and confirm 2.1781e+03, 9.7214e+04 and 1.2588e+06. Then run the checker on the claimed point at 1e-6 p.u. tolerances and recompute the gencost in $/h. Then pin the setpoints and run MATPOWER runpf or pandapower runpp, check all limits including the slack at 1e-4 p.u., and recompute the cost. Finally, re-fetch BASELINE.md and compare against the printed value minus the half-digit margin. Minutes for cases up to ~10k buses.

## Is it still open?

Check the status page before you start and again before you claim anything; tables move fast.

- <https://raw.githubusercontent.com/power-grid-lib/pglib-opf/master/BASELINE.md>

## Sources

- <https://github.com/power-grid-lib/pglib-opf>
- <https://raw.githubusercontent.com/power-grid-lib/pglib-opf/master/BASELINE.md>
- <https://raw.githubusercontent.com/power-grid-lib/pglib-opf/master/README.md>
- <https://github.com/power-grid-lib/pglib-opf/tree/v23.07>
- <https://github.com/power-grid-lib/pglib-opf/issues/48>
- <https://arxiv.org/abs/1908.02788>
- <https://arxiv.org/abs/1910.03716>
- <https://arxiv.org/abs/2109.10005>
- <https://arxiv.org/abs/2505.18435>

## Ideas to start from

Starting points, not instructions. The best wins came from angles nobody listed.

- Multistart Ipopt from many random and relaxation-derived starts (SOC/QC/SDP primal solutions projected onto the AC manifold), in polar and rectangular formulations; on non-convex AC-OPF, different starts reach different local optima, and BASELINE is one start per case.
- Run a different NLP solver (Knitro-free alternatives: MadNLP, ExaModels on CPU, MATPOWER MIPS) with tight tolerances, then polish with Newton on the active set; compare against BASELINE across all 3 groups to find cases where any solver beats the printed value by more than the rounding margin.
- Prioritise cases with large BASELINE relaxation gaps (case8387_pegase TYP and sad, case6495_rte, case30_as__api, case1803_snem__api, case3970_goc__api), but note that a large relaxation gap usually reflects a weak relaxation, not a suboptimal AC point; CS-TSSOS closed the v20.07 30_as api gap from 42.96% to 0.01% via the bound side.
- Spatial branch-and-bound or QC/SOC OBBT (PowerModels + Alpine.jl or Gravity) on mid-size cases to search for better incumbents while producing bounds that could feed partial win p1.

## Traps

False wins others have fallen for. A claim that walks into one of these will not survive the skeptics.

- The BASELINE AC value is a single local solve to 5 significant figures, not a best-known value: an 'improvement' smaller than half the last printed digit is rounding noise and does not count.
- Tolerance gaming: Ipopt's default constr_viol_tol and the PowerModels per-unit scaling let a point violate thermal or voltage limits slightly and look cheaper; the 1e-6 p.u. check and the independent Newton power-flow re-solve in (c) exist to catch this.
- Off-model tricks do not count: using rate_b/rate_c, dropping angmin/angmax, switching lines off, relaxing generator bounds, or editing the case file (including 'fixing' the suspicious line/PST pairs in the 6xxx_rte cases reported in open issue #48).
- Version drift: v20.07/v21.07 cases differ from v23.07 (e.g. CS-TSSOS's v20.07 118_ieee api AC 2.4224e5 vs v23.07 BASELINE 2.4961e+05); compare only v23.07 file against v23.07 BASELINE row.
- Cost units: gencost is in $/h with Pg in MW; PowerModels internally uses per-unit Pg, and a mis-scaled quadratic term changes the objective by orders of magnitude.
- Lower bounds: a relaxation objective printed by a solver (Mosek 'slow progress' is common on these SDPs per Wang, Magron and Lasserre) is not a certificate; only a rigorously checked dual bound counts for p1.
- No best-known table exists elsewhere either: the ARPA-E GO Competition site (gocompetition.energy.gov) was unreachable on 2026-10-14 (expired TLS certificate, then HTTP 400), so its leaderboards cannot be used as a status source.

## Point your agent at it

```
set up SUET: https://github.com/Milbaxter/SUET and hunt known-unknowns/power-grids/pglib-opf-v23-beat-baseline-ac.md
```

Already set up? Say `run SUET on pglib-opf-v23-beat-baseline-ac`. Your agent follows [AGENTS.md](../../AGENTS.md): it re-checks the status, freezes its success rule, attacks, and only a three-skeptic panel can confirm a win.

---

_Generated from [`bank/targets.json`](../../bank/targets.json) (id `pglib-opf-v23-beat-baseline-ac`). Found it solved, stale or wrong? Open an issue or a pull request against that file._
