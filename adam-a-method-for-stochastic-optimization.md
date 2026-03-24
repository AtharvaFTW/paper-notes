# Adam: A Method for Stochastic Optimization
**Authors:** Diederik P. Kingma , Jimmy Lei Ba
**Year:** 2015

---
## Summary



---

## Key Concepts:

### Adaptive Learning Rates
Adam is an optimization technique that focuses on adaptive learning rates for each weight, rather than one fixed learning rate for all weights like classic SGD

### First moment (m)
A running average of past gradients. Smooths out noisy gradients so the weight doesn't jump around.
- Formula: m = β1 * m + (1-β1) * gradient

### Second moment (v)
A running average of past gradients squared. Tracks how large the gradients have been.
- Formula: v = β2 * v + (1-β2) * gradient²
- If the v is large (weight has been getting big gradients) -> divide by large number -> small update
- If the v is small (weight has been getting small gradients) -> divide by small number -> large update

### Bias Correction
m and v start at zero, so early on they're too small. Adam corrects for this:
- m_corrected = m / (1 - β1^t)
- v_corrected = v / (1 - β2^t)

Where t is the current timestep. This just scales them up in early steps.

### Default Values
The paper recommends:
- lr = 0.001
- β1 = 0.9 (momentum decay)
- β2 = 0.999 (velocity decay)
- epsilon = 1e-8 (prevents division by zero)

These work well across a wide range of problems. You rarely need to change them.
