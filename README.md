# Mushroom Classification Using Machine Learning

## 1. Overview
A beginner-friendly machine learning project that predicts whether a mushroom is **edible** or **poisonous** from its physical characteristics. It compares two classifiers: **Decision Tree** and **K-Nearest Neighbors (KNN)**. Built with Python, scikit-learn and Jupyter Notebook.

## 2. Problem Statement and Objective
Eating the wrong wild mushroom can be fatal. The objective is to build and compare two simple models that learn from labelled examples to classify mushrooms as edible or poisonous, and to practise data preparation, model building and evaluation (accuracy, confusion matrix, precision, recall, F1-score).

## 3. Dataset
- **Original source:** UCI Machine Learning Repository, *Mushroom* dataset: https://archive.ics.uci.edu/dataset/73/mushroom
- **CSV used in this project:** the commonly used `mushrooms.csv` version (columns `class`, `cap-shape`, `cap-surface`, ...), obtained from this public GitHub mirror: https://github.com/kcncell/Mushroom-dataset
- **Direct download link:** https://raw.githubusercontent.com/kcncell/Mushroom-dataset/master/mushrooms.csv
- **Why a mirror:** the UCI site was not reachable from the environment where this project was built, so the mirror was used. The file was checked: 8,124 rows, 23 columns, with the same class counts as the UCI dataset (4,208 edible, 3,916 poisonous).

**Download instructions (any one option):**
1. Use the `mushrooms.csv` file included in this project folder (nothing to do), **or**
2. Download it manually from the direct link above and save it as `mushrooms.csv` next to the notebook, **or**
3. Run the notebook without the file. It downloads the CSV automatically from the mirror (internet required).

Optional terminal command:
```bash
curl -L -o mushrooms.csv https://raw.githubusercontent.com/kcncell/Mushroom-dataset/master/mushrooms.csv
```

## 4. Features and Target
- **Target:** `class` (`e` = edible, `p` = poisonous). Encoded as 0 = edible, 1 = poisonous.
- **Features (22, all categorical):** `cap-shape`, `cap-surface`, `cap-color`, `bruises`, `odor`, `gill-attachment`, `gill-spacing`, `gill-size`, `gill-color`, `stalk-shape`, `stalk-root`, `stalk-surface-above-ring`, `stalk-surface-below-ring`, `stalk-color-above-ring`, `stalk-color-below-ring`, `veil-type`, `veil-color`, `ring-number`, `ring-type`, `spore-print-color`, `population`, `habitat`.
- **Missing values:** `stalk-root` uses `?` for 2,480 unknown values. They are converted to `NaN` and filled with a `"missing"` category inside the pipeline.

## 5. Technologies and Libraries
Python 3, Jupyter Notebook, pandas, numpy, matplotlib, seaborn, scikit-learn.

## 6. Project File Structure
```
.
├── Mushroom_Classification_ML.ipynb   # main notebook (executed, with outputs)
├── mushrooms.csv                      # dataset (mirror of UCI Mushroom data)
├── requirements.txt                   # required libraries
└── README.md                          # this file
```

## 7. Installation and Setup
```bash
# (optional) create a virtual environment
python -m venv venv
venv\Scripts\activate          # Windows
# source venv/bin/activate     # macOS / Linux

pip install -r requirements.txt
```

## 8. How to Run
**Jupyter Notebook**
```bash
jupyter notebook
```
Open `Mushroom_Classification_ML.ipynb`, then choose **Kernel > Restart & Run All**.

**Google Colab**
1. Go to https://colab.research.google.com and choose **File > Upload notebook**.
2. Upload `Mushroom_Classification_ML.ipynb` (optionally also `mushrooms.csv` using the Files panel on the left).
3. If you do not upload the CSV, the notebook downloads it automatically.
4. Choose **Runtime > Run all**. All libraries are already installed in Colab.

## 9. Evaluation Metrics
- **Accuracy:** share of correct predictions on the test set.
- **Confusion matrix:** actual vs predicted counts (Edible / Poisonous).
- **Precision, recall, F1-score:** per-class performance from the classification report.
- Both models are tested on the same stratified 80/20 split (`random_state=42`). Preprocessing is fitted on training data only, through scikit-learn pipelines, to avoid data leakage.

## 10. Actual Results and Conclusion
The notebook was executed successfully (scikit-learn, pandas, seaborn) and produced these test-set results (1,625 test mushrooms):

| Model | Test Accuracy | Poisonous predicted as Edible |
|---|---|---|
| Decision Tree | 1.0000 | 0 |
| KNN (k=5) | 1.0000 | 0 |

**Conclusion:** Both models classified every test mushroom correctly, so neither performed better on this test set. This happens because the dataset's features, especially `odor`, separate the two classes very clearly. Exact numbers come from running the notebook, so rerunning it with a different split or library version could give slightly different results.

## 11. Limitations and Safety Disclaimer
- The dataset is small, old and covers limited mushroom families, so results may not transfer to other mushrooms.
- Features are expert descriptions, not photos, and real-world observations can be wrong or incomplete.
- Only one train-test split and default settings were used (no cross-validation or tuning). Perfect accuracy on one split does not guarantee perfect performance on new data.
- **Safety disclaimer:** This project is for educational purposes only. **Never use this model, or any similar program, to decide whether a wild mushroom is safe to eat.** Always consult a qualified expert.
