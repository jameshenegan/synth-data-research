# PATE-GAN: Generating Synthetic Data with Differential Privacy Guarantees

Jordon
2021

## Summary

The paper addresses the challenge of generating **synthetic datasets** that preserve key statistical properties of real data **while providing rigorous privacy guarantees**. To achieve this, the authors propose **PATE-GAN**, a method that combines:

1. **Generative Adversarial Networks (GANs)** for synthetic data generation, and
2. **Private Aggregation of Teacher Ensembles (PATE)** to ensure **differential privacy** of the generated data.

---

### Key Contributions

1. **Differentially Private GAN Framework**

   - The authors adapt the PATE framework to a GAN setup by replacing the usual GAN discriminator with a “teacher-student” ensemble (the PATE mechanism).
   - **Multiple “teacher” discriminators** are each trained on disjoint subsets of the sensitive dataset, and their outputs are aggregated _with added noise_ to provide privacy guarantees.
   - A **student discriminator** is then trained on (teacher-labeled) generated samples, ensuring that the overall process **does not reveal individuals’ sensitive data** (differential privacy).

2. **Improved Privacy-Utility Trade-off**

   - PATE-GAN’s privacy mechanism (which limits the influence of any single real-data sample on the teacher outputs) allows for **tighter privacy bounds** than methods that rely on noisy gradients alone (e.g., DPGAN).
   - With a fixed privacy budget, PATE-GAN can thus generate **higher-quality synthetic data** compared to prior work.

3. **New Metric: Synthetic Ranking Agreement (SRA)**
   - Beyond training models on synthetic data and testing on real data (an existing measure of utility), the authors propose **SRA** to evaluate **how well the synthetic data preserves the _relative performance ranking_ of different predictive models**.
   - This ensures that if one model outperforms another on real data, it tends to do so on the synthetic data as well—valuable for machine-learning competitions and method comparisons on non-public datasets.

---

### Experimental Findings

- **Datasets Used:** The paper presents results on six different datasets, including Kaggle competition data, two real-world medical datasets, and two UCI benchmarks.
- **Comparison to Baseline (DPGAN):**
  - **PATE-GAN consistently outperforms DPGAN** in terms of how well models trained on the synthetic data perform on real data.
  - PATE-GAN also better preserves the **ranking** of predictive models, an important practical consideration.
- **Effect of Privacy Budgets:**
  - As differential privacy constraints are loosened (i.e., larger ε), both PATE-GAN and DPGAN approaches improve and converge closer to a non-private GAN.
  - Across a wide range of privacy levels, **PATE-GAN maintains higher utility**.

---

### Conclusion

The authors introduce **PATE-GAN** as a robust framework for generating differentially private synthetic datasets. By combining the PATE mechanism with GANs, the approach maintains strong formal privacy guarantees while yielding synthetic data with **higher predictive utility** than previous methods. Moreover, the new **SRA metric** provides an additional lens to assess the utility of synthetic data by measuring its ability to preserve performance orderings of different models, which is crucial for tasks like algorithm benchmarking and Kaggle-style competitions.
