# 04 · Applications

## 1. Atomistic simulation: machine-learned interatomic potentials (MLIPs)

**Where things stand (2026).** Universal "foundation" MLIPs are pretrained on tens to hundreds of millions of DFT structures (OMat24, OMol25, MPtrj, Alexandria, OC20/22). They are then used zero-shot or fine-tuned for MD, relaxations and property prediction.

| Model | Symmetry | Notable 2026 claim |
|---|---|---|
| EquiformerV3 [S1] | SE(3)-equivariant attention | State of the art on OC20, OMat24, Matbench Discovery (F1 ≈ 0.931 with DeNS) |
| NequIP/Allegro FMs [S2] | E(3)-equivariant | Fastest equivariant inference; diversity and consistent TM treatment matter most |
| DPA4C [S3] | Equivariant + CUDA co-design | About 100× MACE-OMat throughput; 2.048B atoms on 1,024 GPUs at 83–91% weak scaling; Nano variant beats MEAM empirical potentials |
| UMA [S4] | Equivariant (eSEN) + mixture of linear experts | One model across molecules, materials and catalysts (~500M structures) |
| PET-OAM, Orb | Not equivariant | Competitive (PET-OAM-XL F1 0.924); symmetry learned or imposed after the fact |

**Conservative vs direct forces.** Predicting forces directly instead of as −∇E is faster but breaks energy conservation. "The dark side of the forces" [S5] shows that this degrades MD stability and properties that depend on derivatives (phonons, thermal conductivity). Most 2026 leaders are conservative, or offer a conservative fine-tuning head.

**Six open questions** [R9] (Creed et al., Jun 2026):

1. What is the minimal definition of an atomistic foundation model? Is broad element coverage enough, or is transferability across properties needed?
2. Is the bottleneck more data, better data (consistent DFT levels), or better models?
3. Can MLIPs handle long-range electrostatics and dispersion, and does it matter in practice?
4. Can MLIPs discover genuinely new physics, or only interpolate?
5. Can they scale to useful simulations (time and length scales, throughput)?
6. How do we know they are any good, given that leaderboards (Matbench Discovery) do not equal experimental agreement [S8]?

**Representation diagnostics** [S6]. Latent spaces of 7 MLIPs align into a shared "Platonic" geometry. Distortions in it flag symmetry breaking and phonon errors, which gives an architecture-agnostic way to audit models.

## 2. Protein structure and design

- **La-Proteina** [S9] (ICLR 2026) uses partially latent flow matching. Backbone Cα coordinates are explicit, and sequence and side-chain atoms sit in per-residue VAE latents. It achieves state-of-the-art all-atom co-designability and atomistic motif scaffolding, and scales to 800 residues.
- **Genie 3** [S10] (May 2026) is all-atom and SE(3)-equivariant. It represents side chains as branched-polymer frames and pairs a LatentTransformer with an IPA decoder. In silico it reports up to 20× higher binder success on hard multimeric targets. In the Adaptyv Nipah competition it reached 12.5% experimental success and found a nanomolar binder. This is a strong data point that **equivariance remains state of the art in protein generation**.
- **Context.** AlphaFold3's diffusion module is *not* equivariant (augmentation only). Test-time compute and generative pretraining are scaling binder design [S11]. Evaluation standards for protein generative models are themselves under review [R11].

## 3. Weather and climate

- **Operational**: ECMWF's AIFS uses a GNN encoder/decoder between the N320 (~0.25°) grid and a latent mesh, with a sliding-window transformer processor. It runs alongside the physics-based IFS [S12].
- **The GraphCast lineage**: 16-layer message-passing GNNs on multi-scale refined icosahedral meshes (GraphCast, FastNet). Ensemble generative variants include GenCast and WeatherNext 2/FGN, which is reported as 10–20% better than GenCast and 8× faster.
- **Geometry-aware meshes**: MR-GNF uses ellipsoidal multi-resolution meshes [S13].
- **Foundation models**: Aurora is a transformer-based weather and earth-system foundation model.

## 4. Relational and enterprise data

Relational deep learning turns a database into a temporal heterogeneous graph. KumoRFM-2 [F3] does few-shot prediction across schemas at billion-row scale. RelBench v2 [F4] supplies 11 datasets, autocomplete tasks and more than 70 extra databases. This is the clearest *commercial* GDL application outside science, and it is where the benchmark-crisis paper [R7] says graph learning should be heading.

## 5. Combinatorial optimization, chips and crystals

The position paper [R7] names combinatorial optimization and chip design as high-value, under-benchmarked applications. Recent examples include crystal structure prediction via graph neural combinatorial optimization [S14]. Evidence here is still scattered across task-specific setups, and no shared benchmark has emerged.

## 6. Knowledge graphs, recommendation and others

Knowledge-graph reasoning with GNNs [R12], recommender systems, fraud detection and traffic forecasting remain large industrial users of GNNs. They are mostly mature engineering rather than a research frontier, and they are covered here only at survey level.
