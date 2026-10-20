# Benchmarks and Evidence: A Cross-Study Synthesis

IDs refer to [bibliography.md](bibliography.md).

## Is there a meta-analysis?

**No.** As of October 2026 there is no formal quantitative meta-analysis of reservoir computing performance: no pooled effect sizes and no systematic review following PRISMA. Searches return only:
- the **benchmark tutorial review and critique** by Wringe, Trefzer & Stepney [R3], the closest thing to a systematic methodological review;
- **narrative and systematic reviews by platform** (photonic [R1], memristive [R6, R7], quantum [R2], edge-AI [R5]);
- scattered **head-to-head comparisons**.

The main reason a meta-analysis cannot yet be done is the one [R3] documents: studies use different dataset variants, parameters, splits, metrics, and reporting, so results cannot be pooled. Below is a structured cross-study synthesis that is as quantitative as the literature allows.

---

## What the benchmark critique found [R3]

Wringe et al. (IJPEDS 2025) sort RC benchmarks into a taxonomy and review dozens of them. Examples are NARMA, Mackey–Glass, Santa Fe laser, sunspots, IPIX radar, memory capacity, IPC, and the chaotic-systems catalogues. Recurring problems:
- **The same benchmark name can mean different data.** There are several sunspot datasets, Santa Fe laser data is used in different subsets, and the IPIX radar has several recordings.
- **Parameters change the task.** Mackey–Glass becomes chaotic only for τ ≥ 16.8, and the literature uses several τ values. NARMA order and coefficients vary.
- **Generated data depends on the integrator.** The timestep and solver change the dataset, citing Gilpin's catalogue of 131 chaotic systems as a good practice.
- **Reservoir configurations are under-reported**, so results cannot be reproduced.

**Their reporting checklist** (condensed):
- State the data source, the exact subset, the generation parameters and why they were chosen, and the integrator settings.
- Publish new datasets with datasheet-style metadata.
- Report node count, input bias, leak rate, input noise, output feedback, connectivity, spectral radius, input scaling, washout, readout and regularization, and the number of independent runs.
- Use statistical tests for comparisons.

The QRC survey [R2] proposes an even stricter **minimum reporting protocol** that includes the full search budget, failed runs, and resource accounting. It applies equally well to classical RC.

---

## Cross-study evidence table (2025–2026)

These numbers come from different papers with different protocols, so treat them as indicative only.

| Study | Task | RC variant | Best competitor | Outcome |
|---|---|---|---|---|
| ParalESN [A1], ICML 2026 | sMNIST | ParalESN-deep **97.2%**, 3.3 min, 0.05 kWh | S4 99.2%; LRU 98.5% (29 min, 0.57 kWh); Transformer 98.4% (141 min, 1.81 kWh); LSTM 97.5% (81 min) | RC is about 1–2 points behind, with about 10–40× less energy |
| ParalESN [A1] | psMNIST | ParalESN **96.9%** | S4 97.9%; LRU 97.8%; Transformer 97.4%; Mamba 92.6%; LSTM 92.8% | RC beats LSTM and Mamba, and is about 1 point behind S4 |
| ParalESN [A1] | UCR classification (Blink, FordA, …) | ParalESN-deep 76.8–96.5% | Standard ESN 62.7–92.1% | Large gains over classical ESN |
| FRESCO [A2] | Memory, sequential classification, long-horizon multivariate forecasting | O(N) frequency-domain ESN | Deep sequence models | Similar accuracy at up to about 1000× less energy |
| Häußer [B1] | M4 monthly and quarterly | Autoregressive ESN | ES-RNN (M4 winner), ARIMA, ETS, Theta, TBATS, MLP, RNN | Ties ARIMA/TBATS (monthly MASE), 2nd (quarterly); **ES-RNN best** |
| Echo Flow Networks [A4] (preprint) | ETTh/ETTm/Weather/Air-Quality/DMV | EFN / EchoFormer | PatchTST | Claims state of the art: error 43%→35% (about 20% relative), 4× faster training, 3× smaller model |
| Adaptive NVAR [A5] | Noisy chaotic series | NVAR + MLP features | NVAR, leaky ESN, hybrid ESN | Adaptive NVAR best, especially under noise |
| Hurley & Shaheen [T7] | Noiseless Lorenz-63 | Tuned ESN | Solver-limited ground truth | VPT above 30 Lyapunov times (about 70% of a single-step-error benchmark) |
| KARC [A3] | PDE forecasting | KAN-basis RC | Prior RC methods | Beats prior RC |
| Comparative study (2022) [B5] | Lorenz and other chaotic systems | ESN, NVAR | LSTM, GRU | ESN accurate for 400+ steps vs about 50 for LSTM/GRU; RC/NVAR more efficient |
| Context parroting [B2], ICLR 2026 | Chaotic attractors, turbulence, oscillators | *(no RC)* | Time-series foundation models | Copying the context beats foundation models, so **foundation models are not yet a reliable baseline** for dynamical systems |
| Ensemble RC [A7] | Error detection on STO hardware | ERC | Conventional STO-RC | 99% vs chance |
| Chaos-controlled bio-RC [H2] | Classification and forecasting on neuron cultures | cc-RC | Standard bio-RC | About 300% better accuracy and longevity |

## What can be concluded

**Consistent findings across independent groups (moderate to high confidence):**
1. **RC and NVAR are very efficient for learning low-dimensional chaotic dynamics from little data.** Several groups over several years agree, and both a 2022 comparison and 2025 VPT work support it. This is RC's most robust advantage.
2. **On general sequence benchmarks, modern RC gets close to trained models but does not beat them**: about 1–3 points behind S4/LRU/Transformers at 1–3 orders of magnitude lower training cost [A1, A2].
3. **Classical dense ESNs are clearly outperformed by parallel and deep reservoir variants** [A1].
4. **On standard statistical forecasting (M4), ESNs are competent mid-pack performers**, not leaders [B1].

**Claims that need replication (low confidence):**
- ESN-derived models achieving state of the art on long-horizon multivariate benchmarks vs PatchTST [A4]. These are single-group preprints, and the ETT benchmarks are known to be noisy and leakage-prone.
- Energy figures of "up to 1000×" [A2], which depend heavily on hardware, implementation, and what is counted.
- Every quantum-advantage claim [R2].
- Most hardware-RC accuracy claims, which are rarely compared against a matched-size software ESN.

**Systematic biases to keep in mind:**
- **Publication bias.** Almost every paper introducing a new reservoir variant reports beating the "standard ESN," but tuning effort is rarely matched. [R2] explicitly asks for the full search budget and failed runs to be reported.
- **Weak baselines.** Few RC papers compare against modern SSMs or tuned deep models. ParalESN [A1] is a notable exception.
- **Metric inconsistency.** NRMSE, MSE, VPT, MASE, sMAPE, and accuracy are used with different normalizations and horizons.
- **The ground-truth horizon problem.** Very long VPT claims can exceed the integrator's own reliability [T7].

## Recommended evaluation protocol (synthesized from R2, R3, T7, B2)

1. Use canonical, versioned datasets, e.g. Gilpin's `dysts` chaotic-systems benchmark for dynamics, UCR/UEA for classification, M4/Monash for forecasting. State exact subsets and generation parameters.
2. Baselines: tuned ESN, NGRC (SVD solve), persistence or context parroting, and at least one modern trained model (LRU/S4/Mamba or PatchTST).
3. Give every model the **same tuning budget**, and report it.
4. Use at least 10 seeds and report mean ± dispersion and a significance test.
5. For chaotic forecasting, report VPT in Lyapunov times *and* the valid ground-truth time [T7].
6. For hardware, also report energy per inference, latency, and a matched-size software ESN result.
