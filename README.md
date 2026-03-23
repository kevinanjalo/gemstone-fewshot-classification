# Gemstone Few-Shot Classification

Experimental comparison of a Standard CNN versus a Prototypical Network for image-based gemstone classification under data-scarce conditions.

**Course:** DS402.3 – Neural Networks  
**Dataset:** [Gemstones Images Expanded Dataset](https://www.kaggle.com/datasets/lsind18/gemstones-images) (Kaggle)

---

## Overview

Standard deep learning models require large labelled datasets to generalise reliably. In mineral identification, rare gemstone varieties often have only a handful of documented images. This experiment tests whether a Prototypical Network — a metric-based few-shot learning approach — can overcome this limitation using only 5 reference images per novel class.

| Model | Setting | Accuracy |
|---|---|---|
| Standard CNN | Base classes (validation) | 68.8% |
| Standard CNN | Novel classes (unseen) | 0.7% |
| Prototypical Network | 5-way 5-shot (novel classes) | 82.9% ± 1.3% |
| Random Chance | 5-way baseline | 20.0% |

---

## Repository Structure

```
gemstone-fewshot-classification/
├── gemstone_classification.ipynb   # Full experiment notebook (start here)
├── experiment_metrics.json         # All recorded accuracy metrics
├── results_summary.csv             # Summary results table
├── requirements.txt                # Python dependencies
└── README.md
```

---

## How to Run

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/gemstone-fewshot-classification.git
cd gemstone-fewshot-classification
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Download from [Kaggle](https://www.kaggle.com/datasets/lsind18/gemstones-images) and extract so the structure looks like:
```
gemstones/
  Alexandrite/
    img001.jpg
    img002.jpg
  Amethyst/
    ...
```

### 4. Set the dataset path
In Cell 3 of the notebook, update:
```python
DATASET_ROOT = './gemstones'   # point this to your extracted folder
```

### 5. Run all cells in order
The notebook is fully self-contained and runs end to end.

---

## Experiment Design

- **88 classes**, ~50 images per class
- **60 base classes** → used to train CNN and meta-train Prototypical Network
- **28 novel classes** → held out entirely, used only at test time
- **Few-shot setting:** 5-way 5-shot (5 classes, 5 support images each)
- **Test episodes:** 200 randomly sampled episodes on novel classes

---

## Key Findings

The Standard CNN completely fails on unseen novel classes (0.7%), confirming that conventional supervised models cannot generalise beyond their training distribution. The Prototypical Network — given only 5 reference images per novel class — achieves 82.9% accuracy, demonstrating that metric-based few-shot learning is a practical solution for rare gemstone identification.

---

## Citation

If you use this code or results, please cite:

```
[Group Member Names] (2026). Few-Shot Gemstone Classification: A Comparative Study 
of Standard CNN and Prototypical Networks. DS402.3 Neural Networks Assignment, 
[University Name].
GitHub: https://github.com/<your-username>/gemstone-fewshot-classification
```
