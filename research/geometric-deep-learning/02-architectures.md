# 02 · Architectures

## 1. The blueprint

The GDL "5G" blueprint [R1, R2] builds networks from:

1. **Equivariant layers**: linear maps that commute with the domain's symmetry group, followed by pointwise nonlinearities.
2. **Local pooling / coarsening**: scale separation.
3. **An invariant global readout**: for predictions that must not depend on the group action.

CNNs (translations on grids), GNNs (permutations on graphs), spherical CNNs (rotations), mesh and gauge CNNs, and Transformers (permutations on sets) are all instances of this blueprint. Sáez de Ocáriz Borde & Bronstein [R2] collect the required mathematics: groups and representations, differential geometry and fiber bundles, spectral graph theory, and algebraic topology.

## 2. Message-passing GNNs and the common layer equation

Navuluru et al. [G2] reduce more than 200 GNN architectures to one layer equation with seven components. Its key split is between:

- **the propagation bank**: *where* information moves (adjacency powers, diffusion, rewired graphs, attention scores, positional encodings)
- **the message maps**: *what* moves (linear, MLP, gated, edge-conditioned)

Many apparently distinct models differ in only one or two components. The paper uses the framework to locate where over-smoothing, over-squashing and heterophily problems enter, and suggests more papers should report results as ablations of these components.

**Rewiring** (adding or removing edges to improve curvature, effective resistance or spectral gap) is the main architectural answer to over-squashing [R6]. Virtual nodes and graph transformers are the extreme cases.

## 3. Graph Transformers

Graph Transformers [R4] add global attention to message passing (GPS-style hybrids) or replace it with attention plus structural and positional encodings (Laplacian eigenvectors, random-walk encodings, shortest-path biases). The 2026 survey [R3] treats attention as a **learned dense adjacency**, so Transformer rank collapse and GNN over-smoothing are the same phenomenon. Practically, graph transformers dominate long-range and molecular tasks. Sparse or local attention (sliding-window processors, as in ECMWF AIFS [S12]) is common at scale.

## 4. Geometric (3D) GNNs and equivariant networks

These are used for point clouds with E(3)/SE(3) symmetry: molecules, materials and proteins.

| Family | Mechanism | 2026 exemplars |
|---|---|---|
| Spherical-tensor / irrep networks | Features carry SO(3) irreps; Clebsch–Gordan tensor products | NequIP/Allegro foundation models [S2], MACE |
| Equivariant attention | eSCN-style SO(2) convolutions plus attention over irreps | EquiformerV3 [S1], eSEN/UMA [S4] |
| Kernel-co-designed equivariant | Custom CUDA; reduced tensor-product cost | DPA4C [S3] (about 100× MACE-OMat throughput) |
| Frame / local-frame methods | Canonicalize to local frames, then use any network | Genie 3 branched-polymer frames [S10] |
| Unconstrained + learned symmetry | Plain Transformer; augmentation or equivariance loss | TransIP [E2], Orb, PET, REMUL [E6] |

**EquiformerV3** [S1] is a typical 2026 recipe. It improves efficiency (1.75× speedup), adds an equivariant merged layer norm, uses smooth-cutoff attention so the potential energy surface stays smooth (important for MD and Hessians), and swaps activations for SwiGLU-S². With DeNS denoising pretraining it is state of the art on OC20, OMat24 and Matbench Discovery.

**Efficiency work on equivariance:**

- *Flopping for FLOPs* [E5]: mirror-symmetric features split into even and odd irreps, which makes layers block-diagonal and halves FLOPs at the same parameter count.
- *Equivariance Breaks the Learning Rate* [E4]: in equivariant layers each irrep block shares parameters across its 2ℓ+1 components, so Adam's per-parameter step sizes become inconsistent across blocks. Block-wise spectral or RMS normalization fixes much of this. This also explains why Muon (orthogonalized updates) does well on equivariant nets.

## 5. Graph foundation models (GFMs)

The survey taxonomy [R5] splits GFMs along three axes. Backbones are GNN, LLM, or GNN+LLM hybrids. Pretraining is contrastive, generative or synthetic-prior. Adaptation is fine-tuning, prompting or in-context learning. The design families are:

- **Graph-pretrained GNNs/Transformers** such as OpenGraph, AnyGraph, GCOPE, SAMGPT and MDGFM. They aim for transfer across graphs with different feature spaces. A fair evaluation finds they **underperform tuned GNNs** [F1].
- **PFN-based GFMs** such as GraphPFN [F2], G2T-FM and TAG. They come from TabPFN and LimiX and are pretrained on *synthetic* priors.
  - GraphPFN's prior combines multi-level stochastic block models with graph-aware structural causal models for node features and targets.
  - It adds attention-based neighborhood aggregation to the LimiX tabular backbone and supports pure in-context learning or fine-tuning.
  - Fine-tuned GraphPFN is the best model on all 10 datasets in the fair evaluation [F1].
- **LLM-on-graphs**: graphs serialized to text, or graph tokens fed to an LLM. Known failure modes are context-window limits, structural hallucination and permutation sensitivity. Useful mainly for text-attributed graphs.

## 6. Relational deep learning

Relational deep learning treats a relational database as a heterogeneous temporal graph: rows are nodes, and foreign keys are edges.

- **KumoRFM-2** [F3]: a native relational foundation model with in-context learning and fine-tuning. It scales to billions of rows and is up to 8% better than supervised or foundation baselines.
- **Relational Transformer** [F5]: aims for zero-shot transfer across schemas.
- **Training-free encoders** [F6]: the papers argue parameter-free encoders plus a tabular FM are competitive.
- **Known failure modes**: context-window failures [F7].

The benchmark is **RelBench v2** [F4].

## 7. Topological deep learning (TDL)

TDL generalizes message passing to simplicial complexes, cell complexes, hypergraphs and combinatorial complexes, so that higher-order relations become first-class objects [R10]. Tooling exists (TopoX / TopoBench), and applications are emerging, such as periodic TDL for polymers [S15]. However, Schmidt et al. [G5] show that on the MANTRA benchmark of triangulated manifolds, ordinary GNNs with the right representation match higher-order message passing. **Neither** generalizes to refined triangulations of the same manifold. TDL's claimed advantage therefore needs better evidence.

## 8. Domain architectures

- **Weather** [S12, S13]: encode–process–decode on multi-scale meshes. GraphCast and FastNet use 16-layer GNNs on refined icosahedral meshes. ECMWF AIFS uses a GNN encoder/decoder with a sliding-window transformer processor. MR-GNF uses ellipsoidal multi-resolution meshes. Ensemble variants (GenCast, FGN/WeatherNext 2) add generative noise.
- **Proteins** [S9–S11]: flow matching or diffusion over residue frames (SE(3)), sometimes with latent side chains.
  - La-Proteina uses explicit Cα plus per-residue latents.
  - Genie 3 is all-atom SE(3)-equivariant, using branched-polymer frames.
  - AlphaFold3's non-equivariant denoiser shows the alternative also works.
