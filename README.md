# KAN_Project
# 🧠 Kolmogorov–Arnold Networks (KANs) – Project Experiments

This repository presents a series of experiments using **Kolmogorov–Arnold Networks (KANs)**, a novel neural network paradigm inspired by the **Kolmogorov–Arnold representation theorem**. KANs model multivariate functions through compositions of univariate functions and additions, allowing for:
- Better interpretability
- Efficient parameterization
- Symbolic regression capabilities
- Robustness in continual learning

---

## 📁 Repository Contents

This project includes Jupyter Notebooks demonstrating:
- Function approximation (including Feynman symbolic functions)
- Interpretability via symbolic recovery
- Performance comparisons with MLPs
- Neural scaling laws
- Digit classification on MNIST
- Catastrophic forgetting in continual learning

---

## 📘 Notebooks Overview

### `main.ipynb`
- **Goal**: Demonstrates KAN architecture on simple function approximations.
- **Key Points**:
  - Fits functions like `sin(x)`, `x^2 + sin(x)`.
  - Shows how KANs achieve low error with fewer parameters compared to MLPs.

---

### `Interpretability.ipynb`
- **Goal**: Recovers symbolic expressions from learned KAN functions.
- **Function Examples**:
  - \( f(x) = x^2 + \sin(x) \)
  - \( f(x, y) = \exp(\sin(\pi x) + y^2) \)
- **Highlight**:
  - Uses `auto_symbolic()` to produce human-readable formulas.
  - Demonstrates true interpretability of the KAN structure.

---

### `MNIST_program.ipynb`
- **Goal**: MNIST digit classification using KANs.
- **Result**:
  - Achieves ~97% accuracy with fewer weights than a standard MLP.
- **Takeaway**:
  - KANs are competitive even in non-symbolic, high-dimensional image tasks.

---

### `Neural_scaling_laws.ipynb`
- **Goal**: Explore how KAN and MLP performance scale with model size.
- **Findings**:
  - KANs exhibit steeper performance gains with increased size (neurons).
  - Plots show improved generalization with fewer parameters.

---

### `Cataastrophic_forgetting(1).ipynb`
- **Goal**: Evaluate KANs in continual learning settings.
- **Setup**:
  - Sequentially learn functions like `x^2`, `sin(x)`, and `exp(x)`.
- **Outcome**:
  - KANs preserve earlier learned tasks better than MLPs (less forgetting).

---

## 🧪 Function-Specific Experiments

### `f_1.ipynb`
- Trains KAN and MLP on symbolic and Feynman functions.
- Compares:
  - Loss curves
  - Training time
  - Symbolic recoverability

---

### `f_2.ipynb`
- Studies performance as hidden width increases.
- Default function: \( f_2(x, y) = x^2 + y^2 \)
- Observes parameter efficiency with increasing complexity.

---

### `f_3.ipynb` and `f_3_1.ipynb`
- Target: \( f(x, y) = x \cdot y \)
- Includes more Feynman functions and deeper symbolic matching in `f_3_1`.

---

### `f_4.ipynb`
- Function: \( f(x_0, ..., x_{99}) = \sum \sin^2(x_i) \)
- Tests KANs in **100D input** space.
- Shows robustness and fitting capability at scale.

---

### `f_5.ipynb`
- Function: \( \sin(x_0 + x_1) + \exp(x_2^2 + x_3^2) \)
- Tests 4D compositional modeling.

---

### `f_6.ipynb`
- Function: \( \exp(J_0(20x) + y^2) \) (with Bessel function)
- Evaluates fitting performance on oscillatory + nonlinear terms.

---

### `f_7.ipynb`
- Function: \( \sqrt{1 + x^2 + y^2} \)
- Benchmarks radial symmetry fitting and generalization.

---

### `f_8.ipynb`
- Function: \( \exp(\sin(\pi x) + y^2) \)
- Performs symbolic recovery and retraining from the recovered expression.
- Demonstrates nearly **zero loss** on validation with symbolic model.

---

## 📌 Summary of Results

| Feature                     | KAN                            | MLP                            |
|----------------------------|--------------------------------|--------------------------------|
| Parameter Efficiency        | ✅ Few parameters              | ❌ Needs more layers/nodes     |
| Interpretability            | ✅ Symbolic regression possible | ❌ Black-box weights           |
| High-Dimensional Scaling    | ✅ Performs well (e.g., 100D)   | ⚠️ Slower convergence           |
| Continual Learning          | ✅ Less forgetting              | ❌ Performance degradation     |
| Symbolic Function Recovery  | ✅ With `auto_symbolic()`       | ❌ Not applicable              |
| Training Time (for small models) | ⚠️ Slightly slower due to functional kernels | ✅ Faster, fewer ops |

---
