# Annotated Bibliography

Compiled 2026-10-01. Weighted toward 2026, with key 2025 work and a few foundational papers for context.
"PDF" means the file is in [`papers/`](papers/). Summaries come from the abstracts. Items marked † were also read in full or in part (conclusions, tables).

Tags: `[review]` survey/review · `[theory]` · `[algo]` new model/algorithm · `[hw]` physical hardware · `[quantum]` · `[bench]` benchmarking/evaluation · `[app]` application

---

## Reviews and surveys

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| R1 | † Abdalla, Van der Sande, Argyris, Pavanello, Soriano, Rontani — *Photonic reservoir computing: a thematic review* | J. Phys. Photonics 8(2) 022003, Apr 2026. DOI 10.1088/2515-7647/ae2e67 | review, hw | [pdf](papers/Abdalla2026-photonic-RC-thematic-review.pdf) |
| R2 | † Tariq, Talha, Ali, Diyan, Chatzinotas — *Quantum Reservoir Computing: Recent Advances and Future Directions* | arXiv 2607.18552, Jul 2026 | review, quantum | [pdf](papers/arXiv-2607.18552.pdf) |
| R3 | † Wringe, Trefzer, Stepney — *Reservoir Computing Benchmarks: a tutorial review and critique* | Int. J. Parallel, Emergent & Distributed Systems 40(4), 2025 (arXiv 2405.06561) | review, bench | [pdf](papers/arXiv-2405.06561.pdf) |
| R4 | te Vrugt — *An introduction to reservoir computing* | Book chapter, *AI and Intelligent Matter* (Springer, 2026); arXiv 2412.13212 | review | [pdf](papers/arXiv-2412.13212.pdf) |
| R5 | Liu et al. — *Physical reservoir computing for Edge AI applications* | The Innovation Materials 3(2) 100127, Mar 2025 | review, hw | [link](https://www.the-innovation.org/article/doi/10.59717/j.xinn-mater.2025.100127) |
| R6 | Jiao et al. — *Memristive Physical Reservoir Computing* | Advanced Science, Apr 2026 | review, hw | [link](https://advanced.onlinelibrary.wiley.com/doi/10.1002/advs.75476) |
| R7 | Park et al. — *Device-Level Implementation of Reservoir Computing With Memristors* | Advanced Intelligent Systems, 2026 | review, hw | [link](https://advanced.onlinelibrary.wiley.com/doi/full/10.1002/aisy.202500843) |
| R8 | IEEE Task Force on RC — IJCNN 2026 special session call (Paassen, Tanaka, Ceni, Gallicchio) | 2026 | community agenda | [link](https://sites.google.com/view/reservoir-computing-tf/activities/ijcnn-2026-special-session) |

## Theory

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| T1 | † Kleyko, Kymn, Frady, Loutfi, Sommer — *Towards a Comprehensive Theory of Reservoir Computing*. Uses perceptron theory to predict memory capacity and accuracy for 30 ESN variants; proposes an untrained readout that beats earlier ESNs; finds regular-simplex readout geometry, as in deep nets. | arXiv 2511.14484, Nov/Dec 2025 | theory | [pdf](papers/arXiv-2511.14484.pdf) |
| T2 | Abdalla, Rontani — *Organization of computation in reservoir computing*. Eigen-spectral decomposition links degree-wise information-processing capacity to state-space modes. Much of the capacity sits in low-energy modes that noise destroys. | arXiv 2607.17858, Jul 2026 | theory | [pdf](papers/arXiv-2607.17858.pdf) |
| T3 | Qian, Fiete — *Fundamental performance bounds on reservoir computing*. Separates failures into *stability-limited* (independent of the algorithm) and *reach-limited* (dependent on the algorithm). Makes DMFT scaling bounds. Scaling up network size trades stability against reach; neuronal diversity removes the trade-off. | Phys. Rev. E 112, 054214, Nov 2025 | theory | [link](https://journals.aps.org/pre/abstract/10.1103/t4hg-vpmr) |
| T4 | Polloreno — *Restrictions on Physical Stochastic Reservoir Computers*. A noisy analog RC can only do a polynomial amount of learning, even though its latent space is exponentially large and even with exponential post-processing. | Phys. Rev. Applied 24, 014031, 2025 | theory, hw | [pdf](papers/arXiv-2307.14474.pdf) |
| T5 | Cui, Nakajima, Aihara — *Optimal Memory Encoding Through Fluctuation-Response Structure (ROME)*. Optimal input encoding is a geometric problem set by the system's fluctuation-response structure. Matches backprop-optimized encoders and works on non-differentiable hardware. | arXiv 2603.21666, Mar 2026 | theory, hw | [pdf](papers/arXiv-2603.21666.pdf) |
| T6 | dos Santos, Bollt — *On the emergence of numerical instabilities in NGRC*. The feature matrix is ill-conditioned with short lags, high polynomial degree, or short training data. SVD-based solves work even without regularization. | arXiv 2505.00846, 2025 | theory, algo | [pdf](papers/arXiv-2505.00846.pdf) |
| T7 | Hurley, Shaheen — *Reservoir computing with large valid prediction time for the Lorenz system*. Reports VPT above 30 Lyapunov times on noiseless Lorenz; VPT can be predicted from the error in the first few steps; introduces "valid ground-truth time" for solver limits. | arXiv 2508.06730, Aug 2025 | bench | [pdf](papers/arXiv-2508.06730.pdf) |
| T8 | *Quantum Reservoir Computing and Risk Bounds*: Rademacher-complexity generalization bounds for QRC classes | arXiv 2501.08640, 2025 | theory, quantum | [link](https://arxiv.org/abs/2501.08640) |

## Algorithms and architectures

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| A1 | † Pinna, Lagomarsini, Ceni, Gallicchio — *ParalESN: parallel information processing in RC*. Diagonal complex linear recurrence; keeps the echo state property and universality. Reaches 96–97% on sMNIST/psMNIST in about 3 min, versus 98–99% for LSTM/Transformer/S4/LRU/Mamba at 10–150 min and 10–40× the energy. | ICML 2026 (arXiv 2601.22296) | algo | [pdf](papers/arXiv-2601.22296.pdf) |
| A2 | † Schertler, Runge, Ceni, Kappel, Gallicchio — *Frequency Domain Reservoir Computing (FRESCO)*. O(N) dense nonlinear recurrent updates in the frequency domain (circulant reservoirs). Matches deep sequence models on long-horizon forecasting at up to about 1000× less energy. | arXiv 2606.24969, Jun 2026 | algo | [pdf](papers/arXiv-2606.24969.pdf) |
| A3 | Huang, Kurths, Tang — *Kolmogorov-Arnold Reservoir Computing (KARC)*. Replaces the reservoir with explicit KAN-style basis expansions and closed-form training. Beats prior RC on PDE benchmarks and also plugs into diffusion models. | arXiv 2606.19984, Jun/Jul 2026 | algo | [pdf](papers/arXiv-2606.19984.pdf) |
| A4 | Liu, Xu — *Echo Flow Networks (EFN / EchoFormer)*. ESN-based with matrix-gated random activations and a dual-stream design. Claims 4× faster training, 3× smaller, and about 20% relative error reduction vs PatchTST on ETT/Weather/etc. | arXiv 2509.24122 v3, Aug 2026 (under review) | algo | [pdf](papers/arXiv-2509.24122.pdf) |
| A5 | Azimov et al. — *Adaptive NVAR*. Delay-embedded linear inputs plus a shallow trainable MLP for features. Beats NVAR, leaky ESN, and hybrid ESN on noisy chaotic data. | arXiv 2507.08738 v3, Sep 2026 | algo | [pdf](papers/arXiv-2507.08738.pdf) |
| A6 | Kubota, Imai, Tsunegi, Nakajima — *Reservoir Computing Generalized (GRC)*. Drops the requirement that the reservoir respond reproducibly. Non-reproducible substrates and even spatiotemporal chaos become usable. | arXiv 2412.12104 (Nature-family follow-ups 2025) | algo, hw | [pdf](papers/arXiv-2412.12104.pdf) |
| A7 | Nakamura, Kubota, Imai, Tsunegi, Notsu, Nakajima — *Ensemble Reservoir Computing for Physical Systems (ERC)*. Ensemble averaging over spatially multiplexed copies cancels noise. A spin-torque oscillator reaches 99% on a task where conventional STO-RC is at chance. | arXiv 2601.21807, Jan 2026 | algo, hw | [pdf](papers/arXiv-2601.21807.pdf) |
| A8 | Gauthier, Bollt, Griffith, Barbosa — *Next generation reservoir computing* (NGRC / NVAR), the foundational paper | Nat. Commun. 12, 5564 (2021) | algo | [pdf](papers/arXiv-2106.07688.pdf) |
| A9 | *Harnessing Untrained Dynamics: A Reservoir Computing Approach to State-Space Models (RSSM)* | OpenReview, 2025–26 | algo | [link](https://openreview.net/forum?id=azNpwiObPp) |
| A10 | Di Antonio et al. — *Linearizing and Forecasting: an RC route to digital twins of the brain*. Linear RNN reservoirs for fMRI BOLD forecasting. | Advanced Science, 2026 | algo, app | [link](https://advanced.onlinelibrary.wiley.com/doi/10.1002/advs.202517234) |

## Physical, biological and quantum hardware

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| H1 | Terasaki, Imai, Kim, Nakajima — *Programming Spintronic Reservoir Computing*. MRAM-based. Maps prescribed input-output functions directly to the readout, with no training data. Includes a programmability metric and demonstrates a Newton solver. | arXiv 2609.13169, 2026 | hw | [pdf](papers/arXiv-2609.13169.pdf) |
| H2 | Kim, …, Beggs, Gazzola — *Computing with Living Neurons: Chaos-Controlled RC with Knowledge Transplant*. Optical control of neuron cultures gives about 300% better accuracy and longevity. Learned readouts transfer between attractor-equivalent cultures. | arXiv 2604.02552, Apr 2026 | hw (bio) | [pdf](papers/arXiv-2604.02552.pdf) |
| H3 | Park, Watabe, Sunada, Yamagami, Uchida — *Photonic reservoir computing with complex networks*. Implemented on an SLM; small-world topology gives the best memory capacity and prediction; connectome-based variant included. | arXiv 2607.23285, Jul 2026 | hw | [pdf](papers/arXiv-2607.23285.pdf) |
| H4 | Donald et al. — *Nanoporous NbOx oxide memristor RC*. Demonstrates XOR, image recognition, and Lorenz-63 prediction. | arXiv 2602.04619, Feb 2026 | hw | [pdf](papers/arXiv-2602.04619.pdf) |
| H5 | *All-Optically Controlled Memristive RC with Bipolar and Parallel Coding* | Nat. Commun., Jul 2026 | hw | [link](https://www.nature.com/articles/s41467-026-76258-0) |
| H6 | *Reservoir Computing with Heterogeneous Magnetic Metamaterials* | arXiv 2608.08879, 2026 | hw | [link](https://arxiv.org/abs/2608.08879) |
| H7 | *RC for branch prediction in pipelined processors using CMOS memristor devices* | arXiv 2607.27140, 2026 | hw, app | [link](https://arxiv.org/abs/2607.27140) |
| H8 | *A Reservoir Computing Approach to Quantum Gate Synthesis* | arXiv 2607.13887, 2026 | quantum, app | [link](https://arxiv.org/abs/2607.13887) |
| H9 | *Quantum RC for Statistical Classification in a Superconducting Quantum Circuit* | arXiv 2602.15474, 2026 | quantum | [link](https://arxiv.org/abs/2602.15474) |
| H10 | *Minimalistic and scalable quantum RC enhanced with feedback* | npj Quantum Inf., 2025 | quantum | [link](https://www.nature.com/articles/s41534-025-01144-4) |
| H11 | Cai et al. — *Brain organoid reservoir computing (Brainoware)*, foundational | Nat. Electron., Dec 2023 | hw (bio) | [link](https://www.nature.com/articles/s41928-023-01069-w) |
| H12 | *Reservoir Computing with a Single Oscillating Gas Bubble: Emphasizing the Chaotic Regime* | arXiv 2504.07221, 2025 | hw | [link](https://arxiv.org/abs/2504.07221) |

## Benchmarks, evaluations and the competitive landscape

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| B1 | Häußer — *ESNs for Time Series Forecasting: Hyperparameter Sweep and Benchmarking*. On M4 monthly/quarterly series, a simple ESN ties ARIMA/TBATS on MASE (monthly) and ranks 2nd (quarterly). ES-RNN is best overall. | arXiv 2602.03912 v4, Sep 2026 | bench | [pdf](papers/arXiv-2602.03912.pdf) |
| B2 | Zhang, Gilpin — *Context parroting: a simple but tough-to-beat baseline for foundation models in SciML*. Copying the context beats time-series foundation models on chaotic systems at a fraction of the compute. | ICLR 2026 (arXiv 2505.11349) | bench | [pdf](papers/arXiv-2505.11349.pdf) |
| B3 | Yao, Jiang — *PAC-LLM: LLM-powered long-term chaotic forecasting* | arXiv 2608.29579, Aug 2026 | bench | [link](https://arxiv.org/abs/2608.29579) |
| B4 | *Echos: an R package for automatic time-series forecasting using ESNs* | The R Journal RJ-2026-040 | tooling | [link](https://journal.r-project.org/articles/RJ-2026-040/) |
| B5 | Prediction of chaotic time series using RNNs and RC: a comparative study | Machine Learning with Applications, 2022 | bench | [link](https://pmc.ncbi.nlm.nih.gov/articles/PMC9230140/) |
