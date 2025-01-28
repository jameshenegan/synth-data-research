## Auditing Synthetic Data

**Summary**

This section explores how to empirically evaluate synthetic data along two main dimensions—**privacy** and **utility/fidelity**:

---

### 1. Evaluating the Privacy of Synthetic Data

1. **Differential Privacy Verification**

   - Differential privacy (DP) is a property of the _algorithm_ rather than the final dataset.
   - Researchers have proposed methods to check compliance with DP by querying or attacking the generation algorithm, but true “proof” requires a formal DP analysis rather than just empirical tests.

2. **Leakage Estimation**

   - Techniques from **quantitative information flow** can estimate how much private information a synthetic data generator leaks under specific threat models (e.g., membership inference).
   - These methods often treat the generator as a “black box,” requiring multiple samples but can help in practice to tune or compare privacy parameters.

3. **Empirical Tests on Final Datasets**

   - Some practitioners use a **hold-out test set** (i.e., Nearest-Neighbour Distance Ratio, NNDR) to compare synthetic data points to real data points.
   - However, such metrics can miss “holes” where the generator deliberately avoids real data points, and thus do not fully capture privacy risks.

4. **Privacy Attacks**
   - **Membership and Attribute Inference Attacks**: These can be adapted to test whether synthetic data leaks information about who was in the original dataset or which attributes they had.
   - **Black-Box Adversarial Approaches**: Recent work (e.g., shadow modeling) highlights vulnerabilities in many synthetic data generators, suggesting that strong privacy often degrades accuracy.

---

### 2. Evaluating Utility and Fidelity

**Utility** and **fidelity** are related but distinct concepts:

- **Utility** focuses on **task performance**: For instance, how well a model trained on synthetic data performs on (or ranks models for) a real-world task.
- **Fidelity** measures how **statistically similar** the synthetic data is to the real data, often without reference to a particular downstream task.

#### 2.1 Utility-Driven Evaluation

1. **Train on Synthetic, Test on Real**

   - Analysts train a machine learning model on synthetic data and then measure performance on real data.
   - If performance is good (e.g., classification accuracy, AUROC), the synthetic data is considered useful for that task.

2. **Model Selection**
   - Synthetic data can be used to compare models or hyperparameters.
   - The ranking of models (best to worst) on synthetic data should ideally match the ranking on real data.

#### 2.2 Fidelity-Driven Evaluation

1. **Low-Dimensional Checks**

   - Compare 1- or 2-dimensional marginals (histograms, correlations) between real and synthetic data.
   - Measures such as total variation distance, correlation coefficients, or Cramer’s V can indicate how closely the distributions match on these limited dimensions.

2. **Higher-Dimensional Metrics**
   - **Propensity scores**: Train a classifier to differentiate real vs. synthetic samples; lower classification accuracy implies better fidelity.
   - **GAN-Based Metrics**: Precision and recall for generative models evaluate how well synthetic data covers the real data “support” (recall) and avoids generating unrealistic samples (precision).

---

**Key Takeaways**

- **Privacy Evaluation**:

  - True differential privacy must be proven at the algorithmic level.
  - Empirical methods (attacks, leakage estimation) provide insights but cannot formally guarantee DP.
  - Attacks on synthetic data show that strong privacy often reduces utility.

- **Utility & Fidelity Evaluation**:
  - Must be tailored to specific use cases (e.g., classification tasks, model selection).
  - Fidelity metrics gauge distributional similarity; utility metrics gauge task performance.
  - High fidelity does not always mean high utility for every task, and vice versa.

Overall, **no single metric** can capture all aspects of privacy, utility, and fidelity for synthetic data. Effective evaluation involves combining **formal guarantees** (when available) with **empirical tests** tailored to the intended application and threat model.
