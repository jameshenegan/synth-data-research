## De-biased Synthetic Data Generation

**Summary**

This section examines how **synthetic data** can be used to **remove or mitigate biases** found in real-world training datasets. Whereas standard fairness methods typically modify or post-process trained models, **fair synthetic data** approaches aim to adjust the data before training. Below are the key points:

---

## 1. Motivation: Bias in Training Data

- **Machine learning models inherit biases** from their training data (e.g., historical discrimination in hiring).
- Correcting biases in already-trained models requires deep knowledge of the model internals and an understanding of different fairness metrics.
- **Synthetic data generation** for fairness attempts to produce data that has reduced or eliminated certain biases.

---

## 2. Fairness Notions

Fairness in ML is complex and can be defined in multiple ways, each requiring an identified set of **protected attributes** (e.g., race, gender).

1. **Fairness Through Unawareness (FTU)**

   - The protected attribute cannot directly be used by the predictor.
   - However, **indirect correlations** (where other features correlate with protected attributes) can still result in bias.

2. **Demographic Parity (DPa)**
   - A predictor’s outputs (e.g., job offers) should be **independent** of protected attributes.
   - Often enforced via **causal modeling** by removing edges or information that depend on protected attributes.
   - Can significantly hurt predictive performance since many correlated variables may be “contaminated” and must be dropped or altered.

---

## 3. Limitations of Fair Synthetic Data

1. **Distribution Shift**:
   - Even if a synthetic dataset is “fair,” a model trained on it may not remain fair when deployed on **real data**, because real-world feature distributions could differ from those in the synthetic data.
2. **Model-Specific Definitions**:
   - Fairness is typically assessed for a **specific predictor** trained on a given dataset; it does not necessarily generalize to all possible models that could be trained.
3. **Minority/Outlier Representation**:
   - Ensuring **protected groups** are adequately represented while also preserving overall utility can be challenging, given the inherent privacy and sampling constraints (see also discussion on outliers in Section 7).

---

## 4. Existing Fair Synthetic Data Methods

1. **Causal, GAN-Based Approaches**
   - Example: [23] constructs a **causal model** of the data and drops certain edges related to protected attributes to enforce fairness notions (like FTU or DPa).
   - The synthetic data generated has these biased causal pathways removed.
2. **GANs with Fairness Constraints**
   - Example: [22] adds a **fairness penalty** term to a GAN’s loss function. This trades off fidelity vs. fairness—if the model improves fidelity but reintroduces bias, it is penalized accordingly.

---

## 5. Evaluating Utility & Fidelity

- Much of the utility/fidelity assessment mirrors **Section 6.2** (e.g., Train-on-Synthetic-Test-on-Real).
- Additionally, **bias/fairness metrics** must be evaluated. For instance:
  - Whether the protected attributes correlate with model outputs.
  - Whether different demographic groups have similar error rates or outcomes.

---

### Key Takeaways

- **Fair synthetic data** can be an attractive alternative to per-model de-biasing because it creates a single adjusted dataset for multiple downstream tasks.
- **No universal notion of fairness**: The chosen fairness definition (e.g., FTU, DPa) dictates what data modifications are needed and what trade-offs must be made.
- **Practical Limitations**: Shifts between synthetic and real distributions, plus the complexity of multi-model usage, mean fair synthetic data may not guarantee fairness in all deployment scenarios.
