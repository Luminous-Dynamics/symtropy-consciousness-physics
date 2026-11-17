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
| Symtropy living-world model | Reuse CIVDYN's shared resource ledger and causal-path substrate; add ecology-specific process models and empirical adapters | Balance residuals, process tests, observation-backed trajectories |
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

## 9. Reuse shared stock-flow and causal infrastructure; add the missing ecology layer

**Do not build a second general-purpose ledger or a second civilization simulator.** The main Symtropy repository already has an active foundation:

- [CIVDYN-001 issue #3390](https://github.com/Luminous-Dynamics/symtropy/issues/3390) defines the bounded socio-ecological dynamics programme.
- [Resource-ledger draft PR #3391](https://github.com/Luminous-Dynamics/symtropy/pull/3391) provides a deterministic water/energy/food stock-flow kernel, dimensional conservation checks, service coverage, and a synthetic two-region shock fixture.
- [Causal-path draft PR #3803](https://github.com/Luminous-Dynamics/symtropy/pull/3803) reuses that ledger as the sole physical stock-flow authority and qualifies matched intervention → mechanism → independently measured outcome paths. Its reported exact-head pass is limited to the deterministic software fixture, not real-world causal identification.
- [Civilizational Systems Science issue #10076](https://github.com/Luminous-Dynamics/symthaea/issues/10076) and [interchange proposal](https://github.com/Luminous-Dynamics/symthaea/blob/research/civbench-social-learning-core-2026-11/research/civbench-social-learning-core/CIVILIZATIONAL_SYSTEMS_SCIENCE_INTERCHANGE_V0_1.md) define the cross-project evidence and model-run semantics.

LSB's distinct contribution is **ecological process fidelity, empirical ecological observations, disturbance/recovery evaluation, and ecology-specific decision quality**. It should consume the CIVDYN ledger and causal receipts through a versioned interface. Any required generalization of the ledger belongs in the shared Symtropy owner, not as a fork in this repository.

Minimum ecology-specific state/process concepts (names provisional):

- `EcologicalCompartment`: soil water, soil organic carbon, mineral nitrogen/phosphorus, living biomass by functional group, detritus, habitat extent/quality.
- `EcologicalProcess`: primary production, nutrient uptake, mortality, grazing/predation, decomposition/mineralization, dispersal/colonization, evapotranspiration, and disturbance response.
- `ProcessFlux`: amount, unit, interval, source/destination compartments, and process/model identity.
- `EcologicalObservation`: measured target, method, spatial/temporal support, uncertainty, provenance, and missingness state.
- `ViabilityEnvelope`: separate ecological and infrastructure thresholds, target bands, and recovery criteria.
- `Disturbance`: typed, seeded intervention with explicit schedule, magnitude, duration, and affected compartments.

Design constraints:

1. Keep water, energy, carbon, nitrogen, phosphorus, biomass and area in dimensionally distinct quantities. Do not create a cross-unit aggregate residual.
2. Every ecological source/sink must be declared at the model boundary; photosynthesis, fixation, deposition, harvesting, respiration, export, and leaching are not interchangeable generic regeneration.
3. Internal transformations must conserve each applicable element even where energy is dissipated or chemical form changes.
4. Biodiversity/function indicators are observation or model outputs, not resource stocks unless they have an explicit physical representation.
5. The ecological adapter MUST NOT recalculate or override balances already owned by CIVDYN; it submits typed flows and consumes receipts.
6. Invalid units, missing process endpoints, overflow, NaN, and undeclared sinks fail closed.
7. Symthaea may encode observations and propose hypotheses, but lossless typed observations remain available to independent scoring.

This layer is deliberately independent of Phi. HDC/CfC/FEP may be compared as candidate inference or control methods, not as privileged definitions of ecological health.

## 10. Immediate implementation sequence

### Slice 1 — ecological process conformance (first code increment)

1. Read and reuse the CIVDYN resource-ledger interface and the shared model-run/claim contract; do not fork generic stock, transfer, or conservation semantics.
2. Specify a small ecological compartment/process profile with explicit units, system boundary, process sources/sinks, and observation targets.
3. Add one analytically checkable synthetic process fixture (for example, detritus decomposition and plant nutrient uptake) whose carbon/nutrient/water balances can be independently recomputed.
4. Add ecology-specific process/receipt tests for valid transformations, unit mismatch, unaccounted loss, boundary flux, and deterministic replay.
5. Publish raw trajectories and per-compartment residuals. State clearly which generic balances are evaluated by CIVDYN and which ecological processes are evaluated by LSB.

### Slice 2 — empirical ecological benchmark

1. Select one small, permissively reusable ecological dataset and freeze data version, observation scope, preprocessing and blind split.
2. Reproduce persistence, seasonal climatology, and a conventional process/statistical baseline before Symthaea.
3. Use CRPS or another suitable proper score for probabilistic forecasts, plus calibration, coverage, interval width and horizon-wise skill.
4. Compare against relevant ILAMB-style observation confrontations; do not treat an agent-based synthetic fixture as empirical validation.
5. Respect data-use, citation, and custodianship conditions for Jena/NEON and any community-held data.

### Slice 3 — causal ecological intervention and resilience

1. Reuse CIVDYN's matched causal-path receipt semantics rather than defining a second causal graph protocol.
2. Add ecological treatment/control/negative-control arms for disturbance, restoration, resource removal, and recovery interventions.
3. Track viability, function, recovery time, external input, biodiversity/functional-group response, and uncertainty separately.
4. Compare no-op, fixed-rule, greedy, conventional model-predictive, robust policy, and Symthaea proposal policies under common initial conditions.
5. Evaluate on blind disturbance schedules and held-out sites/seasons.

### Slice 4 — cross-project integration

1. Map Symthaea biological/ecological primitives to explicit typed observation and process contracts; do not treat a vocabulary embedding as a calibrated ecological state estimate.
2. Consume CIVDYN model-run and intervention receipts.
3. Use Mycelix for rights/provenance and Sol-Atlas for spatial-temporal visualization without creating duplicate state ownership.
4. Preserve fail-closed authority, unknown/stale/out-of-domain states, and independent safety checks.

## 11. Current gaps and claim boundaries

Inspection of the current companion repository shows a useful persistent per-agent `EnergyBudget`, multiple controller/null-model experiments, and a revised thesis. The main Symtropy repository separately has a draft generic resource-ledger implementation (PR #3391) for water, energy and food, plus a draft causal-path conformance crate (PR #3803). These are the correct shared foundations to compose, not duplicate.

The companion per-agent energy reservoir is not a whole-world ecological model. The current CIVDYN resource vector also does not, by itself, establish calibrated carbon/nitrogen/phosphorus cycling, species/functional-group dynamics, biodiversity observations, habitat processes, or field-validated restoration responses. Those are the distinct LSB gaps.

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
