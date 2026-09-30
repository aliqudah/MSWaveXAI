#  MSWaveXAI: Multi-Scale Wavelet Explainable AI for Biomedical Signals

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()

**MSWaveXAI** is a novel, model-agnostic Explainable AI (XAI) framework designed specifically for physiological time-series data. Unlike traditional XAI methods (e.g., LIME, SHAP, Integrated Gradients) that suffer from scale blindness, instability, and sign-inversion artifacts on biosignals, MSWaveXAI operates natively in the wavelet domain. It provides stable, sparse, and physiologically anchored explanations by combining exact Wavelet-Shapley fusion, NNLS sign-locking, and a novel **Morphological Concordance Index (MCI)**.

>  **Associated Paper:** *"Morphologically-Conscious Explainable AI for Biomedical Signals via Multi-Wavelet Shapley Fusion and Physiological Baselines"*  
> 👤 **Authors:** Ali Mohammad Alqudah, Zahra Moussavi  
> 🏫 **Affiliation:** University of Manitoba, Canada

---

## ✨ Key Features

- 🧠 **Exact Wavelet-Shapley Fusion:** Computes game-theoretic band attributions with a novel energy-based fallback to prevent zero-metric degeneracy in perfectly separable tasks (e.g., ECG-VT).
- 🔒 **NNLS Sign-Locked Refinement:** Eliminates gradient dead-zones and sign-inversion pathologies common in gradient-based methods.
-  **Cycle-Spinning Envelopes:** Yields shift-invariant, noise-stable saliency traces with bootstrap 95% Confidence Intervals (CIs).
- 🎯 **Morphological Concordance Index (MCI):** A novel evaluation metric that quantifies the exact Intersection-over-Union (IoU) between XAI attributions and ground-truth physiological landmarks (e.g., QRS complexes, S1/S2 heart sounds, MUAP bursts).
- ⚖️ **Rigorous Model-Agnostic Protocol:** Features an automated 10-classifier, hyperparameter-optimized, stratified $k$-fold CV model-selection loop to eliminate model-dependence bias.
- 📊 **Comprehensive Benchmark:** Evaluated across **11 real-world datasets** (ECG, EEG-Sleep, PPG, PCG, ECG-AF, ECG-VT, ECG-SVE, ECG-Apnea, PPG-HR, ECG-Paced, and EMG).

---

## 📦 Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/MSWaveXAI.git
   cd MSWaveXAI
