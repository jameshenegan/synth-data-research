## Utility, Fidelity and Privacy of Synthetic Data

**Summary**

The text discusses the core attributes and design principles for meaningful synthetic data, emphasizing that it should be **similar** to the real data but also **different** enough to avoid replicating the same issues (privacy, bias, or small sample size). The authors identify **three main attributes**—utility, fidelity, and privacy—along with additional practical considerations:

1. **Utility**

   - Refers to how well synthetic data performs on specific tasks compared to real data.
   - Often assessed using the “Train on Synthetic, Test on Real” (TSTR) approach, where models are trained on synthetic data and then evaluated on real data.
   - Other utility considerations include model fairness and general performance metrics (accuracy, precision, etc.).

2. **Fidelity**

   - Measures how closely the synthetic data statistically matches the real dataset.
   - Involves comparing distributions or structural properties (e.g., time-series dependencies, valid postcodes).
   - Full statistical match can be undesirable if the original data is biased or if privacy needs require reducing fidelity.

3. **Privacy**

   - Concerns how much real-data information might be revealed through the synthetic data.
   - Formalized by frameworks such as differential privacy, which provides worst-case guarantees about limiting information leakage.
   - Generally, higher fidelity can decrease privacy, so there’s a **trade-off** between privacy and fidelity.

4. **Synthetic Data Desiderata**

   - **Syntactical Accuracy**: Generated data should be plausible, respecting domain-specific constraints (e.g., valid postcodes, correct time-series ordering).
   - **Privacy**: Quantifiable and robust, typically captured through definitions like differential privacy or similar approaches.
   - **Statistical Accuracy**: Relevant statistical properties (distributions, correlations) should match real data to the extent needed by the use case.
   - **Efficiency**: The method should scale with the dimension of the dataset; generating synthetic data in high-dimensional spaces is computationally challenging.

5. **Challenges and Impossibility Results**
   - There is no universal, computationally efficient method that provides **both** strong privacy guarantees **and** perfect fidelity for all correlations.
   - Instead, generation methods must prioritize which relationships in the data are most crucial for the intended use case.
   - Some relaxations (e.g., preserving “most” correlations rather than all) are possible but require careful assessment to understand what information might be lost.

Overall, **synthetic data must be tailored to specific use cases** to balance utility, fidelity, and privacy. A one-size-fits-all solution does not exist; instead, data scientists must decide which data characteristics are essential and which can be relaxed to enhance privacy or reduce bias.
