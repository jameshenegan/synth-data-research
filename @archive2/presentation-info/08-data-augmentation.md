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
