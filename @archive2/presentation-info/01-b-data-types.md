### Data-Type-Specific Challenges

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
