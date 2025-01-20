# Synthetic Data - what, why and how?

Jordon
2022

## Summary

The key insights from this review on synthetic data for statistical disclosure control are:

## Synthetic Data Approaches

1. Full synthesis: Generates entirely new datasets based on the statistical information in the original data.

2. Partial synthesis: Only synthesizes some variables (e.g., sensitive or identifying variables) while keeping others unchanged.

3. Differential privacy: Aims to prevent reconstruction of original data by limiting the effect of any individual record on the synthetic data.

## Benefits and Challenges

- Synthetic data allows wider dissemination of data while protecting respondent privacy and confidentiality.

- The goal is to maintain valid statistical inferences from synthetic data compared to the original data.

- Creating synthetic populations that give valid inferences for a wide variety of analyst models is challenging.

- Uncongeniality between the model used to create synthetic data and analyst models can lead to biased or inefficient estimates.

## Key Considerations

- Methods need to continually evolve to respond to increasing threats of disclosure from external information.

- It's crucial to balance disclosure control with maintaining the utility and validity of statistical analyses.

- For longitudinal studies, synthesizing later waves while maintaining consistency with previously released synthetic data poses additional challenges.

## Implementation

- Sequential regression approaches are commonly used to generate synthetic data, modeling the joint distribution as a series of conditional distributions.

- Software packages like synthpop (R) and IVEware implement synthetic data generation methods.

- Differential privacy methods are emerging, with implementations often available on platforms like GitHub.

## Future Directions

- More research is needed on nonparametric approaches for creating synthetic samples.

- Developing trust between data producers and users regarding synthetic data is important.

- Further work is required on synthetic data generation for longitudinal studies and big data scenarios.

Citations:
[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/48038041/a1d6e0ec-cb6a-4e4c-b4d7-8bdca7240a13/2205.03257v1.pdf

## Abstract

**Summary**

This explainer highlights the growing importance of **synthetic data**—artificially generated data designed to resemble real datasets—for a variety of applications, including **privacy**, **fairness**, and **data augmentation**. It examines both the **potential** of synthetic data and the **challenges** that arise in its practical deployment.

1. **Significant Potential**

   - **Privacy**: Well-crafted synthetic data can support data sharing without exposing sensitive information.
   - **Fairness**: Generating de-biased or balanced data can help reduce systematic discrimination.
   - **Data Augmentation**: Creating additional samples can improve model robustness and training efficiency.
   - **Project Acceleration**: Synthetic data facilitates faster prototyping and testing in data science and software development pipelines.

2. **Not Automatically Private**

   - Simply generating data does not ensure anonymity; synthetic datasets may still leak sensitive information.
   - Formal methods (e.g., **differential privacy**) are often needed to provide rigorous privacy guarantees.

3. **No Perfect Substitute for Real Data**

   - Privacy-preserving synthetic data inevitably distorts certain features, which may reduce its usefulness for some tasks.
   - For high-stakes applications, final models typically need validation or fine-tuning on real data.

4. **Difficulties with Outliers and Rare Events**

   - Unusual or extreme data points (e.g., billionaires in a wealth dataset) are harder to represent privately.
   - Synthetic data may either omit them (leading to poor fidelity) or inadvertently reveal sensitive details.

5. **Challenges in Privacy Evaluation**

   - **Rigorous privacy** focuses on how the data was generated, not on the dataset alone.
   - Empirical checks can reveal flaws but can also give false confidence if not carefully conducted.

6. **Complexity of Black-Box Generative Models**

   - Large, overparameterized models like deep neural networks can produce high-fidelity synthetic data.
   - Their internal workings can be opaque, making it difficult to assess privacy and accuracy consistently.

7. **Beyond Privacy**
   - Synthetic data can advance **fairness, bias reduction**, and **robustness** in machine learning.
   - Further research is needed to understand both the opportunities and potential pitfalls fully.

Overall, **synthetic data** is a powerful tool but must be used **strategically**—with careful design, clear objectives, and robust validations—to ensure the right balance between utility and privacy.

## Introduction

**Summary**

Organizations today have access to massive and diverse datasets with the potential to significantly improve decision-making and fuel research. However, privacy regulations (such as GDPR and CCPA), along with inherent vulnerabilities in high-dimensional data, make sharing or using real data difficult. Traditional anonymization often fails to protect individual privacy, creating a bottleneck in deploying data-driven techniques.

**Synthetic data** offers a potential solution. By generating artificial datasets that approximate the statistical properties of real data, one can:

- **Control privacy**: Limit the risk of re-identification by carefully regulating the similarity between synthetic and real data.
- **Mitigate bias**: Adjust historical imbalances and explore plausible hypothetical scenarios.
- **Facilitate innovation**: Provide safe, representative test environments for researchers, startups, and developers, supporting rapid prototyping and validation of machine learning systems.

Despite its promise, synthetic data also presents challenges. Ensuring utility (the data’s usefulness for model training), fidelity (faithful representation of original data characteristics), and privacy (protection against re-identification) requires well-designed techniques and frameworks. Moreover, generating synthetic data for fairness and data augmentation necessitates specialized methods.

In this report, the authors introduce:

1. **Definition and history** of synthetic data: Explaining key concepts and early motivations.
2. **Applications** in machine learning: Highlighting how synthetic data can drive model development and testing.
3. **Privacy frameworks** (e.g., differential privacy): Discussing limitations and how they intersect with synthetic data generation.
4. **Evaluation metrics**: Outlining how to assess utility, fidelity, and privacy of synthetic data.
5. **Private synthetic data generation methods**: Surveying existing techniques and exploring hybrid real-synthetic approaches.
6. **Fairness and data augmentation**: Examining how synthetic data can reduce bias and expand training sets.
7. **Technical survey of generative models**: Reviewing the modern tools that enable effective synthetic data creation.
8. **Industry perspectives**: Summarizing insights from startups and practitioners on deploying synthetic data responsibly.

Ultimately, while synthetic data can preserve privacy, improve research workflows, and expand innovation opportunities, careful strategies are required to ensure that the data is both safe and valuable for its intended uses.

## What is Synthetic Data?

**Summary**

The text provides an overview of **synthetic data**—data generated by a mathematical model rather than real-world processes—and addresses key questions around its definition, potential applications, and limitations.

1. **Definition and History**

   - **Synthetic data** is defined as data generated by a purpose-built model or algorithm to solve data science tasks.
   - It contrasts with **real data**, which stems from actual processes (e.g., financial transactions, medical tests).
   - Synthetic data has a long history, dating back to Monte Carlo methods in the 1940s. Researchers often use it for **“ground truth”** simulations, facilitating model development and evaluation.

2. **Motivations**

   - **Privacy Regulations**: Stricter rules (e.g., GDPR) encourage synthetic data as a way to share information without disclosing identifiable real data.
   - **Bias Removal**: Synthetic data can be engineered to reduce or remove historical biases related to attributes like gender or race.
   - **Data Augmentation**: Synthetic data can expand limited real datasets to improve the robustness of machine learning models.
   - **Privacy Protection**: There is hope that synthetic data, if generated properly, can replace sensitive real data and mitigate disclosure risks.

3. **Challenges**

   - **No Automatic Privacy**: Simply generating data with standard methods (like GANs) does not guarantee privacy—models can memorize and inadvertently reveal real examples.
   - **No Automatic Bias Mitigation**: Off-the-shelf synthetic data generation can perpetuate existing biases if not explicitly addressed.
   - **Quality and Realism Trade-Off**: There is often tension between data realism (for utility) and privacy protection.

4. **Key Questions**

   1. _Can synthetic data be used in place of real data to do the same tasks (training models, hypothesis testing, data analysis)?_
      - Yes in principle, but specialized methods (e.g., Bayesian updates for model parameters, bias-correction strategies) often improve accuracy when dealing with synthetic data.
   2. _Can synthetic data be treated exactly like real data (e.g., linking records from different datasets)?_
      - Linking different synthetic datasets independently generated from real data can break 1-to-1 correspondence across records. Specialized approaches—or regenerating a single, joint synthetic dataset—may be needed.

5. **Integrations with Other Privacy Technologies**
   - **Secure Research Environments**: Synthetic data can be used in a tiered approach—start with strongly private synthetic versions, refine methods, and only grant access to more sensitive real data as needed.
   - **Federated Learning**: Synthetic data can help develop and test machine learning models locally, without pooling real data in a central location.

Overall, while synthetic data has significant promise for privacy, bias reduction, and data augmentation, **proper techniques and careful design** are essential to ensure that it meets the intended goals of utility and privacy.

## Why Use Synthetic Data?

The text highlights three main ways synthetic data is used within machine learning:

1. **Private Data Release**

   - **Development of ML tools**: Organizations share synthetic data with potential partners or researchers so they can develop or compare machine learning models without exposing sensitive real data. The synthetic data must preserve statistical properties needed to evaluate models reliably.
   - **Software testing**: Synthetic data supports system testing and User Acceptance Testing without privacy concerns. Here, it needs to reflect realistic (but not necessarily statistically accurate) structures and formats.
   - **Deploying private ML tools**: Although one could train models entirely on private synthetic data, it often loses key statistical nuances. Typically, better results come from models trained directly on real data with privacy controls integrated into the training process rather than relying solely on synthetic data.

2. **De-biasing**

   - **Reducing or removing bias**: Synthetic data can be generated to remove historical biases in attributes such as gender or race, providing a fairer dataset for training. This can create a consistent approach to fairness across multiple models within an organization.
   - **What-if scenarios**: Synthetic data, generated from carefully defined causal models, can explore alternate realities or interventions (e.g., changing distributions or causal links) to see how the system might behave under different conditions. These techniques introduce model risk and require careful validation.

3. **Data Augmentation**
   - **Data labeling**: Industries rely on vast, accurately labeled data for deep learning models, particularly in computer vision. Synthetic data can cost-effectively supply labeled examples to bolster real datasets and improve model robustness, though privacy is often not the main concern in this specific use case.

In each of these scenarios, synthetic data must strike a balance between utility (realistic, relevant for the intended task) and any privacy or fairness objectives. The success of synthetic data depends heavily on how it is generated, validated, and integrated into broader workflows.

## Privacy in Machine Learning - An Overview

**Summary**

This section provides an overview of privacy in machine learning, emphasizing the risks and defenses involved when sharing or analyzing data:

1. **Privacy Motivation**

   - Individuals consent to data collection under the assumption it will not be used to harm them (e.g., by revealing sensitive health information).
   - Sharing data can foster collaboration (as in open benchmark datasets like MNIST or CIFAR) but also poses risks to personal privacy.

2. **Threat Model Approach**

   - **Membership Inference**: An attacker determines whether a specific individual was part of a dataset (e.g., identifying someone’s involvement in a sensitive clinical study).
   - **Attribute Inference**: An attacker predicts missing attributes (e.g., revealing someone’s smoking status). Although inference is a core goal of machine learning, it can become a privacy violation if the attacker’s predictions are substantially improved by an individual’s inclusion in the dataset.
   - **Reconstruction Attacks**: An attacker attempts to recover entire records (for instance, reconstructing exact data of individuals from aggregate statistics).

3. **Differential Privacy (DP)**

   - **Definition**: DP ensures that the algorithm’s output changes minimally when any one individual’s data is added or removed, limiting the potential privacy harm.
   - **Interpretation**: If a person opts out of the dataset, DP guarantees the algorithm’s output will not change “too much,” thus severely limiting information leakage about that person.
   - **Properties**:
     - _Composability_: Multiple DP operations combine to still maintain DP guarantees.
     - _Resistance to Post-Processing_: Any transformations on DP outputs remain DP.
     - _Bayesian Interpretation_: DP bounds how much posterior beliefs (e.g., about an individual’s presence in a dataset) can change relative to prior knowledge.

4. **Limitations of DP**
   - **Choosing Parameters (ε, δ)**: Selecting the privacy parameters that balance protection and utility is notoriously difficult and context-dependent.
   - **Relaxations**: Variants (e.g., approximate DP, Rényi DP) address practical concerns but can be harder to interpret. Overly conservative assumptions can lower utility by adding too much noise.

Overall, differential privacy is a widely accepted framework for protecting individuals in machine learning systems, but implementing it effectively requires careful design and a context-sensitive choice of privacy parameters.

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

## Data Augmentation

**Summary**

This section discusses **data augmentation** using synthetic data—one of the most successful and widely adopted applications of synthetic data in machine learning.

1. **Motivation and Context**

   - **Data augmentation** is often considered a form of semi-supervised learning, where synthetic examples are added to a real dataset to improve model training.
   - By increasing the effective size of a dataset, synthetic data can serve as a form of **regularization**, helping models generalize better and reducing overfitting.
   - Unlike domains such as **computer vision**, where straightforward transformations (e.g., flips, rotations) can generate new data, **generic tabular data** typically lacks similar structure, making synthetic generation more critical for augmentation.

2. **Basic Principle**

   - The goal is to improve model **generalization** by training on **real plus synthetic** data.
   - Crucially, **synthetic samples must be sufficiently different** from the real training data to offer new information rather than repeating what is already captured in the dataset.

3. **Methods and Techniques**
   - Any **generative model** that can produce realistic-yet-novel samples (e.g., GANs, VAEs) may be used for augmentation.
   - However, simply training a perfect generator (i.e., one that replicates the data distribution too closely) may not always boost performance. A certain “imperfection” or **diversity** in generated samples can be beneficial for improved robustness and generalization.
   - Researchers have proposed various **metrics** to measure diversity in synthetic data (e.g., the distribution-based scores in the GAN literature).

Overall, data augmentation with synthetic data is especially promising for **domains lacking natural transformations** (e.g., tabular datasets), where it can provide new, diverse samples that help models learn more robustly.

## Generative Modeling: An Overview

**Summary**

This text provides an overview of **generative modeling** methods and how they apply across various data types (tabular, time-series, images, audio, and video). It distinguishes **explicit density-based** and **implicit** generative models, examining popular architectures such as **Variational Autoencoders (VAEs)**, **Generative Adversarial Networks (GANs)**, and **Boltzmann Machines**. Below is a brief outline:

---

### 1. Generative Model Taxonomy

- **Explicit Models**: Define a tractable or approximate probability distribution; examples include VAEs and (Restricted) Boltzmann Machines.
- **Implicit Models**: Do not define a density directly but rather learn to **sample** from the target distribution. GANs are the primary example, with a generator-discriminator framework that achieves realistic outputs through adversarial training.

---

### 2. Data-Type-Specific Challenges

1. **Tabular Data**

   - Requires modeling multiple columns of varying data types (continuous, categorical) plus interdependencies.
   - Techniques include **Bayesian networks**, **Gaussian Copulas**, and **GAN-based** methods (with specialized handling of discrete variables).
   - Ensuring valid row-level semantics (e.g., no contradictory values) often requires additional constraints or post-processing.

2. **Time-Series Data**

   - Historically tackled by **autoregressive** models but challenged by non-stationarity and heavy-tailed distributions.
   - Modern methods often use **implicit modeling** (e.g., recurrent GANs) that condition future values on past data.
   - **Signature-based** approaches can reduce dimensionality, leveraging statistics of the path.

3. **Image Generation**

   - Early VAEs sometimes struggled to capture fine details due to pixel-wise loss functions.
   - **GANs** rapidly became a dominant approach, using semantic loss functions better aligned with human perception.
   - Techniques include **Conditional GANs (CGANs)**, **Deep Convolutional GANs (DCGANs)**, **Wasserstein GANs (WGANs)**, and more to improve stability and diversity (avoid mode collapse).

4. **Audio**

   - High temporal resolution demands efficient representations.
   - **WaveNets** (inspired by PixelRNN) directly model raw audio waveforms but can be computationally expensive.
   - Spectrogram-based methods trade off invertibility for reduced complexity.

5. **Video**
   - Viewed as sequences of images with significant inter-frame dependencies.
   - **Unconditional models** attempt to capture coherent objects and movement without external inputs.
   - **Conditional models** use text, audio, or future-frame forecasting tasks to guide video synthesis (e.g., video-to-video translation).

---

### 3. Key Observations & Challenges

- **Balancing Model Complexity and Stability**: Complex models (like GANs) can be powerful but risk training instability and mode collapse.
- **Handling Discrete Attributes**: For tabular data, transforming categorical columns into continuous distributions can lead to inaccuracies or complexity in generation.
- **Scalability**: Generating high-dimensional, multi-modal data (images, videos) requires careful architecture choices to manage training time and memory.
- **Quality vs. Diversity**: Improving realism can sometimes reduce variety in outputs (and vice versa), so advanced methods aim to balance these two aspects.

---

**Overall**, generative modeling has grown dramatically, driven by **GANs** and **VAEs** across many data modalities. While image synthesis is often the showcase, tabular, time-series, audio, and video data each introduce unique challenges requiring specialized architectures and post-processing to ensure **validity**, **stability**, and **quality** of the generated results.

## Messages from Industry/Start-ups

**Summary**

This section summarizes key insights from interviews with various **industry partners and start-ups** working on synthetic data, emphasizing both excitement and caution around the technology:

1. **Emerging Technology**

   - **AI Adoption is Still Maturing**: Organizations are only beginning to integrate advanced AI and ML solutions at scale, making synthetic data—an even newer concept—an area of ongoing research and interest.
   - **Heightened Privacy Demands**: Public concerns over data protection and regulatory pressures make privacy-focused technologies like synthetic data more appealing.

2. **Empirical Evaluations are Crucial**

   - While **differential privacy** provides a strong theoretical foundation, businesses require **practical demonstrations** of privacy defenses (e.g., resistance to real-world attacks).
   - Understanding how privacy parameters (ε, δ) map to **actual risk** is essential for confidence in private synthetic data solutions.

3. **Replacing Real Data?**

   - **Divided Opinions**:
     - Some believe synthetic data will **never fully replace** real data; the final stages of model development or fine-tuning likely require the original dataset for maximum accuracy.
     - Others suggest that, with enough research and methodological improvements, **fully synthetic** solutions could become feasible for many use cases.
   - **Theoretical Nuances**: Impossibility results (e.g., Ullman et al.) argue against universal general-use synthetic data, but relaxations (e.g., matching “most” correlations rather than all) hold promise for many practical scenarios.

4. **Enabling Power of Synthetic Data**
   - **Facilitates Collaboration**: Synthetic data can **circumvent legislative or cross-border data-sharing hurdles**, enabling more efficient collaboration or global deployment of ML models.
   - **Accelerates Development**: Teams can prototype and test models **earlier and more quickly** without waiting on complex data-sharing approvals.
   - Overall, synthetic data can **unlock potential** for broader data access and innovation while aiming to preserve individuals’ privacy.

In essence, industry players see **synthetic data** as a valuable tool to expedite development and handle privacy challenges, but they acknowledge that it may not always supersede real data for final model training. The key is striking the right balance between **practical utility** and **robust privacy**.
