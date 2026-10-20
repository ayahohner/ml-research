# 01 · State of the Field (late 2026)

## The one-paragraph version

Geometric deep learning (GDL) is the program of building neural networks whose inductive biases come from the symmetry and structure of the domain: grids, groups, graphs, geodesics and gauges [R1, R2]. In 2026 the field has split in two. In **science** (atomistic simulation, protein design, weather) geometric models are the production workhorses: equivariant interatomic potentials top Matbench Discovery [S1, S7], run billion-atom MD [S3], and power operational forecasts at ECMWF [S12]. In **generic graph learning**, the field is in a self-critical phase. Its benchmarks are called inadequate [R7]. Its folklore about over-smoothing and over-squashing is being dismantled [G1]. Most "graph foundation models" lose to a well-tuned GNN [F1]. The exceptions are **prior-data-fitted (PFN) and relational foundation models** [F1–F3], which actually work. Cutting across both halves is the question of whether symmetry should be **hard-wired or learned**.

## Five storylines of 2025–26

### 1. "Is equivariance worth it?" has become an engineering question

The 2024–25 consensus was that augmentation plus scale might make equivariant architectures unnecessary. AlphaFold3's non-equivariant denoiser, Orb and PET potentials, and the bitter lesson all pointed that way. Controlled evidence now says something more nuanced:

- Equivariant transformers **win at every compute budget** on rigid-body dynamics. Augmentation only closes the *data-efficiency* gap, and only with enough epochs [E1].
- Non-equivariant models can *learn* symmetry well when trained for it explicitly, for example with a contrastive objective (TransIP) [E2] or relaxed multitask losses [E6]. Naive augmentation is 40–60% worse [E2].
- The real cost of equivariance is **FLOPs and optimization**, not expressivity. New work tackles both: halving FLOPs [E5], explaining why Adam misbehaves on irrep-structured weights [E4], and kernel co-design [S3].
- At the frontier, equivariant models are still state of the art: EquiformerV3, NequIP/Allegro foundation models, and DPA4C for potentials [S1–S3], and Genie 3 for proteins [S10].

The emerging stance is **"symmetry as a training goal, not necessarily an architectural constraint"**. Whether to hard-wire it is a compute and throughput trade-off, decided per domain.

### 2. Foundation MLIPs became the flagship application

Universal machine-learned interatomic potentials (UMA, MACE-MP/OMat, eSEN, EquiformerV3, PET-OAM, Orb, DPA) are where GDL meets scale. In 2026 the field asked itself what these models really are [R9]. Is there a minimal definition? Is the bottleneck data or models? Can they handle long-range physics, discover new physics, or be validated at all? Representation analysis shows that different MLIP families converge to a shared "Platonic" latent geometry [S6], and that shared space can be used to diagnose failures.

### 3. Graph foundation models: mostly hype, except PFNs and relational models

A fair comparison of nine GFMs on node property prediction found that **non-PFN GFMs always underperform well-tuned classic GNNs** [F1]. PFN-based approaches (GraphPFN, G2T-FM, TAG) borrow from tabular foundation models (TabPFN, LimiX). They usually win, and fine-tuned GraphPFN is best on every dataset tested [F1, F2]. In relational deep learning over multi-table databases, KumoRFM-2 reports few-shot performance above supervised models [F3], and RelBench v2 scales up the evaluation [F4]. The lesson is that synthetic-prior pretraining and the tabular view of graphs worked, while "an LLM-style GNN pretrained on lots of graphs" mostly did not.

### 4. The graph benchmark reckoning

A position paper co-signed by many of the field's leading groups argues graph learning **"will lose relevance due to poor benchmarks"** [R7]. Its complaints are an over-focus on small molecules and citation graphs, fragmented protocols and leaderboard overfitting. The same correction is visible elsewhere:

- universal claims about over-smoothing, over-squashing and homophily are refuted with counterexamples [G1]
- topological deep learning's flagship benchmark is saturated by plain GNNs with the right input representation, and neither model family generalizes structurally [G5]
- GFMs are re-evaluated against tuned baselines [F1]

### 5. Unification of propagation theory across GNNs and Transformers

Over-smoothing and over-squashing are now understood as instances of **rank collapse and representational collapse**, which also afflict decoder-only Transformers [R3]. Self-attention is a learned, fully connected adjacency. The theory is consolidating:

- a single layer equation that covers more than 200 GNNs [G2]
- generalization bounds that tie expressivity (WL classes) to geometry [G3]
- unified accounts of uniform expressivity [G4]
- links between graph propagation and recurrent vanishing gradients [G7]

The last link connects naturally to the reservoir-computing notes in [`../reservoir-computing/`](../reservoir-computing/).

## What GDL is *for* in 2026, ranked by maturity

| Area | Maturity | Representative 2026 evidence |
|---|---|---|
| Interatomic potentials / materials | Production; foundation-model era | EquiformerV3 F1 ≈ 0.93 on Matbench Discovery [S1, S7]; DPA4C 2B-atom MD [S3] |
| Weather and climate | Operational | ECMWF AIFS (GNN encoder/decoder), GraphCast lineage [S12] |
| Protein structure and design | Production-adjacent; wet-lab validated | La-Proteina [S9], Genie 3 binders [S10] |
| Relational / enterprise data | Commercializing | KumoRFM-2 [F3], RelBench v2 [F4] |
| Node/graph prediction on generic graphs | Mature tooling, contested progress | Tuned GNNs ≈ or > most GFMs [F1] |
| Combinatorial optimization, chip design | Promising, under-benchmarked | Called out as neglected [R7]; crystal structure prediction [S14] |
| Topological deep learning | Research-stage | Generalization questioned [G5]; polymer applications [S15] |

## Is there a meta-analysis?

There is **no formal statistical meta-analysis** of GDL, as there was none for RC. The closest substitutes are:

- large controlled studies such as equivariance at scale [E1] and the fair GFM evaluation [F1]
- living leaderboards (Matbench Discovery [S7], RelBench [F4], OC20/OMat)
- position papers that aggregate community evidence [R7, R9]
- comprehensive surveys [R3, R5, R6]

[05-benchmarks-and-evidence.md](05-benchmarks-and-evidence.md) puts together the quantitative evidence that does exist.
