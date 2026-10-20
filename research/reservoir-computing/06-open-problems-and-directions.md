# Open Problems and Research Directions

IDs refer to [bibliography.md](bibliography.md). The IEEE Task Force on RC (IJCNN 2026 special session [R8]) names three community priorities: (1) theory of stability, adaptability, and generalization; (2) hybrid RC and deep-learning architectures; (3) energy-aware neuromorphic, photonic, and spintronic hardware. The problems below are drawn from the 2025–26 literature and grouped under those priorities.

## A. Theory

| Problem | Why it matters | Starting points |
|---|---|---|
| Task-general performance prediction | Theory now predicts memory and recall tasks [T1] but not forecasting or classification in general | Perceptron theory [T1]; IPC decomposition by eigenmode [T2] |
| Expressivity cost of linear, diagonal, or circulant reservoirs | ParalESN/FRESCO give up dense nonlinear recurrence for speed [A1, A2]. When does this hurt? | SSM approximation theory; universality proofs for ParalESN |
| Noise-aware capacity | Total IPC ignores fragility [T2]; noise bounds learnability [T4] | SNR-weighted modal IPC; ROME [T5] |
| Scaling laws | Bigger reservoirs trade stability against reach [T3]; there is no RC equivalent of neural scaling laws | DMFT [T3]; heterogeneity |
| Quantum vs classical separation | No demonstrated advantage under realistic resources [R2, T4] | Risk bounds [T8]; matched-resource experiments |

## B. Architectures and algorithms

1. **Hybrid RC and deep models.** Use fixed reservoirs as cheap long-memory front-ends to trained models (EchoFormer [A4]), or as frozen SSM layers (RSSM [A9], ParalESN [A1]). Open question: what is the best split between frozen and trained parameters for a given compute budget?
2. **Beyond random matrices.** Structured feature libraries (NGRC [A8], KARC [A3]) vs learned features (Adaptive NVAR [A5]). How much training can be added before the efficiency argument for RC disappears?
3. **Training-free and programmable readouts.** Analytical untrained readouts [T1] and programmed readouts [H1] suggest RC without any data fitting for some function classes.
4. **High-dimensional spatiotemporal systems** (weather, turbulence, PDEs). Cross-scale and multi-resolution reservoirs, hybrid physics+RC models, KARC on PDEs [A3]. Parallel and local reservoirs are needed to scale.
5. **Online, continual and federated RC.** The closed-form readout makes RC well suited to on-device adaptation. This is under-explored relative to the opportunity.

## C. Hardware

1. **Noise and variability.** This is the main barrier. Solutions to validate at scale: ensembles [A7], GRC [A6], chaos control [H2], optimal encoding [T5].
2. **Standard metrics.** Energy per MAC or per inference, latency, and footprint alongside accuracy, plus a matched software baseline [R1].
3. **Photonic nonlinearity.** Strong, fast, controllable, fabrication-tolerant nonlinear elements; low-loss integration; on-chip gain [R1].
4. **Co-design.** Jointly optimize masks, encoding, and operating point with physics-aware ML instead of heuristics [R1, T5].
5. **Killer applications.** Optical and RF equalization, in-sensor temporal processing, robotics and morphological computation, and processor microarchitecture (branch prediction [H7]).
6. **Biological substrates.** Longevity, transfer between cultures [H2], and the ethics and governance of organoid computing.
7. **Quantum.** Shot-efficient measurement design, memory engineering via reset and mid-circuit measurement, multitask capacity, and honest benchmarking [R2].

## D. Methodology (high leverage, low cost)

- Adopt the reporting checklists of [R3] and [R2] as defaults.
- Build a shared RC leaderboard on versioned benchmarks (`dysts`, UCR/UEA, Monash) with matched tuning budgets. Nothing like this exists yet. It would make a real meta-analysis possible and would be a strong community contribution.
- Always include modern baselines (SSMs, PatchTST) and simple ones (persistence, context parroting [B2]).

## Opportunities for a new project

Ranked by how feasible they are for a small team and how much impact they could have:

1. **A reproducible RC benchmark suite and leaderboard.** It directly fills the missing-meta-analysis gap. Run ESN, NGRC, ParalESN, FRESCO, and KARC against LRU/S4/Mamba/PatchTST on `dysts` + UCR + Monash with matched budgets and multiple seeds.
2. **Independent replication of the 2026 efficiency claims** (FRESCO's up-to-1000× energy, EchoFormer vs PatchTST) under a fixed protocol.
3. **Noise-robustness study**: inject realistic hardware noise models into software reservoirs and test ensemble averaging [A7] vs SNR-aware readouts derived from [T2].
4. **ParalESN/FRESCO as frozen front-ends** inside a small trained model, mapping the Pareto frontier of trained-parameter fraction vs accuracy.
