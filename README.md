# SAPM Monte Carlo — Arms Exports / End-Use Enforcement Impossibility

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Arms Exports (End-Use Enforcement Impossibility).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **2.54** |
| β_W mean | 2.59 |
| β_W std | 0.49 |
| **90% CI** | **[1.9, 3.5]** |
| 99% CI | [1.7, 4.0] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$75.0B/yr** |
| Π (revenue) | $29.6B/yr |

**β_W = 2.54** means the arms exports industry destroys **$2.54 in system
welfare for every $1.00 in revenue** — across 5 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-arms-exports.git
cd sapm-mc-arms-exports
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 2.54` and `ΔW median : $75.0B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_conflict_casualties | $29.6B | [$17.9B, $48.6B] | Lognormal |
| C2_humanitarian_crisis | $18.5B | [$14.8B, $22.2B] | Normal |
| C3_arms_race_dynamics | $14.8B | [$9.0B, $24.4B] | Lognormal |
| C4_development_diversion | $7.4B | [$4.5B, $12.2B] | Lognormal |
| C5_end_use_enforcement_failure | $3.7B | [$2.2B, $6.1B] | Lognormal |
| **Total ΔW** | **$75.0B** | **[$55.6B, $102.7B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 1.4 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0340%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Arms Exports (End-Use Enforcement Impossibility)*.
> GitHub: epostnieks/sapm-mc-arms-exports.
> https://github.com/epostnieks/sapm-mc-arms-exports
