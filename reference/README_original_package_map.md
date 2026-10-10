# Q-Blueprint closed-loop auto-calibration: package map
Run from this directory (`pip install -r requirements.txt`; single CPU core; full sweep ~25 min).

| file | role |
|---|---|
| config.py, drift.py, transmon.py, propagator.py | D1 plant: constants, drift generators, Hamiltonian/pulses, batched propagator |
| oracle.py, evaluate.py | **evaluation only** (gate error Eq. 3, hidden-state evaluator); never imported by agent code |
| plant.py | hidden-state Device with the agent-visible API `run(circuit, shots, Controls) -> counts` |
| calib/ (amplitude, ramsey, bayes, drag, common) | D2/D3 calibration primitives and adaptive Bayesian design |
| agent.py, policies.py, closed_loop.py | agent belief, P0/P1/P2, closed-loop driver |
| qaoa.py, run_sweep.py, d4_d5_analysis.py, d6_ablation.py | D4/D5/D6 analysis |
| d2_d3_studies.py, d2_drag_rerun.py | D2/D3 statistical studies |
| tests/ | `python tests/test_phase2_3.py` (13 tests), `python tests/test_all.py` (18 tests) |
| notebooks/ | D1-D5 (cells verified by headless execution; load precomputed results where noted) |
| results/ | sweep.jsonl (484 runs), aggregate tables, ablation, paired tests, final statement |
| REPORT.md / D6_memo.md | report and 400-word memo |

Official drift seed: 2026. Additional seeds: 1-21. Reproduce the sweep: `python run_sweep.py results/sweep.jsonl 2026,1,...,21`.
