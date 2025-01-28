# 30 years of synthetic data

April, 2023
Drechsler

Over the past 30 years, **synthetic data** has evolved into a critical method for protecting confidentiality while enabling broader access to sensitive microdata. Below is an overview of the field’s development and key concepts:

1. **Historical Context and Motivation**

   - Initially proposed by Rubin (1993) and Little (1993) as an adaptation of multiple imputation, synthetic data replaces original values (fully or partially) with model-based draws.
   - Early milestones include U.S. Federal Reserve applications in 1997, the U.S. Census Bureau’s large-scale SIPP Synthetic Beta in 2007, and numerous national statistical offices adopting the approach.

2. **Statistical vs. Computer Science Approaches**

   - **Statistical**: Emphasizes valid inference, adapting multiple imputation combining rules (e.g., Reiter, 2003). Methods include sequential regression, Bayesian mixtures, and custom modeling for different data types.
   - **Computer Science**: Historically focused on anonymity measures (k-anonymity, l-diversity). With the rise of **differential privacy (DP)**, new frameworks emerged (e.g., PrivBayes, DP-GAN). Machine learning methods—like GANs and autoencoders—help generate synthetic datasets that maintain useful statistical properties while limiting disclosure risks.

3. **Combining Rules for Valid Inference**

   - **Fully Synthetic**: All records replaced. Special variance estimators (e.g., from Raghunathan et al., 2003) account for the extra sampling step.
   - **Partially Synthetic**: Only certain sensitive values replaced. Its variance formulas (Reiter, 2003) avoid negative estimates but differ from the fully synthetic approach.
   - **Alternative Estimators** (Raab et al., 2016) allow valid inference from a single synthetic dataset, which can reduce disclosure risk.

4. **Taxonomy of Methods**

   - **Sequential vs. Joint Modeling**: Synthesizing one variable at a time vs. modeling entire distributions at once.
   - **Parametric vs. Machine Learning**: Traditional statistical models vs. automated, high-dimensional methods (random forests, GANs, etc.).
   - **Formal Privacy Guarantees vs. No Formal Guarantees**: Whether the method provides mathematically rigorous privacy (e.g., DP).
   - **Extensions of MI Approaches**: Multi-stage synthesis, subsampling before synthesis, and handling missing data jointly with disclosure protection.

5. **Differentially Private Data Synthesis**

   - DP imposes a strict bound on how much a single record can affect published outputs, offering strong formal guarantees.
   - Methods include adding noise to margins (e.g., MWEM), Bayesian networks (PrivBayes), copulas (DPCopula), and DP-enhanced GANs.

6. **Utility Evaluation**

   - **Global Metrics**: Distances (Kullback-Leibler, Hellinger) or propensity score measures (pMSE) that compare real vs. synthetic data in aggregate.
   - **Outcome-Specific Metrics**: Compare specific analyses (e.g., regression coefficients, ML accuracy) on real vs. synthetic datasets.
   - **Fit-for-Purpose**: Graphical checks, plausibility checks, and goodness-of-fit statistics (like chi-square, Kolmogorov-Smirnov) to diagnose modeling quality and identify problematic variables.

7. **Risk Assessment**
   - **Fully Synthetic**: No direct one-to-one link with original records, but potential leakage of sensitive information remains (e.g., exact replication of records, membership attacks).
   - **Partially Synthetic**: One-to-one correspondence persists for replaced records, so re-identification metrics (e.g., expected match risk, true/false match rates) can be calculated.

In summary, the field of synthetic data has grown from early theoretical ideas to a broad spectrum of practical tools and frameworks. Researchers and practitioners balance **utility** (ensuring analyses on synthetic data mirror those on real data) with **confidentiality** (minimizing risks of identifying or inferring sensitive information). Ongoing innovations in machine learning, differential privacy, and model-based synthesis continue to shape the future of synthetic data generation.

## Abstract

In an increasingly data-driven world, there is growing tension between the benefits of broad data availability for research, policy, and industry applications on the one hand, and the need to protect confidentiality and privacy on the other. Traditional techniques (such as swapping and suppression) have become insufficient in light of advancing computational power and the proliferation of publicly available data.

A key emerging solution is the use of **synthetic data**—artificially generated datasets that preserve many statistical properties of the original data without directly revealing sensitive information. Originating from ideas by Rubin and Little in the early 1990s, synthetic data methods were initially motivated by the concept of multiple imputation (filling in missing values), but have expanded significantly over the last three decades. Separate strands of development arose within statistics (focusing on valid inference and uncertainty assessment) and computer science (focusing on creating training data for machine learning).

These approaches share the goal that analyses performed on synthetic data should produce results similar to those that would have been obtained with real data, while reducing the risk of disclosure. Applications now span government agencies, health research (including synthetic patient and electronic health record data), and various industrial contexts (ranging from autonomous driving to environmental monitoring). As synthetic data methods gain momentum, researchers continue to refine approaches for balancing utility and privacy, measuring disclosure risk, and potentially enhancing usability through verification servers.

## A Brief History

### The Statistical Approach

**Origins and Early Development**

- The concept of releasing _synthetic data_ for disclosure protection dates back to **Rubin (1993)**, who proposed adapting his multiple imputation framework to replace original records entirely with data imputed from a model.
- **Little (1993)** introduced the idea of _partially synthetic_ datasets, whereby only high-risk or sensitive values are replaced, striking a balance between privacy and analytical usefulness.
- **Fienberg (1994)** offered a related approach—releasing bootstrap samples from smoothed estimates of the empirical distribution.

**Methodological Foundations**

- Around a decade later, **Raghunathan et al. (2003)** and **Reiter (2003)** formalized how to draw valid inferences from fully and partially synthetic data, adapting the combining rules from multiple imputation for nonresponse.
- Subsequent work (e.g., **Reiter & Kinney, 2012**; **Raab et al., 2016**) refined these methods, clarifying differences in how model parameters are drawn for partial versus full synthesis and providing guidance for scenarios with a single synthetic dataset.

**Key Applications**

- **Earliest Use (1997):** The U.S. Federal Reserve Board replaced high-disclosure-risk monetary values in the Survey of Consumer Finances (Kennickell, 1997).
- **Complex Linked Data:** Abowd & Woodcock demonstrated the feasibility with French longitudinal data; later, the U.S. Census Bureau released the _SIPP Synthetic Beta_ (2007), a large-scale synthetic product linking survey data with administrative records.
- **OnTheMap** used synthetic data with formal privacy guarantees (a variant of differential privacy).
- **Further Major Products:**
  - _Synthetic Longitudinal Business Database_ (U.S. Census Bureau)
  - Synthetic data for the _American Community Survey (ACS)_
  - Maryland Longitudinal Data System Center’s _Synthetic Data Project_
- **International Adoption:**
  - Statistics New Zealand’s _Synthetic Unit Record Files_ (SURFs)
  - German Institute for Employment Research’s partial synthesis of its Establishment Panel
  - Scottish Longitudinal Study providing synthetic extracts for external researchers
  - Statistics Netherlands’ synthetic version of EU-SILC for training and code development
  - Statistics Canada’s hackathon datasets (2020)

**Recent Directions**

- Ongoing projects include synthetic tax data (Urban Institute & IRS), and initiatives by the Australian Bureau of Statistics to broaden microdata access.
- Methodological advances address challenges like synthesizing business data, handling nested structures, preserving additive constraints, protecting geospatial data, and accommodating complex survey designs.

Overall, the field has progressed from early theoretical proposals to widespread practical applications in government, research, and industry, all aiming to provide broader data access while preserving confidentiality.

### The Computer Science Approach

Traditionally, computer science literature on data privacy focused on standards like _k_-anonymity, _l_-diversity, and _t_-closeness, which primarily address how the _released data themselves_ must look to prevent re-identification. Synthetic data—which do not neatly fit these standards—drew relatively little attention until the advent of **differential privacy (DP)** (Dwork et al., 2006). By shifting the focus from the data to the _mechanism_ generating the data, DP opened the door to synthetic data solutions that satisfy formal privacy guarantees.

Early work on **differentially private synthetic data** includes Barak et al. (2007) (using Fourier transformations for contingency tables) and other studies (e.g., Eno & Thompson, 2008; Blum et al., 2011). These were soon followed by methods integrating statistical modeling with DP (Abowd & Vilhuber, 2008; Machanavajjhala et al., 2008; Charest, 2011). Meanwhile, **Generative Adversarial Networks (GANs)**, introduced by Goodfellow et al. (2014), propelled synthetic data research—initially for images, then adapted to **microdata** (e.g., medGAN, CTGAN). Outside GAN-based approaches, other techniques rely on Bayesian networks (PrivBayes), copulas (DPCopula), or autoencoders.

Practical deployments of differentially private synthetic data include **OnTheMap** (Machanavajjhala et al., 2008), which uses a relaxed form of DP, and the **2020 Decennial Census** in the U.S., whose “TopDown” algorithm can be viewed as producing synthetic microdata from noisy counts. Broader interest in these approaches is reflected in events like the **NIST Differential Privacy Synthetic Data Challenge** (2018–2019), where participants tested diverse strategies (often relying on Bayesian networks or marginal-preserving methods). Beyond microdata, computer science researchers apply GANs to generate realistic synthetic medical images and records—further illustrating the rapidly expanding use of synthetic data under formal privacy frameworks.

## Obtaining valid inferences for the MI inspired approaches

Rubin’s original idea to create synthetic data was inspired by multiple imputation (MI) for nonresponse. Although similar, two major differences from MI require adjusted combining rules for analyzing synthetic datasets:

1. **Fully Synthetic Data**

   - All records are replaced (or drawn from a model for a new sample).
   - The established combining rules (Raghunathan et al., 2003) must account for this extra sampling step.
   - The usual variance formula can become negative, prompting a modified approach (Reiter, 2002) that is always nonnegative but can slightly overestimate variance.

2. **Partially Synthetic Data**

   - Only certain records (often high-risk or sensitive) are replaced.
   - Combining rules (Reiter, 2003) differ because the model uses the full dataset to create synthetic values.
   - Unlike the fully synthetic case, the variance estimator here cannot be negative.

3. **Alternative Variance Estimator for Fully Synthetic Data**
   - In practice, researchers often skip Rubin’s two-step sampling procedure and use only the observed dataset to build the synthesis model.
   - This approach can be treated like an “extreme” form of partially synthetic data, so partial-synthesis combining rules still work.
   - Raab et al. (2016) propose a variance formula based solely on the “within-imputation” variance.
     - It never becomes negative.
     - It has less variability compared to the traditional fully synthetic formula.
     - It permits valid inferences from a single synthetic dataset (important for reducing disclosure risk).

Overall, these combining rules ensure valid inferences from synthetic data, balancing ease of implementation and protection against disclosure.

## A taxonomy of synthetic data approaches

Synthetic data methods are diverse, making it challenging to adopt a single taxonomy. Beyond distinguishing between **statistical (multiple-imputation-inspired)** and **computer-science-oriented** approaches, three additional classification schemes are useful:

1. **Sequential vs. Joint Modeling**

   - **Sequential Modeling**: Synthesizes each variable in turn, conditioning on previously synthesized or original variables. This allows flexibility in choosing a different model for each variable (e.g., parametric or machine learning).
   - **Joint Modeling**: Directly models the entire joint distribution of the data at once. Traditional versions assumed simple distributions (e.g., multivariate normal), but newer methods include more flexible mixture models, Bayesian network approaches, and GAN-based techniques.

2. **Parametric vs. Machine Learning-Based**

   - **Parametric**: Relies on specified statistical models, which may struggle with large numbers of variables or complex interactions.
   - **Machine Learning**: Techniques like random forests, CART, Support Vector Machines, or neural networks “let the data speak” by automatically capturing interactions. They also avoid collinearity and perfect prediction issues common in large datasets.

3. **Formal Privacy Guarantees vs. No Formal Guarantees**
   - Some methods, especially in computer science (e.g., differential privacy frameworks), explicitly include privacy parameters and formal proofs of disclosure risk.
   - Other methods rely on informal risk assessments and do not provide strict privacy guarantees.

A further **fourth category** includes **extensions of the multiple-imputation (MI) approach**, which might require specialized inferential procedures beyond the standard formulas. For example:

- Jointly handling missing data and disclosure risk with two-stage synthesis.
- Using subsampling before synthesis, potentially improving utility by fitting models on the full population while only releasing a synthetic sample.

Finally, the **computer-science approaches** often leverage:

- **Generative Adversarial Networks (GANs)**, which use two neural networks (generator and discriminator) in an adversarial setup. Variations include Wasserstein GANs (WGAN) and Causal-TGAN.
- **Variational Autoencoders (VAEs)**, featuring encoder and decoder networks (plus a discriminator) for learning latent representations and reconstructing data.

All of these methods aim to produce synthetic datasets that protect privacy while maintaining as much analytical utility as possible.

## Differential Private Data Synthesis

**1. Differential Privacy (DP) Basics**

- DP (Dwork et al., 2006) imposes a strict bound on how much one individual record can affect an output’s probability distribution.
- In simple terms, it ensures that an observer cannot determine whether any single individual’s data was used in generating the published result.
- Large organizations (e.g., Apple, Google, Microsoft, US Census Bureau) have adopted DP for some of their data products.

**2. Advantages of Differentially Private Synthetic Data**

- DP is _immune to post-processing_: any subsequent operation on a DP output remains DP.
- Thus, researchers can analyze or share _differentially private synthetic data_ freely without added disclosure risk.

**3. Approaches to Differentially Private Synthetic Data**

- **Marginal Distributions**: Adding noise to one-, two-, or three-way margins (e.g., McKenna et al. 2019, Liu et al. 2021).
- **Bayesian Networks**: For instance, PrivBayes (Zhang et al. 2017) and PrivMRF (Cai et al. 2021) model variable correlations.
- **Game-Based Optimization**: Techniques like MWEM (Hardt et al. 2012) optimize specific queries under DP guarantees.
- **Copula Functions**: DPCopula (Li et al. 2014) uses copulas to capture dependencies.

**4. DP in GANs**

- **Generative Adversarial Networks (GANs)** increasingly incorporate DP by adding noise and gradient clipping during training.
- Only the discriminator network typically needs DP modifications; the generator never directly sees raw data.
- Prominent examples include methods by Beaulieu-Jones et al. (2019), Xie et al. (2018), and Yoon et al. (2019), often extending WGANs or using frameworks like PATE (Papernot et al. 2018).
- Neunhoeffer et al. (2021) propose combining multiple DP-trained generators to improve the utility of the final synthetic dataset.

Overall, differentially private synthetic data aim to preserve analytical utility while providing _formal_ and _rigorous_ privacy guarantees.

## Utility Evaluation

Researchers use **utility metrics** to assess how well synthetic data preserve analytical validity compared to the original data. These measures fall into three broad categories:

1. **Global Utility Metrics**

   - Compare original and synthetic datasets on an aggregated level, often without assuming a particular analysis.
   - Common approaches include **distance measures** (e.g., Kullback-Leibler, Hellinger) and **propensity-score-based** methods.
   - A popular example is **pMSE** (propensity mean squared error), which measures how effectively a combined model can distinguish between real and synthetic records. Smaller values generally imply higher similarity.
   - However, these metrics can be sensitive to model specification (e.g., how the propensity model is built) and may not always reflect performance for specific analyses.

2. **Outcome-Specific Utility Measures**

   - Directly evaluate how well the synthetic data replicate particular statistical or machine learning results.
   - Examples include plotting estimates (e.g., regression coefficients) from original vs. synthetic data, checking **confidence interval overlaps**, or comparing **ML performance** (accuracy, F1 scores) on a shared test set.
   - These methods reveal how well synthetic data support specific analyses of interest.

3. **Fit-for-Purpose Measures**
   - Provide a **first diagnostic** for potential issues in the synthetic dataset.
   - **Graphical checks** (e.g., side-by-side distributions, contour plots) highlight differences in marginal or conditional distributions.
   - **Plausibility checks** look for clearly impossible values or relationships (e.g., negative ages, overly large changes in turnover).
   - **Goodness-of-fit metrics** (e.g., Kolmogorov-Smirnov, chi-square statistics) quantify how closely the synthetic data match the original on selected features.
   - These should not be used for formal hypothesis tests (original and synthetic are not independent), but rather as guides to compare different synthesis strategies or identify problematic variables.

In practice, many of these measures are **highly correlated**, so using just one or two well-chosen metrics (plus graphical checks) often suffices to gauge the synthetic data’s overall quality.

## Risk Assessment

Assessing disclosure risk differs substantially between **fully** and **partially** synthetic datasets:

1. **Fully Synthetic Data**

   - No one-to-one link exists between original and synthetic records (the synthetic dataset can even be a different size).
   - **Direct re-identification metrics** (like matching records) are less meaningful. However, fully synthetic data can still leak sensitive information, especially if the synthesizer “overfits” and replicates real records.
   - Proposed risk measures include:
     - **Counting unique matches** of records in synthetic vs. original data (mostly addresses perceived risk).
     - **Distances** between synthetic and original records (although what constitutes “high risk” is not always clear).
     - **Equivalence-class-based measures** (e.g., WEAP, TCAP) that consider “key” and “target” variables.
     - **Membership-attack analyses**, which investigate whether someone can learn if a specific individual is in the original data (of special concern for sensitive populations).
     - **Posterior-based approaches** (e.g., Reiter et al. 2014), which assess how much an attacker’s knowledge of specific attributes can be refined after seeing the synthetic data.
   - In practice, **quantifying** these risks in realistic, high-dimensional scenarios remains challenging, and more research is needed.

2. **Partially Synthetic Data**
   - Some original attributes remain; each synthetic record corresponds to exactly one real record.
   - **Re-identification risk** can be calculated by estimating the probability that an attacker correctly matches a synthetic record to a real target.
   - Key steps (Reiter & Mitra 2009; Drechsler & Reiter 2010):
     1. Assume the intruder has external knowledge about one target’s “key” variables.
     2. For any synthesized attributes, simulate plausible values.
     3. Use a matching algorithm (e.g., nearest neighbor) to compute the probability that a synthetic record matches the attacker’s target.
     4. Summarize probabilities into metrics such as **expected match risk**, **true match rate**, and **false match rate**.
   - Extensions exist for cases where an intruder is unsure whether the target is even in the dataset (handling sampling uncertainty).

Overall, **full and partial synthesis** each require **different risk frameworks**. While partial synthesis can be evaluated using re-identification-based methods, fully synthetic data demand alternative approaches that focus on potential “leakage” of underlying distributions and membership information.
