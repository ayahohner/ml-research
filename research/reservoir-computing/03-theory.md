# Theory: What We Now Understand (2025–2026)

IDs refer to [bibliography.md](bibliography.md).

Older RC theory (roughly 2001–2020) established **universality** (ESNs and many dissipative systems can approximate fading-memory filters), the **echo state property**, **memory capacity** (Jaeger's linear MC ≤ N), and **information processing capacity (IPC)** (Dambre et al.). The 2025–26 work goes further. It explains *performance* mechanistically and identifies *limits*.

## 1. Predicting performance before training

**Perceptron theory → ESN performance** [T1]. Kleyko, Sommer et al. show that recent perceptron and capacity theory accurately predicts memory capacity and recall accuracy for **30 ESN variants**, covering different neuron types, recurrent-matrix families, and readout designs. Consequences:
- Hyperparameters can be optimized analytically across the full parameter space instead of by grid search.
- An **untrained readout** designed from the theory outperforms earlier trained ESN models.
- Trained ESN readouts settle into a **regular simplex geometry**, the same neural-collapse structure seen in deep nets. This suggests a shared organizing principle.

## 2. Why reservoirs fail: stability vs reach

**Qian & Fiete, PRE 2025** [T3] use dynamical mean-field theory on reservoirs that generate target patterns autonomously:
- **Stability-limited failure**: the target output is not a stable attractor of the closed-loop system. This failure does not depend on the training algorithm.
- **Reach-limited failure**: the training algorithm cannot drive the system close enough to the target. This failure depends on the algorithm.
- Scaling bounds on achievable output amplitude and period follow.
- **Making the reservoir bigger is not free.** It trades stability against reach depending on the regime.
- **Neuronal diversity** (several distinct neuron types) removes the trade-off. This links to biological heterogeneity.

## 3. Where computation lives in state space

**Abdalla & Rontani 2026** [T2] break IPC down by polynomial degree *and* by state-space eigenmode:
- Aggregate metrics (total IPC, MC) hide how task-relevant information is laid out geometrically.
- **A significant share of capacity can live in low-variance (low-energy) modes.** These are exactly the modes that measurement or experimental noise destroys first.
- Implication for hardware: two reservoirs with equal total IPC can behave very differently under noise. Good reservoirs need dimensionality expansion *and* a favorable geometric layout of task information.

## 4. Optimal input encoding

**ROME** [T5] (Cui, Nakajima, Aihara 2026): optimal input encoding under a power constraint is a geometric problem determined by the system's **fluctuation-response structure**. The optimal input directions follow from steady-state fluctuations plus linear response, both measurable on real hardware. Backprop-optimized encoders converge to the same solution, which shows a trade-off between task-dependent feature mixing and intrinsic noise. Validated on spin-wave waveguides and spiking networks.

## 5. Fundamental limits of noisy physical reservoirs

**Polloreno, PR Applied 2025** [T4]: in a noisy analog reservoir, the accessible volume of configurations shrinks **exponentially** (a quantum-complexity-style argument). Through fat-shattering dimension, such reservoirs can learn only **polynomially many** functions, *even with exponential post-processing*. Exponentially large state spaces (in photonic or quantum hardware) do not automatically yield exponentially large computational power.

This agrees with the QRC survey [R2], which argues that Hilbert-space dimension is not the same as usable feature count once you account for finite shots and noise. It also agrees with [T2], where capacity sits in fragile modes.

## 6. Numerical and statistical foundations

- **NGRC conditioning** [T6]: the feature matrix becomes ill-conditioned at short lags, high polynomial degree, or short data. An SVD solve fixes this without regularization.
- **Valid prediction time** [T7]: VPT can be predicted from the error in the first few autonomous steps. The authors introduce *valid ground-truth time*, because beyond the numerical solver's own divergence horizon a VPT is meaningless. This is an important caveat for claims of very long VPT.
- **Generalization bounds**: Rademacher-complexity bounds for RC (Chaos 2022) and for quantum reservoir classes [T8]. The QRC bounds converge in the number of samples for polynomial readouts and scale with qubit count in characterizable ways.
- **Universality**: unified classical and quantum universality conditions (2024). Dissipative models form a universal class under mild conditions.

## Synthesis: a 2026 theoretical picture

| Question | Current answer |
|---|---|
| What makes a good reservoir? | High-dimensional expansion, plus the right memory/nonlinearity balance (IPC), plus a **favorable geometric layout of task information that is robust to noise** [T2]. "Edge of chaos" is one good regime among several [T7]. |
| Can we predict performance? | For ESN memory tasks, yes, quantitatively [T1]. For general tasks, partially. |
| Why does scaling up stop helping? | Stability vs reach trade-off [T3]. In hardware, noise collapses the accessible configuration space [T4]. |
| How do we beat the limits? | Heterogeneity [T3], optimal encoding [T5], ensembles and multiplexing [A7], and readouts that use the robust modes [T2]. |
| Is there a quantum or physical exponential advantage? | **No evidence so far** under realistic noise and with honest resource accounting [T4, R2]. |

## Open theoretical questions

1. A task-general theory of performance, extending [T1] beyond memory and recall tasks.
2. Theory for the new linear-diagonal and frequency-domain reservoirs [A1, A2]: how much expressivity is lost compared with dense nonlinear recurrence, and when does it matter?
3. Noise-aware capacity measures that weight eigenmodes by their signal-to-noise ratio (implied by [T2]).
4. Conditions under which QRC beats a classical reservoir with matched resources [R2].
