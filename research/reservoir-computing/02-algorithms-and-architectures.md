# Algorithms and Architectures

IDs refer to [bibliography.md](bibliography.md).

## The baseline recipe

A classical **echo state network (ESN)** has three parts:
- a fixed random input matrix,
- a fixed random recurrent matrix scaled to a spectral radius ρ, usually with a leak rate α,
- a linear readout trained by ridge regression.

Its strengths are training in seconds, no backprop through time, and a closed-form solution. Its weaknesses are O(N²) sequential state updates, sensitivity to hyperparameters, and limited expressivity on long-range dependencies.

**NGRC / NVAR** [A8] removes the reservoir completely. Features are polynomial monomials of k time-delayed inputs, followed by a linear readout. It needs fewer hyperparameters and much less data and warm-up, and it is interpretable.

2025–2026 work branches out from these two baselines in four directions.

---

## 1. Parallelizable reservoirs: convergence with SSMs

| Model | Key idea | Reported result |
|---|---|---|
| **ParalESN** [A1], ICML 2026 | Diagonal *linear* recurrence in the complex domain. Any linear reservoir can be diagonalized, so nothing is lost. The scan parallelizes across time. Keeps the echo state property and universality. | sMNIST 96.2% (deep: 97.2%) in about 3 min and 0.04–0.05 kWh. LSTM: 97.5% in 81 min, 1.0 kWh. Transformer: 98.4% in 141 min, 1.8 kWh. LRU: 98.5%, 29 min, 0.57 kWh. Standard ESN: 82.5%. psMNIST 96.9% vs Transformer 97.4% and Mamba 92.6%. |
| **FRESCO** [A2] | Runs the whole reservoir in the frequency domain using circulant (circular-convolution) recurrence, which gives O(N) dense nonlinear updates. Nonlinearity is applied natively in frequency space. | No statistically significant accuracy loss vs dense ESN on classification. Matches deep models on long-horizon multivariate forecasting with up to about 1000× less energy. |
| **RSSM** [A9] | Structured convolutional SSM dynamics as a fixed, untrained reservoir. Only a feed-forward readout is trained. | Targets long-range dependencies (OpenReview paper). |
| **Linear RNN reservoirs for brain digital twins** [A10] | Noisy linear RNN within RC, with theory, applied to fMRI BOLD forecasting. | Predicts BOLD activity through low-dimensional spatiotemporal modes. |

**Synthesis.** The pattern copies the SSM insight: make the recurrence **linear and diagonal (or circulant)**, so it can be computed with a parallel scan or FFT, and put the nonlinearity in the readout or in stacked layers. RC's distinctive feature is that the recurrence is never trained. Once parallelized, RC becomes "an SSM with frozen dynamics." It keeps about 95–98% of the accuracy of a trained SSM at a few percent of the cost. Deep or stacked variants consistently close part of the gap.

## 2. Structured feature libraries: NGRC and its descendants

| Model | Fixes | Notes |
|---|---|---|
| NGRC numerical analysis [T6] | Ill-conditioned feature matrices with short lags, high degree, or short data | **Use an SVD solve.** It stays accurate without ridge regularization, unlike Cholesky or LU. |
| Adaptive NVAR [A5] | Fixed features break under noise | Keeps the linear delay terms and replaces the polynomial terms with a small trainable MLP trained jointly with the readout. Beats NVAR, leaky ESN, and hybrid ESN on noisy chaotic series. |
| KARC [A3] | Limited representational capacity and long-range dependencies | Kolmogorov–Arnold basis expansions replace the reservoir and keep closed-form training. State of the art among RC methods on PDE benchmarks. Also used as a component in diffusion models. |
| Quantum NGRC | — | NGRC mapped onto quantum-optical hardware (PRA 2025). |

**Synthesis.** "Reservoir" increasingly means **a fixed, cheap, high-dimensional feature map with a closed-form readout**, whether or not it is recurrent. The open tension is that learned features (Adaptive NVAR) improve robustness but give up RC's no-backprop advantage.

## 3. Richer nonlinearity in ESN-style models

- **Echo Flow Networks / EchoFormer** [A4]: matrix-gated composite random activations give each neuron its own dynamics. A dual-stream design lets recent input select features from infinite-horizon reservoir memory. It claims state of the art on ETTh/ETTm/Weather/Air-Quality/DMV vs PatchTST, with 4× faster training and 3× smaller models. *This is a preprint still under review. The comparisons need independent replication.*
- **Untrained readouts** [T1]: theory-guided readout networks that beat earlier trained ESN models *without training*.
- **Deterministic reservoirs**: e.g. Lobachevsky-function activations (Sci. Rep. 2025) report large gains over cycle reservoirs and classical ESNs on chaotic series.
- **Heterogeneous neurons** [T3]: mixing neuron types removes the stability/reach trade-off that appears as reservoirs grow.

## 4. Robustness for physical substrates (algorithm side)

- **Generalized RC** [A6]: drops the requirement that the reservoir respond identically to identical inputs. This makes non-reproducible materials, and even spatiotemporal chaos, usable.
- **Ensemble RC** [A7]: averages states over spatially multiplexed copies. It provably removes temporal noise under stated conditions and also exposes capacity that standard RC misses. Spin-torque-oscillator demo: 99% vs chance.
- **ROME encoding** [T5]: analytically optimal input directions from measured fluctuation and response. Equivalent to backprop-trained encoders and usable on non-differentiable hardware.
- **Programmed readouts** [H1]: maps a target function to readout weights analytically with no training data, which is the start of "RC as programmable analog computing."

## Practical recommendations

1. **Baselines to always include:** a tuned leaky ESN; NGRC with an SVD solve; a persistence or context-parroting baseline [B2]; and a modern SSM (LRU/S4/Mamba) if compute allows.
2. **Hyperparameters that matter most for ESNs:** spectral radius, leak rate, input scaling, and ridge λ. Results on M4 [B1] show the optimum depends on data frequency: monthly data favors persistent reservoirs with high leakage, quarterly favors more contractive dynamics. Large valid prediction time on Lorenz appears in two ρ regimes, near 0 and near the edge of chaos [T7].
3. **Large reservoirs:** use ParalESN-style diagonal recurrence or FRESCO-style circulant recurrence instead of dense O(N²) updates.
4. **Tooling:** `reservoirpy` (Python), `ReservoirComputing.jl` (Julia), and the `echos` R package [B4] for automatic ESN forecasting.
