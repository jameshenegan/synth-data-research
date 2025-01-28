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

# Break out

Below is a concise timeline highlighting key developments in synthetic data over roughly the past 30 years. It combines milestones from both the statistical and computer science perspectives, showing how the idea of synthetic data evolved from early theoretical proposals to broad real-world deployments.

---

### **Before 1993: Foundations in Multiple Imputation**

- **1978 & 1987** – Donald Rubin introduces multiple imputation (MI) for handling missing data. This framework later becomes the foundation for synthetic data methods used for disclosure protection.

---

### **Early 1990s: First Proposals of Synthetic Data**

- **1993** – **Rubin** suggests using MI to generate fully synthetic data as a novel disclosure protection strategy.
- **1993** – **Little** proposes _partially_ synthetic data, synthesizing only the most sensitive or risky parts of the dataset.

---

### **Mid-Late 1990s: Initial Applications and Extensions**

- **1994** – **Fienberg** proposes using a smoothed estimate of a dataset’s distribution (via bootstrapping) for synthetic data.
- **1997** – **U.S. Federal Reserve Board** replaces high-risk monetary values in the Survey of Consumer Finances with synthetic values (Kennickell, 1997).
- **Late 1990s** – Synthetic data remains primarily an idea in the statistical disclosure control community; computer science approaches to data privacy focus on _k_-anonymity and related models, which do not align neatly with synthetic data.

---

### **Early 2000s: Methodological Foundations**

- **2001 & 2004** – **Abowd & Woodcock** demonstrate generating synthetic longitudinal, linked data (French National Institute of Statistics data), showcasing utility for complex datasets.
- **2003** –
  - **Raghunathan et al.** develop a full methodology for valid inference from _fully_ synthetic data.
  - **Reiter** develops a complementary methodology for _partially_ synthetic data.
- **2006** – **Dwork et al.** formally introduce **differential privacy (DP)**, shifting the privacy focus to the _mechanism_ rather than the _released data_. This opens the door to broader adoption of synthetic data in computer science.

---

### **Mid-Late 2000s: Large-Scale Releases and DP Foundations**

- **2006** – **Abowd et al.** release the _SIPP Synthetic Beta_, linking the Survey of Income and Program Participation (SIPP) to administrative data (Social Security Administration and IRS).
- **2007** – **Barak et al.** propose one of the first **differentially private synthetic data** methods using Fourier transforms and linear programming on contingency tables.
- **2008** –
  - **OnTheMap** (Machanavajjhala et al.) becomes the first large-scale application that incorporates formal (ε, δ)-probabilistic differential privacy to release commuting pattern data.
  - **Abowd & Vilhuber** and others adapt ideas from the statistical synthetic data community to DP.

---

### **Early 2010s: Expanded Use in Agencies & DP Research**

- **2011** – **Reiter & Kinney** highlight differences in combining rules between fully and partially synthetic data; clarify that posterior draws of parameters are unnecessary for partial synthesis.
- **2011** – **Synthetic Longitudinal Business Database** is released (Kinney et al.), partially synthetic data covering all U.S. businesses.
- **2012** – **Reiter & Kinney** further underscore technical distinctions between full and partial synthesis under DP.
- **2013–2014** – Approaches like **PrivBayes** (Zhang et al.) and **DPCopula** (Li et al.) use Bayesian networks and copula models to capture high-dimensional dependencies under DP.

---

### **Mid-Late 2010s: Machine Learning and GANs**

- **2015** – **Statistics Netherlands** publishes synthetic EU-SILC files for Eurostat, mainly for training and code development purposes.
- **2016** – The **Maryland Longitudinal Data System Center** initiates the Synthetic Data Project for longitudinal education data.
- **2017** – Emergence of applying **Generative Adversarial Networks (GANs)** to microdata (e.g., medGAN by Choi et al.) for synthetic health records.
- **2018–2019** – The **NIST Differential Privacy Synthetic Data Challenge** spurs innovation; winning methods often rely on Bayesian networks or preserving certain marginals under DP.

---

### **Late 2010s–Early 2020s: Refinements and New Applications**

- **2019–2020** – Rapid expansion of **GAN-based** synthetic data methods (CTGAN by Xu et al., Causal TGAN by Wen et al.), focusing on mixed data types, causal relationships, and improved fidelity.
- **2020** – **Statistics Canada** uses synthetic data in a hackathon, highlighting broader interest among national statistical offices.
- **2021–2022** –
  - Ongoing work at the **Australian Bureau of Statistics** to evaluate synthetic data for broader microdata access.
  - Continued research on **differentially private** approaches (e.g., quick, flexible neural network approaches, improved Bayesian networks, and specialized techniques for high-dimensional data).

---

### **Recent Trends and Ongoing Research**

- **Integration with Formal Privacy**: Methods increasingly incorporate DP guarantees, balancing utility and privacy by adjusting “noise” in synthesis mechanisms.
- **Advanced ML Techniques**: Beyond GANs, there is growing interest in Variational Autoencoders (VAEs), transformers, and hybrid models tailored to tabular/categorical data.
- **Agency Adoption**: Statistical agencies, government offices, and industry continue to experiment with synthetic data as a safe yet useful proxy for sensitive microdata.
- **Challenges**: Developing robust utility metrics, handling complex survey designs, ensuring interpretability, and reliably protecting privacy remain focal research areas.

---

**In summary**, synthetic data practices originated in the early 1990s within statistics (Rubin, Little) and took shape with important agency releases and refinements. The emergence of differential privacy in 2006 ignited computer science interest, leading to numerous DP-focused methods and real-world applications. Recent advances in generative modeling—especially GANs—have led to new tools, but also new challenges in balancing data fidelity and privacy. Over the last decade, synthetic data have transitioned from a niche idea to a widely discussed solution, embraced by statistical agencies, academic researchers, and private organizations alike.

## Break Out

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
