# Monte Carlo Assumptions — Arms Exports / End-Use Enforcement Impossibility

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $29.6B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 2.54 | Confirmed by N=100,000 draws |
| ΔW median (result) | $75.0B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_conflict_casualties` | lognormal | $16.3B | $29.6B | $48.8B | 100K+ conflict deaths/yr enabled by weapons. Sources: SIPRI, UCDP, UNHCR. |
| `C2_humanitarian_crisis` | normal | $14.8B | $18.5B | $22.2B | Refugee flows, famine, infrastructure destruction. Sources: UNHCR, OCHA, MSF. |
| `C3_arms_race_dynamics` | lognormal | $8.1B | $14.8B | $24.4B | Regional arms races, proliferation. Sources: SIPRI, IISS Military Balance. |
| `C4_development_diversion` | lognormal | $4.1B | $7.4B | $12.2B | Military spending crowds out health/education. Sources: World Bank, SIPRI. |
| `C5_end_use_enforcement_failure` | lognormal | $2.0B | $3.7B | $6.1B | Diversion, re-transfer, monitoring failure. Sources: ATT, Conflict Armament Rese |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 1.4 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 1.4) = 0.0340%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 2.5 | 20% DC adj = 2.0 | 40% DC adj = 1.5

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $75B = 0.1% of world GDP ($106T) ✓
- **β_W range**: 2.54 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
