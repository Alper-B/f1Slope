# Resting-State 1/f Neural Noise & Cross-Sectional Cohort Confounds (MPI-LEMON)

This repository contains an MNE-Python and `specparam` (FOOOF) / IRASA pipeline analyzing resting-state Eyes-Closed EEG ($N = 182$) and fluid intelligence (LPS-2) from the open-access **MPI-LEMON** cohort.

## Key Findings (Aligned with Crespo-García et al., 2026)

1. **Non-Linear Age Trajectory of the $1/f$ Exponent:** Parsing continuous 5-year age brackets reveals that $1/f$ aperiodic flattening occurs steeply during young adulthood (20–40 years: Global $r = -0.28, p = 0.0018$; Parietal $r = -0.31, p = 0.0005$; Occipital $r = -0.30, p = 0.0008$) but plateaus in older adulthood (55–80 years: Global $r = -0.09, p = 0.49$). Sex shows no effect on the $1/f$ exponent ($p = 0.52$).
2. **Simpson's Paradox in Cross-Sectional Cognitive Correlations:** While a naive pooled regression across all subjects suggests that steeper $1/f$ slopes predict higher fluid intelligence ($R^2 = 0.1315, p < 0.0001$), controlling for age cohort in a multiple regression completely eliminates the effect ($\beta = 0.22, p = 0.858$; within-Young $r = 0.01$, within-Old $r = 0.01$). This illustrates how cross-sectional designs can conflate generational/cohort differences with direct neurophysiological links.

![MPI-LEMON Cam-CAN Alignment] (see figures folder)

## Pipeline Features
* **Spectral Parameterization (`specparam` / `FOOOF`):** Evaluates both `fixed` and `knee` aperiodic modes (2–40 Hz, 2-s Hamming windows) alongside regional 10–20 cortical lobe topographies.
* **IRASA Comparison:** Includes a pure SciPy implementation of Irregular Resampling Auto-Spectral Analysis (Wen & Liu, 2016) to benchmark non-parametric $1/f$ slope estimation against Gaussian peak parameterization.
* **Periodic Peak Extraction:** Isolates aperiodic-adjusted Center Frequency (CF) and Power (PW) across Theta (4–8 Hz), Alpha (8–13 Hz), and Beta (15–30 Hz) bands.
