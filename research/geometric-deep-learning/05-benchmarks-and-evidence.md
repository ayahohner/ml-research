# 05 · Benchmarks and Evidence

## Is there a meta-analysis?

**No formal (statistical, pooled-effect-size) meta-analysis of geometric deep learning exists as of October 2026.** The evidence base consists of:

1. **large controlled comparisons** that function as mini meta-analyses [E1, E3, F1, G5]
2. **living leaderboards** [S7, F4, OC20/OMat]
3. **position papers and surveys** that aggregate community evidence [R3, R5, R7, R9]

This document collects the quantitative findings.

## 1. Equivariance vs. learned symmetry

| Study | Setting | Finding |
|---|---|---|
| Brehmer et al. [E1] | Rigid-body interactions; equivariant vs standard transformers; compute sweeps | Augmentation closes the *data-efficiency* gap given enough epochs. Both follow power laws in compute, and **equivariant wins at every compute budget tested**. The compute-optimal split differs. |
| TransIP [E2] | Molecular potentials, OMol25 | A plain Transformer with a contrastive equivariance objective matches equivariant baselines and is **40–60% better than augmentation alone** |
| Nowara et al. [E3] | 3D molecule generation | Augmented non-equivariant CNNs can approach equivariant GNNs. Loss decomposition separates fit error from equivariance error. |
| REMUL [E6] | Several | Relaxed equivariance reaches comparable accuracy with up to 10× faster inference and 2.5× faster training |
| Matbench Discovery [S7] | Materials stability | Top equivariant models (EquiformerV3+DeNS 0.931, EquFlashV2 0.929) narrowly beat the top non-equivariant model (PET-OAM-XL 0.924) |
| Genie 3 [S10] | Protein binder design | The equivariant model leads in silico and has wet-lab hits |

**Synthesis.** Hard-wired equivariance gives a consistent but often **modest** accuracy edge at a fixed compute budget, plus large data-efficiency gains in small-data regimes. Learned symmetry with an explicit objective (not just augmentation) closes most of the gap. The deciding factor in practice is throughput, which is why FLOP and optimizer work matters [E4, E5, S3].

## 2. Graph foundation models vs tuned GNNs

Fair evaluation, node property prediction, 10 datasets [F1]:

| Group | Models | Result |
|---|---|---|
| Non-PFN GFMs | OpenGraph, AnyGraph, GCOPE, SAMGPT, MDGFM, TS-GNN | **Always underperform well-tuned GNNs**, often by a wide margin |
| PFN-based GFMs | G2T-FM, TAG, GraphPFN | Usually best; classic GNNs make the top 3 on only 2 of 10 datasets |
| Fine-tuned GraphPFN | — | **Best on all 10 datasets**; costs more at inference |

The authors attribute earlier positive GFM results to weak, untuned baselines and inconsistent protocols. This matches the diagnosis in [R7]. New benchmarks (NodeGround [F8], RelBench v2 [F4]) aim to stop this recurring.

## 3. The benchmark-crisis diagnosis [R7]

The position paper's claims, with the 2026 evidence for each:

| Claim | 2026 evidence |
|---|---|
| Benchmarks over-represent 2D molecular and citation graphs | GFM evaluation is still dominated by such graphs [F1, F8] |
| Representation choices drive results more than architectures | TDL: the right representation lets GNNs saturate MANTRA [G5] |
| Fragmented protocols and untuned baselines inflate gains | GFM reversal once baselines are tuned [F1] |
| Folklore substitutes for evidence | Formal counterexamples to common beliefs [G1] |
| High-value domains are under-served | RelBench v2 [F4] is the main fix so far; CO and chip design still lack shared benchmarks |

## 4. Topological deep learning

On MANTRA (triangulated 2- and 3-manifolds, predicting orientability, Betti numbers and homeomorphism type), results depend mostly on **representation**, not on whether message passing is higher-order. All models fail to generalize to barycentric subdivisions of the same manifolds [G5]. There is currently no clean empirical evidence that TDL generalizes better than graph models.

## 5. MLIP evaluation

- **Matbench Discovery** [S7] measures crystal-stability classification (F1), energy MAE and thermal conductivity (κ_SRME). The top cluster sits at F1 ≈ 0.92–0.93 and has saturated, so attention is moving to κ and MD-based metrics.
- **Agreement with experiment** [S8] (UniFFBench): good leaderboard scores do not guarantee agreement with measured properties.
- **Conservative vs non-conservative** [S5]: direct-force models are fine for static tasks and worse for dynamic or thermal ones.
- **Throughput** is now a headline metric [S2, S3], because the useful output of an MLIP is simulated nanoseconds.
- [R9]'s Q6 ("how do we know if our MLIPs are any good?") is unresolved. There is no community-agreed suite connecting benchmarks to downstream scientific usefulness.

## 6. Caveats when reading GDL results

1. **Baseline tuning.** Compare against tuned GNNs, GBDTs or TabPFN [F1].
2. **Compute-matched comparisons.** Equivariant and unconstrained models scale differently [E1]. Compare at equal FLOPs and wall clock, not equal parameters.
3. **In-distribution vs structural generalization** [G5].
4. **Leaderboard saturation** (Matbench Discovery F1, QM9, ZINC).
5. **Folklore claims** about over-smoothing or heterophily [G1]. Look for the stated conditions.
6. **Preprints.** Several 2026 results [E4, S2, S3, F3, G2] are preprints at the time of writing.
