**Key Milestones in Synthetic Data**

1. **Foundational Multiple Imputation (1978 & 1987)**

   - **Donald Rubin** develops multiple imputation to handle missing data.
   - This framework later inspires the idea of using synthetic data for privacy.

2. **Fully vs. Partially Synthetic Data (1993)**

   - **Rubin** formally proposes generating _fully_ synthetic data—impute _all_ records and variables to protect confidentiality.
   - **Little** introduces a _partially_ synthetic approach—only synthesize the most sensitive records or fields.

3. **Differential Privacy (2006)**

   - **Dwork et al.** redefine privacy by focusing on how data are released (the _mechanism_) rather than the released data itself.
   - This shift opens the door to _differentially private synthetic data_ methods.

4. **GANs Enter the Scene (2014)**

   - **Goodfellow et al.** propose Generative Adversarial Networks (GANs) to create synthetic images.
   - Researchers soon adapt GANs to generate _tabular (micro) data_, leading to advanced privacy-preserving data synthesis techniques.

5. **Modern Developments**
   - Integration of **DP** with GANs and other machine learning models (e.g., Bayesian networks, autoencoders) improves both _utility_ and _privacy_.
   - Statistical agencies and industry increasingly adopt synthetic data to protect confidentiality while allowing broader data access.

**Refined Timeline**

- **1987:** Donald Rubin formalizes multiple imputation, providing a key foundation for synthetic data.
- **1993:** Rubin and Roderick Little propose using multiple imputation to generate synthetic data, introducing fully and partially synthetic approaches.
- **Early 2000s:** Abowd & Woodcock (2001, 2004) demonstrate synthesizing longitudinal, linked datasets.
- **2006:**
  - U.S. Census Bureau releases the large-scale SIPP Synthetic Beta.
  - Dwork et al. introduce differential privacy, focusing on protecting the _mechanism_ rather than the released data.
- **2007:** Barak et al. publish one of the first differentially private synthetic data methods.
- **2008:** OnTheMap (Machanavajjhala et al.) applies formal privacy techniques at scale.
- **2011:** The Synthetic Longitudinal Business Database is released.
- **2014:** PrivBayes (Zhang et al.) and DPCopula (Li et al.) address high-dimensional data under DP.
- **2015:** Statistics Netherlands publishes synthetic EU-SILC data.
- **2016:** Maryland’s Synthetic Data Project begins.
- **2017:** Generative Adversarial Networks (GANs) emerge for tabular data (medGAN).
- **2018–2019:** The NIST DP Synthetic Data Challenge furthers innovation in differentially private data synthesis.
