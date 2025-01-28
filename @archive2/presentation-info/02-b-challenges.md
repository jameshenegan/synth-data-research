3. **Challenges**

   - **No Automatic Privacy**: Simply generating data with standard methods (like GANs) does not guarantee privacy—models can memorize and inadvertently reveal real examples.
   - **No Automatic Bias Mitigation**: Off-the-shelf synthetic data generation can perpetuate existing biases if not explicitly addressed.
   - **Quality and Realism Trade-Off**: There is often tension between data realism (for utility) and privacy protection.

4. **Key Questions**

   1. _Can synthetic data be used in place of real data to do the same tasks (training models, hypothesis testing, data analysis)?_
      - Yes in principle, but specialized methods (e.g., Bayesian updates for model parameters, bias-correction strategies) often improve accuracy when dealing with synthetic data.
   2. _Can synthetic data be treated exactly like real data (e.g., linking records from different datasets)?_
      - Linking different synthetic datasets independently generated from real data can break 1-to-1 correspondence across records. Specialized approaches—or regenerating a single, joint synthetic dataset—may be needed.

### 3. Key Observations & Challenges

- **Balancing Model Complexity and Stability**: Complex models (like GANs) can be powerful but risk training instability and mode collapse.
- **Handling Discrete Attributes**: For tabular data, transforming categorical columns into continuous distributions can lead to inaccuracies or complexity in generation.
- **Scalability**: Generating high-dimensional, multi-modal data (images, videos) requires careful architecture choices to manage training time and memory.
- **Quality vs. Diversity**: Improving realism can sometimes reduce variety in outputs (and vice versa), so advanced methods aim to balance these two aspects.
