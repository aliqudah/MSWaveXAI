#  MSWaveXAI: Multi-Scale Wavelet Explainable AI for Biomedical Signals

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()

**MSWaveXAI** is a novel, model-agnostic Explainable AI (XAI) framework designed specifically for physiological time-series data. Unlike traditional XAI methods (e.g., LIME, SHAP, Integrated Gradients) that suffer from scale blindness, instability, and sign-inversion artifacts on biosignals, MSWaveXAI operates natively in the wavelet domain. It provides stable, sparse, and physiologically anchored explanations by combining exact Wavelet-Shapley fusion, NNLS sign-locking, and a novel **Morphological Concordance Index (MCI)**.

> 📄 **Associated Paper:** *"Morphologically-Conscious Explainable AI for Biomedical Signals via Multi-Wavelet Shapley Fusion and Physiological Baselines"*  
> 👤 **Authors:** Ali Mohammad Alqudah, Zahra Moussavi  
> 🏫 **Affiliation:** University of Manitoba, Canada

---

## ✨ Key Features

-  **Exact Wavelet-Shapley Fusion:** Computes game-theoretic band attributions with a novel energy-based fallback to prevent zero-metric degeneracy in perfectly separable tasks (e.g., ECG-VT).
- 🔒 **NNLS Sign-Locked Refinement:** Eliminates gradient dead-zones and sign-inversion pathologies common in gradient-based methods.
- 🔄 **Cycle-Spinning Envelopes:** Yields shift-invariant, noise-stable saliency traces with bootstrap 95% Confidence Intervals (CIs).
- 🎯 **Morphological Concordance Index (MCI):** A novel evaluation metric that quantifies the exact Intersection-over-Union (IoU) between XAI attributions and ground-truth physiological landmarks (e.g., QRS complexes, S1/S2 heart sounds, MUAP bursts).
- ⚖️ **Rigorous Model-Agnostic Protocol:** Features an automated 10-classifier, hyperparameter-optimized, stratified $k$-fold CV model-selection loop to eliminate model-dependence bias.
- 📊 **Comprehensive Benchmark:** Evaluated across **11 real-world datasets** (ECG, EEG-Sleep, PPG, PCG, ECG-AF, ECG-VT, ECG-SVE, ECG-Apnea, PPG-HR, ECG-Paced, and EMG).

---

## 🛠️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/MSWaveXAI.git
cd MSWaveXAI
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate the environment:

**Windows:**

```bash
.venv\Scripts\activate
```

**Linux/macOS:**

```bash
source .venv/bin/activate
```

### 3. Install the required dependencies

```bash
pip install -r requirements.txt
```

> See the [Requirements](#-requirements) section below for the package list.

---

## 🚀 Quick Start

To run the full benchmark, generate all statistical tables, and produce publication-ready figures, execute the main script:

```bash
python main.py
```

**What to expect:**

* The script will automatically download/curate the 11 benchmark datasets.
* An internet connection is required for datasets hosted by PhysioNet/UCI.
* It will perform 10-classifier cross-validation model selection for each modality.
* It will compute the 8-dimensional XAI benchmark metrics and ablation studies.
* All outputs, including CSV tables and PNG figures, will be saved in:

```text
Paper_Results/
```

---

## 📁 Repository Structure

```text
MSWaveXAI/
│
├── main.py
├── requirements.txt
├── README.md
├── LICENSE
│
├── data/
│   └── ...
│
├── src/
│   └── ...
│
├── Paper_Results/
│   ├── tables/
│   └── figures/
│
└── notebooks/
    └── ...
```

---

## 📊 Datasets

The framework is validated on **11 diverse public biomedical signal datasets**:

| #  | Modality  | Classes | Dataset                                      |
| -- | --------- | ------: | -------------------------------------------- |
| 1  | ECG       |       3 | MIT-BIH Arrhythmia Database                  |
| 2  | EEG-Sleep |       5 | Sleep-EDF Database                           |
| 3  | PPG       |       3 | BIDMC PPG and Respiration Dataset            |
| 4  | PCG       |       2 | PhysioNet/CinC Challenge 2016                |
| 5  | ECG-AF    |       2 | MIT-BIH Atrial Fibrillation Database         |
| 6  | ECG-VT    |       2 | MIT-BIH + CUDB (Ventricular Tachyarrhythmia) |
| 7  | ECG-SVE   |       2 | MIT-BIH + SVDB (Supraventricular Ectopy)     |
| 8  | ECG-Apnea |       2 | Apnea-ECG Database                           |
| 9  | PPG-HR    |       3 | BIDMC-derived Heart Rate Classification      |
| 10 | ECG-Paced |       2 | MIT-BIH (Paced vs. Normal Beats)             |
| 11 | EMG       |       2 | UCI sEMG for Basic Hand Movements            |

---

## 📈 Evaluation Metrics

MSWaveXAI evaluates explanation quality using a composite **Explanation Quality Index (EQI)** that aggregates multiple complementary XAI metrics.

### Faithfulness

* **Deletion AUC:** Measures the change in model prediction as the most important features are progressively removed.
* **Insertion AUC:** Measures the recovery of model prediction as important features are progressively introduced.

### Stability

* **Stability:** Mean cosine similarity between attribution maps generated from the original signal and Gaussian-noise-perturbed signals.

### Sparsity

* **Gini Coefficient:** Quantifies the concentration of attribution values and the sparsity of the explanation.

### Localization

* **Localization IoU:** Measures overlap between highly attributed regions and predefined physiological windows.

### Morphological Concordance

* **Morphological Concordance Index (MCI):**
  A novel metric measuring the overlap between the top-20% attributed regions and algorithmically identified physiological landmarks.

### Comprehensiveness and Sufficiency

* **Comprehensiveness:** Quantifies the reduction in model confidence after removing the most important features.
* **Sufficiency:** Measures how much predictive information is retained by the most important features alone.

---

## 📜 Citation

If you use **MSWaveXAI** in your research, please cite our work:

```bibtex
@article{alqudah_mswavexai,
  title   = {MSWaveXAI: ...},
  author  = {Alqudah, Ali Mohammad and Moussavi, Zahra},
  journal = {...},
  year    = {2026}
}
```

> Replace the placeholder bibliographic information above with the final publication details once available.

---

## 📝 Requirements

<details>
<summary>Click to view <code>requirements.txt</code></summary>

```text
numpy
scipy
pandas
scikit-learn
matplotlib
seaborn
shap
PyWavelets
wfdb
tqdm
joblib
```

</details>

---

## ⚠️ Limitations & Future Work

### ECG-SVE

The current sparse, sign-locked attribution map concentrates heavily on the QRS complex, while some classifiers exploit subtle, distributed P-wave morphology.

Future iterations will incorporate:

* Multi-lead ground truth.
* Adaptive sparsity constraints.
* More detailed morphological priors.

### Ground Truth

Localization metrics currently rely on algorithmic physiological priors, such as:

```python
scipy.signal.find_peaks
```

A formal clinician reader study is planned for future validation.

### Runtime

The exact Shapley computation has complexity:

$$
O(2^J)
$$

making it slightly slower than Occlusion (approximately **0.42 s per explanation**). However, it remains suitable for:

* Offline clinical review.
* Batch auditing.
* Large-scale XAI benchmarking.

---

## 📬 Contact

For questions, collaborations, or bug reports, please open an issue in this repository or contact:

**Ali Mohammad Alqudah**
[alqudaha@myumanitoba.ca](mailto:alqudaha@myumanitoba.ca)

**Zahra Moussavi**
[Zahra.Moussavi@umanitoba.ca](mailto:Zahra.Moussavi@umanitoba.ca)

---

## 📄 License

This project is licensed under the **MIT License**. See the [`LICENSE`](LICENSE) file for details.

---

## ⭐ Acknowledgments

We acknowledge the maintainers of the public biomedical signal databases used in this benchmark, including PhysioNet, UCI, and the respective dataset contributors.

