# Living Systems Benchmark (LSB) — Research and Engineering Specification v0.1

**Status:** research specification; proposed, not implemented  
**Date:** 2026-11-17  
**Scope:** Symtropy / Symthaea living-systems research  
**Owners:** Luminous Dynamics  
**Normative language:** MUST/SHOULD describe requirements for a benchmark implementation, not claims about current software.

## Executive thesis

Move from demonstrating emergence to qualifying **viability under disturbance**.

A living-system model is useful only to the extent that it can (1) account for the stocks and flows inside a declared system boundary, (2) predict observations with calibrated uncertainty, (3) distinguish causal mechanisms from coincident patterns, (4) select interventions without violating safety constraints, and (5) remain honest when the system leaves its validated domain.

The proposed Living Systems Benchmark (LSB) is a reproducible suite for energy- and material-constrained adaptive systems. It combines ecological model evaluation, agent-based falsification, deterministic simulation, causal interventions, and safety-constrained control. It is not a claim that Symtropy currently models complete ecosystems or that Symthaea has ecological forecasting skill.

## 1. Scientific starting point: preserve the falsification

The existing Symtropy-consciousness-physics experiments found that shared resource attractors can produce clustering and incidental mutual benefit under multiple controllers. Controller replacement weakened the original interpretation that FEP/social seeking was necessary for cooperation.

The revised hypothesis in `THESIS.md` is appropriately bounded to the tested controller families, resource geometries, and scales. LSB MUST preserve that negative result and make it a baseline, not quietly replace it with a new cooperation narrative.

Operational distinctions:

- **Co-location:** agents occupy the same spatial region.
- **Exchange:** a measurable transfer of energy or material occurs between agents.
- **Mutual benefit:** a transfer or interaction improves outcomes for more than one participant relative to a matched counterfactual.
- **Coordination:** actions are causally interdependent; removing the interaction changes task completion or viability.
- **Resilience:** the system absorbs a specified disturbance and returns to a declared viable region within a measured time and cost.
- **Regeneration:** stocks or functions recover through explicitly represented processes without unaccounted inputs.

No one metric is a substitute for another. A cluster is not evidence of cooperation; a stable population is not evidence of regeneration; a high internal `Phi` value is not an ecological-health measurement.

## 2. Paradigm shifts

### 2.1 From agent-centric rewards to system viability

Represent the system as stocks, flows, agents, habitats, and boundary conditions. Evaluate both agent-level outcomes and whole-system viability. A policy that maximizes one agent's energy while exhausting soil nutrients or exporting pollution fails the system-level test.

### 2.2 From a scalar reward to a viability envelope

Define a vector of state constraints and target ranges rather than hiding trade-offs in one weighted reward:

- minimum viable population / occupancy, where applicable;
- carbon, nitrogen, phosphorus, and water stocks within declared limits;
- energy balance and external energy demand;
- habitat/function thresholds;
- toxic residuals or pollution below declared limits;
- safety and uncertainty constraints.

A run reports each constraint separately, including duration, severity, and recovery. A weighted score MAY be reported for convenience but MUST NOT conceal a failed hard constraint.

### 2.3 From pattern recognition to causal ecological twins

A twin must predict what would happen under specified interventions, not merely replay correlations. Use randomized, paired-seed interventions and counterfactual controls. Report the estimand, treatment assignment, confounders, uncertainty, and conditions where causal identification is not possible.

### 2.4 From closed-loop claims to audited open-boundary accounting

A system is rarely closed. Every simulation MUST declare its boundary and record external imports, exports, transformations, losses, and measurement residuals. Energy, water, and elemental stocks are separate ledgers. "Closed loop" is earned only when the material balance closes within tolerance over a stated interval.

### 2.5 From one best model to a portfolio with abstention

Compare mechanistic, statistical, agent-based, and learned models. Preserve ensembles where model structure is uncertain. The controller must be able to abstain, request more observations, or revert to a conservative policy when uncertainty or distribution shift crosses a declared threshold.

### 2.6 From consciousness metrics as authority to testable optional hypotheses

Symthaea's HDC/CfC, FEP, and candidate integration measures may be tested as predictors or policy components. They MUST be ablated against simpler controllers and MUST NOT be treated as proxies for biodiversity, welfare, ecosystem function, or physical safety. No benchmark outcome establishes consciousness.

## 3. System architecture and responsibilities

| Layer | Responsibility | Required evidence |
|---|---|---|
| Symtropy physics | Spatial dynamics, contacts, transport, deterministic stepping and replay | Solver tests, invariants, replay receipts, matched performance measurements |
| Symtropy living-world model | Typed stocks/flows, resource fields, habitats, disturbances, population dynamics | Balance residuals, process tests, reference trajectories |
| Symthaea | State estimation, prediction, hypothesis generation, policy proposals, uncertainty and abstention | Held-out forecast scores, calibration, ablations, decision evaluations |
| Independent evaluator (SAM / benchmark harness) | Frozen inputs, intervention execution, scoring, invariant checks, evidence manifest | Reproducible report, exact commit/config/data identities |
| Mycelix (later integration) | Provenance, authority, consent and cross-operator evidence exchange | Signed provenance and policy checks; never self-authorization of physical actions |

A Symthaea proposal is not an execution authorization. The benchmark harness owns experiment assignment and scoring. Physical deployments require independent safety systems and human authorization appropriate to their risk.

## 4. Benchmark task suite

LSB is staged. The first tasks reuse existing work; later tasks extend from social-agent experiments toward ecological processes.

| ID | Task | Question | Essential controls |
|---|---|---|---|
| LSB-00 | Resource-attractor null replication | Can the revised by-product-mutualism result be reproduced from frozen inputs? | FEP, well-seeking, greedy, random, stationary; resonance on/off |
| LSB-01 | Finite renewable commons | When do harvest and regeneration rates produce persistence, depletion, or recovery? | No regeneration, fixed harvest, greedy harvest, quota policy |
| LSB-02 | Seasonal / migrating resources | Does information sharing help under relocation and temporal volatility? | Random exploration, local sensing, follower/scrounger, forecast-assisted policy |
| LSB-03 | Genuine complementary exchange | When is active exchange load-bearing rather than incidental co-location? | Transfer disabled, sham transfer, unilateral, reciprocal, matched-energy |
| LSB-04 | Habitat-patch metacommunity | How do dispersal, fragmentation, local extinction, and recolonization interact? | No dispersal, random dispersal, optimal-known dispersal, disconnected patches |
| LSB-05 | Disturbance and recovery | Which policies preserve function and recover after drought/fire/resource shocks? | No-op, reactive threshold, fixed schedule, robust/MPC policy |
| LSB-06 | Coupled water–nutrient–producer–decomposer loop | Can stocks and flows be predicted without creating matter or hiding exports? | Uncoupled compartments, process ablations, measured input/output series |
| LSB-07 | Cross-site transfer | Does a model trained/calibrated on one site transfer to a held-out site or season? | Site climatology, persistence, pooled model, site-specific model |

LSB-00 through LSB-03 are the first practical scope. LSB-04 through LSB-07 require explicit ecological state variables and empirical data adapters.

### LSB-00 to LSB-03 design requirements

Each task MUST:

1. Freeze the world geometry, initial stock distribution, agent count, controller definitions, time step, termination rule, and seed schedule.
2. Use paired seeds across conditions so each treatment sees the same initial state where possible.
3. Record trajectories, not only terminal summaries.
4. Separate spatial proximity, actual exchange, recipient benefit, donor cost, and whole-system outcome.
5. Include a no-op and at least one deliberately weak baseline.
6. Pre-register primary outcomes and multiple-comparison correction.
7. Report negative and inconclusive results.

## 5. Empirical anchors and external benchmarks

LSB SHOULD reuse established datasets and scores rather than claim a new leaderboard prematurely.

### 5.1 NEON Ecological Forecasting Challenge

Use the challenge's published target construction and evaluation design as a forecasting adapter where data and terms permit. The challenge evaluates forecasts by site and horizon, uses CRPS for probabilistic submissions, and compares results to a null forecast. LSB should add calibration, intervention, and constrained-decision reporting around this forecasting foundation.

Documentation: https://projects.ecoforecast.org/neon4cast-docs/Evaluation.html

### 5.2 ILAMB

Use ILAMB's approach to multiple observation confrontations: mean bias, variability, trends, seasonal cycles, spatial patterns, and variable-to-variable relationships. For terrestrial/ecosystem tasks, compare against suitable ILAMB reference products and avoid using a single RMSE as the only quality measure.

Documentation: https://www.ilamb.org/doc/

### 5.3 Jena Experiment / biodiversity–ecosystem functioning

Jena's long-running biodiversity and ecosystem-functioning programme is a candidate empirical anchor. Dataset selection MUST respect the provider's data-use and publication policy, metadata, citation, and co-authorship requirements. Public data access is not permission to ignore attribution or reuse terms.

Data portal: https://jenaexperiment.uni-jena.de/index.php/data/

### 5.4 ODD and model adequacy

Every agent-based task SHOULD publish an ODD-compatible model description (Overview, Design concepts, Details), plus explicit rationale, evaluation purpose, model boundary, uncertainty, and code-to-description mapping. LSB extends documentation with executable configuration and evidence identity; it does not replace ODD.

References:
- https://www.jasss.org/23/2/7.html
- https://doi.org/10.1016/j.envsoft.2022.105559

## 6. Baselines: compare fairly

Each leaderboard row MUST identify its input information, calibration budget, compute budget, and model class. A baseline may not receive less information or less tuning than Symthaea.

### Forecast baselines

- persistence / last observation carried forward;
- seasonal climatology;
- linear or state-space model;
- appropriate process-based ecological model;
- tree-based or other conventional statistical learner;
- ensemble of independently calibrated models.

For probabilistic forecasts, report CRPS (primary where applicable), weighted interval score or log score where appropriate, calibration / coverage, interval width, and horizon-wise skill. Report MAE/RMSE as supplementary point-forecast metrics, not as uncertainty measures.

### Policy baselines

- no intervention;
- fixed schedule;
- threshold / rule-based controller;
- greedy immediate-yield controller;
- robust or model-predictive controller where appropriate;
- oracle upper bound with future information, clearly marked non-deployable.

### Mechanism baselines

- independent-agent null;
- random / stationary movement;
- resource-seeking without social terms;
- interaction terms shuffled or delayed;
- exchange disabled / sham exchange;
- FEP/social gradient ablated;
- harmony/resonance ablated.

The strongest simple baseline is the comparator that matters. Beating a weak random policy is not evidence of state of the art.

## 7. Metrics and qualification gates

Do not collapse all outcomes into a single number. Publish a metric vector and pass/fail gates.

### A. Predictive skill

- CRPS or other task-appropriate proper scoring rule;
- normalized anomaly RMSE / MAE;
- interval coverage at 50%, 80%, and 95% nominal levels;
- calibration error and interval width;
- skill by forecast horizon, site, season, and disturbance regime.

**Proposed target:** at least 5% relative improvement in mean CRPS over the strongest eligible non-Symthaea baseline on a pre-registered held-out set, with no material calibration degradation. This is an aspirational gate, not a current result; first measure baseline difficulty and variance.

### B. Causal and intervention skill

- treatment-effect bias and interval coverage;
- correct sign of response to a specified intervention;
- ranking of interventions by measured outcome;
- regret versus the best feasible policy under the same information;
- performance under randomized and withheld perturbations.

**Proposed target:** improve intervention ranking and outcome over the strongest simple policy on held-out disturbance regimes, while satisfying every hard constraint. Thresholds must be calibrated per task before the blind evaluation.

### C. Accounting integrity

For each conserved stock (k):

`residual_k = initial_k + imports_k - exports_k - final_k - declared_unmeasured_loss_k`

Report absolute and normalized residual by tick and over the full run. Transformations between compartments MUST cancel at system level. Matter must not appear through an unrecorded regeneration term. Energy inputs and dissipation must be tracked separately from elemental mass.

**Qualification gate:** all stock/flow invariants pass; numerical tolerance is declared per solver, scale, and unit before evaluation. Any unexplained source/sink blocks a "closed-loop" claim.

### D. Viability and resilience

Report:
- fraction of time each hard constraint is satisfied;
- fraction of runs avoiding irreversible collapse;
- time to return to a pre-registered viable region after disturbance;
- overshoot / undershoot and cumulative constraint violation;
- external resource input required for recovery;
- residual function loss after recovery;
- distribution across seeds, not only the mean.

**Proposed target:** at equal or lower external inputs, reduce median recovery time by 20% against the strongest eligible baseline without worsening lower-tail viability. This is an aspirational engineering gate, subject to task-specific feasibility.

### E. Ecological function and diversity

Where the model/data support it, report:
- abundance, occupancy, richness, and diversity (including Hill-number views where suitable);
- productivity / biomass and temporal variability;
- nutrient and water stocks/fluxes;
- carbon exchange and storage;
- trophic or functional-group persistence;
- spatial heterogeneity and connectivity.

Never infer ecological health from agent survival, population count, or Phi alone.

### F. Robustness and efficiency

- unseen seed / parameter / geometry / weather / disturbance performance;
- sensitivity and uncertainty decomposition;
- structural ablations and negative controls;
- time, memory, and energy per simulated agent-step and per qualified forecast;
- deterministic replay rate for fixed build/config/input/seed.

**Proposed target:** 100% exact replay for the deterministic test profile, or an explicitly documented tolerance-based replay contract where floating-point hardware makes bitwise equality inappropriate.

## 8. Experimental statistics and evidence discipline

- Use independent runs as the unit of replication; time steps within a run are not independent replicates.
- Pre-register primary outcomes, exclusions, sample-size rationale, and stopping rules.
- Use paired-seed designs where valid; report paired effect sizes and confidence intervals.
- Correct families of confirmatory comparisons (e.g. Holm procedure); label exploratory sweeps separately.
- Include power / detectable-effect analysis before large factorial runs.
- Report all attempted configurations, failures, and missing outputs.
- Separate internal reproduction from independent replication.
- Freeze dataset versions, preprocessing, train/validation/test splits, and model-selection procedures.
- Keep an untouched blind test set for final claims.

Each result should carry a machine-readable manifest with: repository URL, full commit SHA, dirty-tree status, compiler/toolchain, target, feature flags, config digest, dataset/version/split digest, seed list, environment parameters, command, wall time, exit status, raw-output digest, and evaluator version.

A queued or skipped CI job is not a pass. Local execution evidence and runner status are separate fields.

## 9. Proposed typed metabolism model

Before adding more agent behaviours, implement an explicit stock-and-flow layer.

Minimum conceptual types (names are provisional):

- `StockId`: a named compartment stock (water, carbon, nitrogen, phosphorus, stored energy, biomass, pollutant).
- `FlowId`: a transfer or transformation with source, destination, amount, units, and time.
- `BoundaryFlux`: import or export crossing the declared system boundary.
- `Transformation`: a stoichiometric conversion between stocks (e.g. substrate to biomass + residuals + heat).
- `LedgerSnapshot`: opening stocks, flows, closing stocks, and residuals.
- `MetabolismGraph`: compartments and permitted transfers.
- `ViabilityEnvelope`: hard limits, target bands, and recovery criteria.
- `Disturbance`: typed, seeded intervention with an explicit schedule and magnitude.

Design constraints:

1. Units and dimensions are explicit; energy, mass, volume, count, and rates cannot be mixed silently.
2. Internal transfer is represented once and cancels in the whole-system balance.
3. Regeneration MUST identify its external source or transformation pathway.
4. Every flow must be finite and non-negative unless a signed-flow representation is explicitly specified.
5. Invalid units, missing source/destination, overflow, NaN, and undeclared sinks fail closed.
6. Stock bounds and transformations are checked at each tick in debug/qualification modes.
7. Snapshots support deterministic replay and independent recomputation of the balance.

This is deliberately independent of Phi. It provides a generic physical substrate that Symthaea may observe and reason over.

## 10. Immediate implementation sequence

### Slice 1 — accounting correctness (first code increment)

1. Add typed stock/flow/boundary records in a new module without breaking the existing public API.
2. Add tests for internal transfer cancellation, import/export accounting, stoichiometric conversion, depletion, regeneration provenance, invalid values, and replay.
3. Add a small deterministic two-compartment example with known closed-form balances.
4. Add a report that emits per-tick and cumulative balance residuals.
5. Run focused local tests; record exact command, exit code, commit SHA, and any unrun verification.

### Slice 2 — causal resource benchmark

1. Factor the existing LSB-00 resource-well setup into a shared harness.
2. Add paired-seed execution and machine-readable per-run output.
3. Reproduce WELL_ONLY / GREEDY / RANDOM / FEP conditions with resonance on/off.
4. Add actual exchange versus passive proximity as a separate manipulation.
5. Add effect sizes, confidence intervals, and corrected comparisons.

### Slice 3 — resilience benchmark

1. Add seasonal, migrating, depletion, and shock disturbances as typed schedules.
2. Add viability envelopes and recovery metrics.
3. Compare no-op, fixed-rule, greedy, and model-based controllers.
4. Evaluate blind disturbance schedules and held-out seeds.

### Slice 4 — empirical bridge

1. Select one small, permissively reusable public ecological dataset.
2. Preserve source attribution and exact preprocessing.
3. Implement persistence, seasonal, and conventional process/statistical baselines.
4. Evaluate probabilistic forecasts and calibration before any closed-loop claim.
5. Treat Jena/NEON as candidate adapters after dataset permissions and target definitions are verified.

## 11. Current gaps and claim boundaries

Inspection of the current repository shows a useful persistent per-agent `EnergyBudget`, multiple controller/null-model experiments, and a revised thesis. That is not yet a complete ecological metabolism model.

The current energy reservoir tracks an entity's internal energy and counters, while regeneration can add energy. A whole-world, boundary-aware ledger for water, carbon, nitrogen, phosphorus, biomass, imports, exports, and transformation products is not established by that per-agent abstraction alone.

Consequently, the following are research targets, not achieved capabilities:

- ecologically calibrated digital twins;
- empirical biodiversity prediction;
- closed-loop ecosystem material accounting;
- validated optimal restoration policy;
- cross-site generalization;
- physical regeneration or self-repair.

Do not describe LSB as state of the art until it has public baselines, frozen data splits, reproducible runs, and fair comparisons. Do not describe a simulation as a field result.

## 12. Definition of a meaningful win

A meaningful win is not merely more agents alive, higher Phi, denser clusters, or a better aggregate reward.

It is a system that, on held-out conditions:

1. predicts ecological and physical state with calibrated uncertainty;
2. identifies which interactions are causally load-bearing;
3. stays inside declared stock, safety, and viability constraints;
4. recovers from disturbances with less external input or less time;
5. reports when it cannot make a reliable prediction or safe intervention;
6. produces an evidence bundle another researcher can reproduce.

That is the standard Luminous Dynamics should aim to establish.
