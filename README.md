# Phishing Detection Framework using Dynamic Ensemble Selection (DES) and LIME

**Author:** Nivesh Kumar Gupta
**Degree:** M.Tech in Information and Cyber Security
**Institution:** ABV-Indian Institute of Information Technology and Management (IIITM), Gwalior

---

## 1. Project Overview
This research proposes an adaptive framework for detecting phishing websites by analyzing webpage complexity. Traditional detection models often struggle with sophisticated phishing attacks that mimic legitimate sites with high fidelity. This project addresses that gap by:

1.  **Quantifying Webpage Complexity:** Categorizing webpages into "Simple," "Medium," and "Hard" levels based on DOM feature density (e.g., number of scripts, iframes, external links).
2.  **Dynamic Selection (DES/DCS):** Utilizing Dynamic Ensemble Selection (DES) and Dynamic Classifier Selection (DCS) to automatically select the most competent classifiers for each specific complexity level, rather than relying on a single static model.
3.  **Explainable AI (XAI):** Implementing LIME (Local Interpretable Model-agnostic Explanations) to provide transparent reasoning for why a specific URL was classified as phishing.

---

## 2. Methodology

The research workflow follows four distinct stages:

### Phase 1: Feature Extraction
Raw HTML data was parsed to extract structural features. Key attributes include count of scripts, forms, CSS styles, and hidden elements.
* **Input:** Raw HTML files (Mendeley Dataset).
* **Output:** `final_feature_dataset_selected.csv`.

### Phase 2: Complexity Categorization
A weighted complexity score was calculated for each webpage. Based on this score, the dataset was segmented using quantile binning:
* **Simple:** Minimal structure (e.g., simple login pages).
* **Medium:** Standard web content.
* **Hard:** High interactive complexity (e.g., rich banking portals).
* **Output:** `webpage_complexity_categorized_weighted.csv`.

### Phase 3: Dynamic Selection Modeling
We implemented and compared multiple strategies:
* **Base Classifiers:** Random Forest, SVM, Naive Bayes, Decision Tree, Logistic Regression.
* **Dynamic Classifier Selection (DCS):** OLA (Overall Local Accuracy), LCA (Local Class Accuracy).
* **Dynamic Ensemble Selection (DES):** KNORA-E (Eliminate), KNORA-U (Union), META-DES.

### Phase 4: Explainability
LIME was applied to "Hard" complexity test samples to identify which specific DOM features triggered the phishing detection, enhancing trust in the system.

---

## 3. Repository Structure

Phishing-Detection-Framework/
├── data/
│   ├── raw/
│   │   └── README.txt              (Instructions for external raw dataset)
│   └── processed/
│       ├── final_feature_dataset_selected.csv
│       └── webpage_complexity_categorized_weighted.csv
├── notebooks/
│   ├── 01_Feature_Extraction.ipynb        (Data parsing and cleaning)
│   ├── 02_Complexity_Categorization.ipynb (Complexity scoring and binning)
│   └── 03_Models_Implementation_and_LIME.ipynb     (RF, DES, DCS, and LIME analysis)
├── requirements.txt                       (Python dependencies)
└── README.md                              (Project documentation)

---

## 4. Installation and Setup

### Prerequisites
* Python 3.8 or higher
* Git

### Installation Steps
1.  Clone the repository:
    ```bash
    git clone [https://github.com/YOUR_USERNAME/Phishing-Detection-Framework.git](https://github.com/YOUR_USERNAME/Phishing-Detection-Framework.git)
    cd Phishing-Detection-Framework
    ```

2.  Install required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

---

## 5. Usage & Execution Instructions

###  IMPORTANT: Before Running
1.  **Check File Paths:** Always verify the `data_path` variable in the notebooks matches your local folder structure.
    * *Default:* `../data/processed/webpage_complexity_categorized_weighted.csv`
2.  **Sequential Execution:** Do not skip cells. You must click the **Run** button (or Shift+Enter) on each cell in order to load the libraries and data correctly.

### Execution Order
1.  **Step 1: Data Categorization**
    * Open `notebooks/02_Complexity_Categorization.ipynb`
    * Click **Run** on all cells to generate the categorized dataset.

2.  **Step 2: Model Training & LIME Analysis**
    * Open `notebooks/03_Models_Implementation.ipynb`
    * Click **Run** on all cells.
    * This notebook includes the **LIME** analysis at the very end, which generates an HTML explanation file.

---

## 6. Key Results
* **Complexity Impact:** Detection accuracy varies significantly across complexity levels. Standard models perform well on "Simple" sites but degrade on "Hard" sites.
* **DES Performance:** Dynamic Ensemble Selection (specifically KNORA-E) demonstrated superior performance on "Hard" complexity webpages by dynamically activating decision boundaries suited for complex structures.
* **Explainability:** LIME analysis revealed that 'Number of External Scripts' and 'Hidden Elements' were the primary indicators for sophisticated phishing attacks.

---

## 7. Dataset Information
This project utilizes the **Phishing Websites Dataset** from Mendeley Data.
* Total Instances: ~80,000
* Classes: Legitimate vs. Phishing
* *Note: Due to file size limits, raw HTML files are not hosted in this repository. Please refer to `data/raw/README.txt` for download instructions.*