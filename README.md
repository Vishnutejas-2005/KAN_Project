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
  - $f(x) = x^2 + \sin(x)$
  - $f(x, y) = \exp(\sin(\pi x) + y^2)$
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

### `Catastrophic_forgetting(1).ipynb`
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
- Default function: $f_2(x, y) = x^2 + y^2$
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

### `main.ipynb`
- **Goal**: Demonstrates KAN architecture on simple function approximations.
- **Key Points**:
  - Fits functions like `sin(x)`, `x^2 + sin(x)`
  - Shows how KANs achieve low error with fewer parameters compared to MLPs

---

### `f_9.ipynb`
- **Function**: \( f(x, y) = \exp(x + y^2) \)
- **Experiment**:
  - Tests symbolic learnability and generalization.
  - Compares KAN's ability to recover exponential forms and contrast against MLP behavior.

---

### `f_10.ipynb`
- **Function**: \( f(x_1, x_2, x_3, x_4, x_5) = \exp\left(\frac{1}{5} \sum_{i=1}^5 \sin^2\left(\frac{\pi x_i}{2}\right)\right) \)
- **Experiment**:
  - Tests high-dimensional symbolic composition (5D input).
  - Visualizes functional branches and spline-based recovery.

---

### `f_11.ipynb`
- **Function**: \( f(x, y) = x\left(\frac{1}{y} - 1\right) \)
- **Experiment**:
  - Benchmarks sharp rational expressions.
  - Examines how accurately KANs can recover singularities or sharp gradients.

---

### `KAN_Report.pdf`
- **Comprehensive project report** containing:
  - Theoretical foundations of KANs (Kolmogorov–Arnold representation theorem)
  - Experimental design and analysis
  - Comparison with MLPs across tasks
  - Graphs and visualizations of learned functions
  - Interpretability and scaling law insights
- **Highlights**:
  - KANs outperform MLPs in interpretability and parameter efficiency.
  - MLPs are faster to train and perform better on high-dimensional, non-symbolic datasets (e.g. MNIST).
  - Symbolic recovery using KANs is demonstrated across several complex expressions.

---

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
| Parameter Efficiency        | ✅ Fewer parameters needed     | ❌ Requires larger models       |
| Interpretability            | ✅ Symbolic regression possible| ❌ Black-box behavior           |
| High-Dimensional Scaling    | ✅ Handles 100D inputs          | ⚠️ Slower convergence           |
| Continual Learning          | ✅ Less catastrophic forgetting | ❌ Prone to forgetting          |
| Symbolic Function Recovery  | ✅ `auto_symbolic()` supported | ❌ Not applicable               |
| Training Time (small models)| ⚠️ Slower due to splines       | ✅ Faster                       |
| Oscillatory Function Fitting| ✅ Bessel/trig functions handled| ⚠️ Requires deeper tuning       |
| Singularities/Sharp Features| ✅ f₁₁-style rational terms fit | ⚠️ Less stable near singularities |

---
# 🧠 MNIST_program – KAN vs. MLP on Digit Classification

This folder contains Jupyter notebooks evaluating **Kolmogorov–Arnold Networks (KANs)** against traditional **Multi-Layer Perceptrons (MLPs)** on the MNIST digit classification task.

A PCA-reduced version of the MNIST dataset (100-dimensional input features) is used to reduce computational complexity. Each notebook explores a different architecture or parameter configuration to analyze:
- Classification performance
- Parameter efficiency
- Accuracy trade-offs between KANs and MLPs

> 📁 **Note**: These files belong to a **separate folder** from the main `KAN_Project` repository and are focused specifically on MNIST classification.

---

## 📘 Notebook Descriptions

### `main.ipynb`
- **Model**: KAN with hidden widths `[50, 20, 10]`
- **Grid Size**: 5 | **Spline Order**: 3
- **Results**:  
  - **Train Accuracy**: 98.85%  
  - **Test Accuracy**: 90.40%  
  - **Parameters**: ~196K
- **Comment**: Demonstrates KAN implementation on MNIST using PCA features. Also compares several MLP architectures.

---

### `main copy.ipynb`
- **Model**: KAN with widths `[90, 50, 10]`
- **Focus**: Architecture & parameter count (no training results shown)
- **Use**: Configuration testing

---

### `main copy 2.ipynb`
- **Model**: KAN with widths `[10, 20, 10]`
- **Focus**: Tests smaller KANs for model compactness
- **Use**: Parametric efficiency testbed

---

### `main copy 3.ipynb`
- **Model**: 3-layer MLP with `[128, 64, 32]` neurons
- **Results**:  
  - **Train Accuracy**: 99.34%  
  - **Test Accuracy**: 92.75%  
- **Comment**: A compact MLP achieving good generalization with ~23K parameters

---

### `main copy 4.ipynb`
- **Model**: 3-layer MLP with `[512, 256, 128]` neurons
- **Results**:  
  - **Train Accuracy**: 99.99%  
  - **Test Accuracy**: 94.90%  
- **Comment**: Large MLP performing best among all tested configurations

---

## 📊 Summary of Results

| Model Type | Architecture               | Parameters | Train Acc (%) | Test Acc (%) | Notes                      |
|------------|-----------------------------|------------|----------------|---------------|-----------------------------|
| KAN        | [100 → 50 → 20 → 10]        | ~196,000   | 98.85          | 90.40         | Grid=5, k=3                 |
| KAN        | [100 → 90 → 50 → 10]        | ~N/A       | —              | —             | Param config only           |
| KAN        | [100 → 10 → 20 → 10]        | ~N/A       | —              | —             | Smaller architecture        |
| MLP        | [100 → 128 → 64 → 32]       | ~23,594    | 99.34          | 92.75         | Compact 3-layer MLP         |
| MLP        | [100 → 512 → 256 → 128]     | ~217,226   | 99.99          | 94.90         | Best performing MLP         |
| MLP        | [100 → 256 → 128]           | ~60,042    | 100.00         | 95.05         | 2-layer MLP (from `main.ipynb`) |
| MLP        | [100 → 512 → 256]           | ~185,610   | 100.00         | 95.20         | 2-layer MLP (from `main.ipynb`) |

---

## 📌 Observations

- MLPs consistently outperform KANs in classification accuracy on MNIST.
- KANs show reasonable results but are slightly behind despite having similar or more parameters.
- KANs may be more beneficial in symbolic or low-dimensional domains (see main `KAN_Project`).

---

## 📂 Folder Structure
- This folder is **independent** from the main repository that handles symbolic regression and function approximation. It specifically focuses on MNIST digit classification under varied network architectures.

---

# 🧩 Interpretability – Symbolic Recovery with Kolmogorov–Arnold Networks (KANs)

This folder contains a series of Jupyter notebooks focused on evaluating and demonstrating the **interpretability** of Kolmogorov–Arnold Networks (KANs) through **symbolic recovery** of learned functions. The goal is to test whether KANs can reconstruct human-readable symbolic expressions from training data, highlighting their unique capability in **symbolic regression**.

---

## 📘 Notebook Descriptions

### `f_3.ipynb`
- **Function**: \( f(x, y) = x \cdot y \)
- **Goal**: Benchmark the performance of KAN vs MLP in fitting multiplicative interactions.
- **Highlight**: Tests a basic multiplicative symbolic function and evaluates symbolic recovery.

---

### `f_6.ipynb`
- **Function**: \( f(x, y) = \exp(J_0(20x) + y^2) \), where \( J_0 \) is the Bessel function of the first kind.
- **Goal**: Examine how KAN handles complex oscillatory functions.
- **Highlight**: Tests symbolic regression involving special functions (Bessel).

---

### `f_7.ipynb`
- **Function**: \( f(x, y) = \sqrt{1 + x^2 + y^2} \)
- **Goal**: Test model's ability to capture radial symmetry.
- **Highlight**: KAN's symbolic recovery is benchmarked against the ground truth.

---

### `f_8.ipynb`
- **Function**: \( f(x, y) = \exp(\sin(\pi x) + y^2) \)
- **Goal**: Recover symbolic expressions and validate by retraining on recovered formula.
- **Highlight**: Achieves **zero validation loss** after symbolic recovery, demonstrating perfect generalization.

---

### `f_9.ipynb`
- **Function**: \( f(x, y) = \exp(x + y^2) \)
- **Goal**: Benchmark symbolic learnability of exponential + quadratic expressions.
- **Highlight**: Assesses KAN's ability to extract concise exponential forms.

---

### `f_10.ipynb`
- **Function**: \( f(x_1, ..., x_5) = \exp\left(\frac{1}{5} \sum_{i=1}^5 \sin^2\left(\frac{\pi x_i}{2}\right)\right) \)
- **Goal**: Recover high-dimensional symbolic structure.
- **Highlight**: Tests spline smoothness and symbolic recovery in 5D inputs.

---

### `f_11.ipynb`
- **Function**: \( f(x, y) = x \left(\frac{1}{y} - 1\right) \)
- **Goal**: Evaluate symbolic fitting in the presence of sharp singularities.
- **Highlight**: Focuses on rational expressions and regions of instability.

---

### `Fey_and_Interp5.ipynb`
- **Function**: Combination of symbolic and Feynman-inspired expressions.
- **Goal**: Test symbolic recovery under mixed functional inputs.
- **Highlight**: Intermediate-level symbolic regression with compound formulas.

---

### `Fey_and_Interp11.ipynb`
- **Function**: Advanced symbolic Feynman-style equation.
- **Goal**: Evaluate symbolic generalization for more complex physics-based formulas.
- **Highlight**: Tests KAN's symbolic kernel recovery on dense, nonlinear forms.

---

### `Fey_and_Interp12.ipynb`
- **Function**: Unknown (Feynman-inspired test).
- **Goal**: Test symbolic learning on physics equations from Feynman dataset.
- **Highlight**: Uses learned spline representations to reverse-engineer expression.

---

## 🧠 Key Techniques

- **Symbolic Regression**: Using `auto_symbolic()` to extract closed-form expressions.
- **Spline-Based Learning**: KANs use spline-parameterized functions to model univariate transforms.
- **Generalization Analysis**: Validation on symbolic accuracy, not just numerical fit.

---

## 📝 Summary

| Notebook              | Function Type                            | Symbolic Recovery | Dimensionality | Notes                                 |
|-----------------------|------------------------------------------|-------------------|----------------|----------------------------------------|
| `f_3`                 | Multiplicative \( x \cdot y \)           | ✅                | 2D             | Basic bilinear test                    |
| `f_6`                 | Bessel + quadratic                       | ✅                | 2D             | Oscillatory special function           |
| `f_7`                 | Radial square root                       | ✅                | 2D             | Tests smooth, symmetric function       |
| `f_8`                 | Exponential of sinusoid + quadratic      | ✅                | 2D             | Perfect recovery post-training         |
| `f_9`                 | Exponential sum                          | ✅                | 2D             | Symbolic learnability test             |
| `f_10`                | 5D periodic composition                  | ✅                | 5D             | High-dimensional symbolic benchmark    |
| `f_11`                | Rational function                        | ⚠️ Partial        | 2D             | Tests singularity handling             |
| `Fey_and_Interp5`     | Mixed symbolic                           | ✅                | Variable       | Compound formula, symbolic generalization |
| `Fey_and_Interp11`    | Complex Feynman-style                    | ⚠️ Advanced       | Variable       | Deep symbolic patterns                 |
| `Fey_and_Interp12`    | Feynman-based (unknown)                  | ⚠️ Advanced       | Variable       | Symbolic extraction focus              |

---

## 📂 Folder Structure

- This folder is **independent** from the main repository that handles symbolic regression and function approximation. It specifically focuses on **symbolic recovery** using Kolmogorov-Arnold Networks (KANs), evaluating whether KANs can learn and extract interpretable **closed-form expressions** from data. These notebooks serve as unit tests for KAN's symbolic capabilities across a variety of analytic functions.
---

