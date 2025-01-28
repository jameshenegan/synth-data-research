# Robin Hood and Matthew Effects: Differential Privacy Has Disparate Impact on Synthetic Data

Ganev
2021

## Summary

This work investigates how **differential privacy (DP)** affects **generative models**—particularly regarding **underrepresented classes and subgroups** in the data. The authors study three widely used DP generative models for tabular data: **PrivBayes** (Laplace Mechanism), **DP-WGAN** (DP-SGD), and **PATE-GAN** (PATE). They run extensive experiments under various privacy budgets and class/subgroup imbalances using multiple datasets (Adult, Texas, Purchases, MNIST).

---

### Key Findings

1. **Opposite “Robin Hood” vs. “Matthew” Effects on Class/Subgroup Sizes**

   - **PrivBayes** tends to **reduce** the gap between majority and minority groups (“Robin Hood” effect).
   - **PATE-GAN** often **increases** the gap, exacerbating imbalance (“Matthew” effect).
   - **DP-WGAN** shows mixed behaviors, preserving the imbalance reasonably well only at moderate-to-high privacy budgets.

2. **Accuracy Disparities in Downstream Tasks**

   - When training **classifiers** on synthetic data, underrepresented classes or subgroups usually suffer **larger accuracy drops**.
   - The magnitude of this drop is tied to both the **privacy budget** (lower budgets = more noise = bigger drop) and the **imbalance level** (greater imbalance = bigger drop).
   - In some cases, **synthetic-data-trained models** even perform worse for majority subpopulations that share visual or tabular similarities with minority subpopulations.

3. **Influence of Privacy Budget and Imbalance**

   - Stricter privacy (smaller ϵ) amplifies distortions in **class counts** and **classification accuracy**.
   - Higher imbalance in the real data intensifies these effects.
   - For multi-attribute subgroups, even when one attribute is balanced by class, the remaining intersectional features can still become disproportionately skewed under DP.

4. **Correlation Distortions**
   - Some DP generative models (especially PATE-GAN under strict privacy) can introduce **artificial correlations** between features and target labels in the synthetic data, potentially leading to misleading patterns or unfair conclusions.

---

### Practical Implications

- **Practitioners** using DP-based synthetic data generation should be aware that **minority groups** in the real dataset may be **over- or underrepresented** in the synthetic version—depending on which DP generative mechanism is applied.
- This can result in **uneven** performance for downstream tasks (e.g., classifiers that disproportionately misclassify minority subgroups), raising concerns about **fairness** and **reliability**.
- The authors recommend **extensive subgroup analyses** and **fairness checks** before deploying DP-generated synthetic data in real-world settings.
- They also point to possible future directions, such as designing new DP training strategies that **better preserve** subgroup characteristics while still offering strong privacy guarantees.

Overall, the paper highlights that while DP generative models mitigate privacy risks, they can introduce **significant and uneven** utility losses that especially affect **underrepresented** parts of the data.
