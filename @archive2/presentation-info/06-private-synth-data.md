## Private Synthetic Data

**Summary**

This section focuses on **privacy issues unique to synthetic data**—particularly how generating data in the same space as the original dataset poses both **opportunities** (e.g., direct substitution for real data) and **challenges** (e.g., extremely high-dimensional outputs). The authors highlight the need to reason about privacy at the algorithmic level, emphasize the limits of releasing large, high-fidelity synthetic datasets, and explore several methodological approaches.

---

### 1. Key Observations for Private Synthetic Data

1. **High-Dimensionality**

   - Synthetic datasets often contain a large number of rows and columns, making the “output space” extremely high-dimensional.
   - Under differential privacy, such large outputs can inflate sensitivity, making it more difficult to achieve good utility without using a large privacy budget.

2. **Privacy is an Algorithmic Property**

   - Differential privacy concerns the _procedure_ that generates synthetic data, not the final dataset itself.
   - A single sample from the generator cannot be deemed “private” or “non-private” in isolation—only the algorithm can satisfy DP guarantees.

3. **Private Data vs. Private Generator**

   - Typically, one trains a **private generator** under DP, then samples as many synthetic records as needed. By the post-processing theorem, generating additional data does not further degrade the privacy guarantees.
   - However, **training a single DP model** to then generate large datasets often sacrifices utility, as the DP constraints limit how much information the generator can extract from the original data.

4. **Handling Outliers and Fairness**
   - DP-based methods struggle to represent outliers or minority groups because these are by definition unique data points and thus are more likely to be “hidden” or lost to protect privacy.
   - There is an inherent tension between retaining minority groups (fairness) and shielding sensitive individuals’ identities (privacy).

---

### 2. Existing Methods and Technologies

1. **Deep Learning Approaches**

   - **GANs and VAEs**: Adapted to satisfy DP using techniques like **DPSGD** (Differentially Private Stochastic Gradient Descent) or **PATE** (Private Aggregation of Teacher Ensembles).
   - Careful placement of privacy (e.g., in the GAN discriminator vs. generator) can impact both the privacy budget and the fidelity of synthetic samples.

2. **Statistical / Low-Dimensional Models**

   - **Bayesian Networks**: Factorize the joint distribution into lower-dimensional conditional distributions.
   - **Copula Models**: Focus on correlation structures.
   - **Marginal-Based Approaches** (e.g., NIST competition winner): Differentially private estimation of all 2-way marginals, followed by sampling consistent synthetic data.

3. **Impossibility Results & Trade-Offs**
   - Theoretical work shows it’s infeasible to produce a single DP synthetic dataset preserving _all_ correlations and structure efficiently.
   - Practitioners therefore tailor which correlations matter most for a given use case (utility) and accept compromises in other aspects.

---

### 3. Partially Synthetic Data

1. **Definition**

   - Only the “sensitive” attributes are replaced with synthetic values; “quasi-identifiers” remain from the real dataset.
   - Often done via **multiple imputation** techniques (e.g., decision trees, random forests).

2. **Utility vs. Privacy**
   - Retaining real quasi-identifiers can improve utility (because the model only needs to learn the distribution of sensitive attributes conditioned on these identifiers).
   - However, it raises **privacy concerns** if quasi-identifiers are themselves sensitive or if they enable linkage attacks.
   - Few methods provide formal privacy guarantees, although **Label DP** has been proposed for this setting.

---

**Overall Takeaways**

- Generating **truly privacy-preserving synthetic data** is intrinsically hard due to the high-dimensional nature of full datasets and the need to protect sensitive outliers or minority groups.
- **No one-size-fits-all solution** exists: developers must carefully balance privacy budgets, utility goals, and fairness considerations.
- **Partially synthetic approaches** can be more tractable but may reveal quasi-identifiers, complicating privacy protections.
- **Advanced DP-based methods** (e.g., DPSGD, PATE) offer formal privacy but can reduce fidelity, especially for large or complex datasets.
