# Phishing Detection Framework using Dynamic Classifier Selection (DCS) and LIME

**Author:** Nivesh Kumar Gupta  
**Degree:** M.Tech in Information and Cyber Security  
**Institution:** ABV-Indian Institute of Information Technology and Management (IIITM), Gwalior

---

## 1. Project Overview

This research proposes a **client-side, complexity-aware** phishing detection framework. Traditional static models struggle with the structural diversity of modern phishing pages. This work addresses that limitation by:

1. **Quantifying Webpage Complexity** – Automatically categorizing webpages into *Simple*, *Medium*, and *Hard* tiers based on DOM feature density.
2. **Dynamic Selection (DCS/DES)** – Selecting the most competent classifier for each individual webpage according to its local competence.
3. **Explainable AI (XAI)** – Using LIME to provide transparent explanations of the model’s decisions.

---

## 2. Methodology

### Phase 1: Feature Extraction
Eleven lightweight structural features are extracted from rendered HTML, CSS, and JavaScript (no external queries).

### Phase 2: Complexity Categorization
A complexity score is computed using Min-Max normalized features. Pages are divided into three equal quantiles:
- **Simple**
- **Medium**
- **Hard**

### Phase 3: Dynamic Selection Modeling
- **Base Classifiers:** Random Forest, XGBoost, Logistic Regression, KNN, MLP
- **DCS methods:** OLA, LCA, Rank, MCB
- **DES methods:** KNORA-E, KNORA-U, DES-P, DES-KNN

### Phase 4: Interpretability
LIME is applied to explain individual predictions, highlighting influential features such as hidden elements and script patterns.

---

## 3. Repository Structure

Phishing-Detection-Framework/
├── data/
│   ├── raw/                  # Instructions for downloading the original dataset
│   └── processed/            # Cleaned and categorized feature files
├── notebooks/
│   ├── 01_Feature_Extraction_and_Cleaning.ipynb
│   ├── 02_Complexity_Categorization.ipynb
│   └── 03_Models_Implementation_and_LIME.ipynb
├── requirements.txt
└── README.md


---

## 4. Installation and Setup

### Prerequisites
* Python 3.8 or higher
* Git

### Installation Steps

1. Clone the repository:
```bash
git clone https://github.com/NiveshGupta123/Phishing-Detection-Framework.git
cd Phishing-Detection-Framework
```

2.  Install required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

---

## 5. Usage & Execution Instructions

### IMPORTANT: Before Running
1. Always check the data path variables inside the notebooks.
2. Run the cells in sequential order (do not skip cells).

### Execution Order

1. **Step 1: Complexity Categorization**
   - Open `notebooks/02_Complexity_Categorization.ipynb`
   - Run all cells

2. **Step 2: Model Training & LIME Analysis**
   - Open `notebooks/03_Models_Implementation_and_LIME.ipynb`
   - Run all cells
   - LIME explanation HTML files will be generated automatically

---

## 6. Key Results

- Detection performance varies significantly across webpage complexity levels.
- **DCS-OLA** achieved the best overall results, particularly on structurally complex (Hard) webpages.
- The framework is fully client-side (no external services required).
- LIME explanations highlight that hidden elements and script patterns are among the most important features for detecting sophisticated phishing pages.

---

## 7. Dataset Information

This project utilizes the publicly available **Phishing Websites Dataset** from Mendeley Data (~80,000 webpages).

- Classes: Legitimate vs. Phishing
- Raw HTML files are not included in this repository due to size limits. Please refer to `data/raw/README.txt` for download instructions.

---

## Citation

If you use this repository, please cite the corresponding research paper (to be updated after publication).
