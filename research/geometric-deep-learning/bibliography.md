# Annotated Bibliography: Geometric Deep Learning

Compiled 2026-10-01. Weighted toward 2026, with key 2025 work and foundational references.
"PDF" means the file is in [`papers/`](papers/). Items marked † were also read in full or in part (conclusions, results); the rest are summarized from abstracts.

Tags: `[review]` · `[position]` · `[theory]` · `[algo]` · `[bench]` · `[sci]` science application · `[gfm]` foundation model

---

## Reviews, surveys and position papers

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| R1 | Bronstein, Bruna, Cohen, Veličković — *Geometric Deep Learning: Grids, Groups, Graphs, Geodesics, and Gauges*. The foundational "proto-book" (5G blueprint). | arXiv 2104.13478, 2021 | review | [pdf](papers/arXiv-2104.13478.pdf) |
| R2 | Sáez de Ocáriz Borde, Bronstein — *Mathematical Foundations of Geometric Deep Learning*. 78-page review of the mathematics required for GDL. | arXiv 2508.02723, Aug 2025 | review | [pdf](papers/arXiv-2508.02723.pdf) |
| R3 | Arroyo, Barbero, Blayney, Bronstein, Dong, Liò, Pascanu, Vandergheynst — *A Survey on Over-Smoothing and Over-Squashing: Unified Propagation Perspectives on GNNs and Transformers*. Over-smoothing and over-squashing correspond to rank collapse and representational collapse in decoder Transformers, with attention read as a learned adjacency. | TMLR 2026 | review, theory | [link](https://mlanthology.org/tmlr/2026/arroyo2026tmlr-survey/) |
| R4 | *A Survey of Graph Transformers: Architectures, Theories and Applications* | ACM Computing Surveys, Aug 2026 | review | [link](https://dl.acm.org/doi/full/10.1145/3834764) |
| R5 | Wang, Liu, Ma, Li, Zhang et al. — *Graph Foundation Models: A Comprehensive Survey*. Taxonomy of backbone, pretraining, and adaptation; scope is universal, task-, or domain-specific. Challenges: structural alignment, heterogeneity, scalability, evaluation. | arXiv 2505.15116, 2025 (93 pp, 438 refs) | review, gfm | [pdf](papers/arXiv-2505.15116.pdf) |
| R6 | Attali, Buscaldi, Pernelle — *Graph Rewiring in GNNs to Mitigate Over-Squashing and Over-Smoothing: A Survey* | arXiv 2411.17429, updated 2026 | review | [pdf](papers/arXiv-2411.17429.pdf) |
| R7 | † Bechler-Speicher, Finkelshtein, Frasca, Müller, Tönshoff, Siraudin, Zaverkin, Bronstein, Niepert, Perozzi, Galkin, Morris — *Position: Graph Learning Will Lose Relevance Due To Poor Benchmarks*. Benchmarks are too narrow (2D molecules, citation graphs) and evaluation is fragmented and overfitting-prone. Calls for real applications (combinatorial optimization, relational databases, chip design), rigorous protocols, and domain experts. | ICML 2025 (position) | position, bench | [pdf](papers/arXiv-2502.14546.pdf) |
| R8 | Morris et al. — *Future Directions in the Theory of Graph Machine Learning* | ICML 2024 (position) | position, theory | [pdf](papers/arXiv-2402.02287.pdf) |
| R9 | † Creed, …, Cheng, Krishnapriyan, Ceriotti, Langer, Frost, Ganose, Kapil, Butler — *Six Open Questions in MLIP Foundation Models*. Q1: what is a foundation MLIP? Q2: more data, better data, or better models? Q3: long-range interactions? Q4: can MLIPs discover new physics? Q5: can they scale to useful simulations? Q6: how do we know they are any good? | arXiv 2606.07327, Jun 2026 | position, sci | [pdf](papers/arXiv-2606.07327.pdf) |
| R10 | Papamarkou, Birdal, Bronstein, Carlsson, …, Veličković — *Position: Topological Deep Learning is the New Frontier for Relational Learning* | ICML 2024 (position) | position | [link](https://pmc.ncbi.nlm.nih.gov/articles/PMC11973457/) |
| R11 | *Generative Modeling in Protein Design: Neural Representations, Conditional Generation, and Evaluation Standards* | arXiv 2603.26378, 2026 | review, sci | [link](https://arxiv.org/abs/2603.26378) |
| R12 | *Knowledge Graphs Meet Graph Neural Networks: A Comprehensive Survey* | arXiv 2607.09666, 2026 | review | [link](https://arxiv.org/abs/2607.09666) |

## Graph learning: theory and architectures

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| G1 | Arnaiz-Rodriguez, Errica — *Oversmoothing, Oversquashing, Heterophily, Long-Range, and more: Demystifying Common Beliefs in Graph ML*. Gives formal counterexamples to widely repeated universal claims. | ICLR 2026 | theory | [pdf](papers/arXiv-2505.15547.pdf) |
| G2 | Navuluru, …, Rossi, Tamil — *Unifying GNNs Through a Common Layer Equation*. A 7-component layer equation that separates *where* information moves (propagation bank) from *what* moves (message maps). Covers more than 200 architectures in 7 families. | arXiv 2608.16097, Aug 2026 | theory | [pdf](papers/arXiv-2608.16097.pdf) |
| G3 | Carrasco, Netto, Martirosyan, Okoyomon, Graziani — *On the Rademacher Complexity of GNNs: Unifying Expressivity and Geometry*. Data-dependent generalization bounds driven by how samples fall into WL equivalence classes; Wasserstein-Lipschitz robustness. | arXiv 2510.10101, rev. Jul 2026 | theory | [pdf](papers/arXiv-2510.10101.pdf) |
| G4 | *Unifying Approach to Uniform Expressivity of GNNs* | KR 2026 (arXiv 2602.18409) | theory | [pdf](papers/arXiv-2602.18409.pdf) |
| G5 | Schmidt, Carrasco, Röell, Wolf, Blaser, Rieck — *No Triangulation Without Representation: Generalization in Topological Deep Learning*. With the right representations both GNNs and higher-order models saturate MANTRA, but **neither generalizes beyond the combinatorial structure** (triangulation refinement). | arXiv 2605.06467, May 2026 | theory, bench | [pdf](papers/arXiv-2605.06467.pdf) |
| G6 | *Short-Range Oversquashing* | arXiv 2511.20406, 2025 | theory | [link](https://arxiv.org/abs/2511.20406) |
| G7 | *On Vanishing Gradients, Over-Smoothing, and Over-Squashing in GNNs: Bridging Recurrent and Graph Learning* | arXiv 2502.10818, 2025 | theory | [link](https://arxiv.org/abs/2502.10818) |

## Graph foundation models and relational deep learning

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| F1 | † Platonov, Bazhenov, Eremeev, Prokhorenkova — *A Fair Evaluation of Graph Foundation Models for Node Property Prediction*. Tests 9 GFMs (OpenGraph, AnyGraph, GCOPE, SAMGPT, MDGFM, TS-GNN, G2T-FM, TAG, GraphPFN) against tuned GNNs on 10 datasets. **Non-PFN GFMs always underperform tuned GNNs.** PFN-based GFMs usually win, and fine-tuned GraphPFN is best on all 10, at higher inference cost. | ICML 2026 GFM Workshop (arXiv 2606.24509) | bench, gfm | [pdf](papers/arXiv-2606.24509.pdf) |
| F2 | Eremeev et al. — *GraphPFN: A Prior-Data Fitted Graph Foundation Model*. Pretrained on millions of synthetic graphs (multi-level SBM + graph-aware SCMs). Extends the LimiX tabular PFN with message passing. State of the art in both in-context learning and fine-tuning. v1.3 and a PyPI package released mid-2026. | ICML 2026 (arXiv 2509.21489) | gfm | [pdf](papers/arXiv-2509.21489.pdf) |
| F3 | Hudovernik, López, Kocijan, Nitta, Lenssen, Leskovec, Fey — *KumoRFM-2: Scaling Foundation Models for Relational Learning*. Natively multi-table, scales to billions of rows, beats supervised and foundation baselines by up to 8%. The authors say it is the first few-shot foundation model to beat supervised models on common relational benchmarks. | arXiv 2604.12596, Apr 2026 | gfm | [pdf](papers/arXiv-2604.12596.pdf) |
| F4 | *RelBench v2: A Large-Scale Benchmark and Repository for Relational Data*. 11 datasets (adds SALT, RateBeer, arXiv, MIMIC-IV), autocomplete tasks, 70+ CTU databases via ReDeLEx, TGB and 4DBInfer integration. | ICLR 2026 DATA-FM Workshop (arXiv 2602.12606) | bench | [pdf](papers/arXiv-2602.12606.pdf) |
| F5 | *Relational Transformer: Toward Zero-Shot Foundation Models for Relational Data* | arXiv 2510.06377, 2025 | gfm | [link](https://arxiv.org/abs/2510.06377) |
| F6 | *No Need to Train Your RDB Foundation Model* / *Parameter-Free Encoders Remain Viable for RDB Foundation Models* | arXiv 2602.13697; 2607.05476, 2026 | gfm | [link](https://arxiv.org/abs/2602.13697) |
| F7 | *Context Window Failures in Relational Foundation Models* | arXiv 2609.00460, 2026 | gfm, bench | [link](https://arxiv.org/abs/2609.00460) |
| F8 | *NodeGround: A Node Classification Benchmark in the GFM Era* | arXiv 2609.39673, 2026 | bench | [link](https://arxiv.org/abs/2609.39673) |
| F9 | Kreuzer-style task-tree GFMs; *What Makes Graph Unified?* (generative sliding-window transformer GFM) | arXiv 2412.16441; 2607.27966 | gfm | [link](https://arxiv.org/abs/2607.27966) |

## Equivariance and symmetry

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| E1 | † Brehmer, Behrends, de Haan, Cohen — *Does equivariance matter at scale?* On rigid-body interactions with transformers: (1) augmentation closes the data-efficiency gap given enough epochs; (2) both scale as power laws in compute, and **equivariant models win at every compute budget tested**; (3) the compute-optimal model size versus training duration split differs between the two. | TMLR 07/2025 (arXiv 2410.23179) | algo, bench | [pdf](papers/arXiv-2410.23179.pdf) |
| E2 | Elhag, Raja, Morehead, Blau, …, Bronstein — *Learning Inter-Atomic Potentials without Explicit Equivariance (TransIP)*. A plain Transformer steered to SO(3) equivariance with a contrastive embedding objective. Matches equivariant baselines on OMol25 and is 40–60% better than augmentation. | arXiv 2510.00027, rev. Mar 2026 | algo, sci | [pdf](papers/arXiv-2510.00027.pdf) |
| E3 | Nowara et al. (Genentech) — *Do we need equivariant models for molecule generation?* Augmented non-equivariant CNNs vs equivariant GNNs. A loss decomposition separates accuracy error from equivariance error; first study of learned equivariance in generative tasks. | arXiv 2507.09753, 2025 | bench | [pdf](papers/arXiv-2507.09753.pdf) |
| E4 | Manolache, Niepert — *Equivariance Breaks the Learning Rate*. Irrep-block parameter sharing gives inconsistent effective step sizes under Adam, which explains why Muon beats Adam. Block-wise spectral or RMS normalization partly closes the gap (rMD17, MD22, QM9). | arXiv 2609.08381, Sep 2026 | algo | [pdf](papers/arXiv-2609.08381.pdf) |
| E5 | Bökman, Nordström, Kahl — *Flopping for FLOPs*. Mirror-symmetric architectures with block-diagonal layers keep FLOPs per parameter equal to standard nets, halving compute. | ICML 2025 (arXiv 2502.05169) | algo | [pdf](papers/arXiv-2502.05169.pdf) |
| E6 | *Relaxed Equivariance via Multitask Learning (REMUL)*. An equivariance loss with a tunable weight; up to 10× faster inference and 2.5× faster training than equivariant baselines. | arXiv 2410.17878, 2024–25 | algo | [link](https://arxiv.org/abs/2410.17878) |
| E7 | *LieAugmenter: Equivariant Learning by Discovering Symmetries with Learnable Augmentations* | arXiv 2506.03914, 2025 | algo | [link](https://arxiv.org/abs/2506.03914) |
| E8 | *Equivariance and Augmentation for Bayesian Neural Networks* | arXiv 2606.26273, 2026 | theory | [link](https://arxiv.org/abs/2606.26273) |
| E9 | *Data Augmentation: A Fourier Analysis Perspective* | arXiv 2606.24418, 2026 | theory | [link](https://arxiv.org/abs/2606.24418) |

## Scientific applications

| # | Paper | Venue / date | Tags | PDF |
|---|---|---|---|---|
| S1 | Liao, Hoffman, Shen, Duval, Norwood, Smidt — *EquiformerV3*. SE(3)-equivariant graph attention: 1.75× speedup, equivariant merged layer norm, smooth-cutoff attention, SwiGLU-S² activations. State of the art on OC20, OMat24, and Matbench Discovery (with DeNS). | arXiv 2604.09130, Apr 2026 | algo, sci | [pdf](papers/arXiv-2604.09130.pdf) |
| S2 | Kavanagh, …, Musaelian, Kozinsky — *Fast and Accurate Equivariant Foundation Models for Atomistic Simulation*. NequIP/Allegro foundation potentials with leading inference speed. **Dataset diversity and consistent transition-metal treatment** are the main levers for accuracy. | arXiv 2607.28461, Jul–Sep 2026 | sci | [pdf](papers/arXiv-2607.28461.pdf) |
| S3 | Li, Xue, Zhang, Zhang, Wang — *DPA4C: Universal ML Molecular Dynamics at the Speed of Empirical Potentials*. Equivariant with co-designed CUDA kernels. About 100× the throughput of MACE-OMat at similar accuracy; the Nano variant is faster than MEAM empirical potentials. Ran 2.048B atoms on 1,024 GPUs. | arXiv 2608.19041, Aug 2026 | sci | [pdf](papers/arXiv-2608.19041.pdf) |
| S4 | Wood et al. (Meta FAIR) — *UMA: A Family of Universal Models for Atoms*. eSEN backbone with a mixture of linear experts, about 500M structures. | arXiv 2506.23971, 2025 | sci, gfm | [pdf](papers/arXiv-2506.23971.pdf) |
| S5 | Bigi, Langer, Ceriotti — *The dark side of the forces: assessing non-conservative force models*. Direct-force models fail on properties that depend on derivatives and destabilize MD. | arXiv 2412.11569, 2024–25 | sci, bench | [pdf](papers/arXiv-2412.11569.pdf) |
| S6 | Li, Walsh — *Platonic representation of foundation MLIPs*. The latent spaces of 7 MLIPs (equivariant or not, conservative or not) align into a common metric space. Distortions in it flag failures such as symmetry breaking and wrong phonons. | Nat. Mach. Intell. 8, 830–840 (2026); arXiv 2512.05349 | sci, theory | [pdf](papers/arXiv-2512.05349.pdf) |
| S7 | Matbench Discovery leaderboard (as of mid-2026): EquiformerV3+DeNS-OAM F1 0.931; EquFlashV2 0.929; PET-OAM-XL 0.924; eSEN 0.925 | Leaderboard | bench | [link](https://matbench-discovery.materialsproject.org/models) |
| S8 | *UniFFBench: Evaluating Universal ML Force Fields Against Experimental Measurements* | arXiv 2508.05762, 2025 | bench | [link](https://arxiv.org/abs/2508.05762) |
| S9 | Geffner et al. (NVIDIA) — *La-Proteina: Atomistic Protein Generation via Partially Latent Flow Matching*. Explicit Cα coordinates plus per-residue latents for sequence and side chains. State-of-the-art all-atom co-designability; up to 800 residues. | ICLR 2026 (arXiv 2507.09466) | sci | [pdf](papers/arXiv-2507.09466.pdf) |
| S10 | Lin, AlQuraishi et al. — *Genie 3: Fast and Ultra-Capable Protein Design via Atomistic SE(3)-Equivariance*. Branched-polymer frames for side chains, LatentTransformer, IPA decoder. Up to 20× higher in-silico binder success on hard multimers; a nanomolar Nipah G binder came out of the Adaptyv competition. | bioRxiv, May 2026 | sci | [pdf](papers/Genie3-bioRxiv-2026.05.01.722168.pdf) |
| S11 | *Scaling Atomistic Protein Binder Design with Generative Pretraining and Test-Time Compute* | arXiv 2603.27950, 2026 | sci | [link](https://arxiv.org/abs/2603.27950) |
| S12 | ECMWF AIFS (GNN encoder/decoder with a sliding-window transformer processor, operational); GraphCast/FastNet icosahedral-mesh GNNs; WeatherNext 2 (FGN) | 2024–26 | sci | [link](https://www.ecmwf.int/en/newsletter/178/news/aifs-new-ecmwf-forecasting-system) |
| S13 | *MR-GNF: Multi-Resolution Graph Neural Forecasting on Ellipsoidal Meshes* | arXiv 2603.13563, 2026 | sci | [link](https://arxiv.org/abs/2603.13563) |
| S14 | *Crystal structure prediction using graph neural combinatorial optimization* | arXiv 2604.23921, 2026 | sci | [link](https://arxiv.org/abs/2604.23921) |
| S15 | *Periodic Topological Deep Learning for Polymer Design and Discovery* | arXiv 2605.26833, 2026 | sci | [link](https://arxiv.org/abs/2605.26833) |
