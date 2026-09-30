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
Create a virtual environment (recommended):
bash

12
Install the required dependencies:
bash

1
(See the requirements.txt section below for the exact package list).
🚀 Quick Start
To run the full benchmark, generate all statistical tables, and produce publication-ready figures, simply execute the main script:
bash

1
What to expect:
The script will automatically download/curate the 11 benchmark datasets (requires an internet connection for PhysioNet/UCI).
It will perform the 10-classifier CV model selection for each modality.
It will compute the 8-dimensional XAI benchmark metrics + ablation studies.
All outputs (CSV tables and PNG figures) will be saved in the Paper_Results/ directory.
📂 Repository Structure
text

123456789101112131415
📊 Datasets
The framework is validated on 11 diverse, public biomedical signal datasets:
ECG (3-class): MIT-BIH Arrhythmia Database
EEG-Sleep (5-class): Sleep-EDF Database
PPG (3-class): BIDMC PPG and Respiration Dataset
PCG (2-class): PhysioNet/CinC Challenge 2016
ECG-AF (2-class): MIT-BIH Atrial Fibrillation Database
ECG-VT (2-class): MIT-BIH + CUDB (Ventricular Tachyarrhythmia)
ECG-SVE (2-class): MIT-BIH + SVDB (Supraventricular Ectopy)
ECG-Apnea (2-class): Apnea-ECG Database
PPG-HR (3-class): BIDMC-derived Heart Rate classification
ECG-Paced (2-class): MIT-BIH (Paced vs. Normal beats)
EMG (2-class): UCI sEMG for Basic Hand Movements
📈 Evaluation Metrics
MSWaveXAI is evaluated using a composite Explanation Quality Index (EQI), aggregating:
Deletion / Insertion AUC: Faithfulness to model predictions.
Stability: Mean cosine similarity under Gaussian noise perturbations.
Sparsity: Gini coefficient of the attribution map.
Localization IoU: Overlap with predefined physiological windows.
Morphological Concordance Index (MCI): Our novel metric measuring top-20% attribution overlap with algorithmic physiological landmarks.
Comprehensiveness / Sufficiency: Predictive mass of the top attributed features.
📜 Citation
If you use MSWaveXAI in your research, please cite our work:
bibtex

1234567
📝 Requirements
<details>
<summary>Click to view <code>requirements.txt</code></summary>

text

12345678
</details>

⚠️ Limitations & Future Work
ECG-SVE: The current sparse, sign-locked map concentrates heavily on the QRS complex, while some classifiers exploit subtle, distributed P-wave morphology. Future iterations will incorporate multi-lead ground truth and adaptive sparsity constraints.
Ground Truth: Localization metrics currently rely on algorithmic physiological priors (e.g., scipy.signal.find_peaks). A formal clinician reader study is planned for future validation.
Runtime: The exact Shapley computation is 
O
(
2
J
)
O(2 
J
 ), making it slightly slower than Occlusion (~0.42s per explanation), but highly suitable for offline clinical review and batch auditing.
📬 Contact
For questions, collaborations, or bug reports, please open an issue in this repository or contact:
Ali Mohammad Alqudah – alqudaha@myumanitoba.ca
Zahra Moussavi – Zahra.Moussavi@umanitoba.ca
📄 License
This project is licensed under the MIT License – see the LICENSE file for details.
