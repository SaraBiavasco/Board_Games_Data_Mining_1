# Board Games Data Mining

Data Mining project developed for the **Data Mining 1** course of the M.Sc. in **Data Science and Business Informatics** at the University of Pisa.

**Authors:** Sara Biavasco, Marco Redaelli

## Project Overview

This project analyzes a dataset of **21,925 board games** described by **46 attributes**, including publication year, playing time, complexity, number of players, popularity, rankings, categories, and textual game information.

The goal is to apply an end-to-end data mining pipeline combining exploratory analysis, unsupervised learning, supervised learning, and pattern mining to identify meaningful structures and relationships in the board game domain.

The project includes:

- data understanding and preprocessing;
- numerical clustering;
- semantic clustering on textual information;
- classification;
- regression;
- frequent pattern and association rule mining;
- rule-based classification.

## Dataset

The original dataset contains **21,925 observations and 46 attributes**.

After data cleaning, feature engineering, removal of redundant or inconsistent attributes, and missing-value handling, the prepared dataset used for the main analyses contains **20,671 observations and 24 features**.

Relevant variables include:

- `YearPublished`
- `AvgPlaytime`
- `GameWeight`
- `MfgAgeRec`
- `MinPlayers`
- `MaxPlayers`
- `Ranking`
- `Rating`
- `NumOwned`
- `NumDemand`
- board game category indicators
- `SemanticString`, created from textual game information

For a complete description of the original attributes, see [`Feature-Description.txt`](./Feature-Description.txt).

## Repository Structure

```text
Board_games_data_Mining/
├── 01_data_understanding_preparation.ipynb
├── 02_clustering.ipynb
├── 02_a_semantic_clustering_full_code.ipynb
├── 02_b_semantic_clustering_results.ipynb
├── 02_c_semantic_clustering_interactive_map.html
├── 03_classification.ipynb
├── 04_regression.ipynb
├── 05_pattern_mining.ipynb
├── DM1_game_dataset.csv
├── DM1_game_dataset_prepared.csv
├── Feature-Description.txt
├── Project_report.pdf
├── README.md
├── requirements.txt
└── .gitignore
```

## Analysis Workflow

### 1. Data Understanding and Preparation

The first notebook performs exploratory data analysis and prepares the dataset for the subsequent tasks. It includes:

- data type and distribution analysis;
- duplicate and missing-value inspection;
- semantic consistency checks;
- outlier analysis;
- correlation analysis;
- feature engineering;
- removal of redundant or unsuitable attributes;
- construction of the final prepared dataset.

### 2. Numerical Clustering

Several clustering approaches are compared on the prepared numerical features:

- K-Means;
- Bisecting K-Means;
- DBSCAN;
- OPTICS;
- hierarchical clustering.

The final structural interpretation focuses on **Bisecting K-Means with 4 clusters**, which produced the clearest and most interpretable segmentation among the tested solutions.

### 3. Semantic Clustering

A separate clustering analysis is performed on textual game information. Text embeddings and dimensionality-reduction/topic-modeling techniques are used to identify semantically coherent groups of board games.

The final semantic solution contains **60 clusters**, including interpretable themes such as war games, Napoleonic games, Civil War games, zombie games, dinosaur games, Catan-related games, and Carcassonne-related games.

The semantic analysis is split into three files:

- [`02_a_semantic_clustering_full_code.ipynb`](./02_a_semantic_clustering_full_code.ipynb): complete experimental pipeline;
- [`02_b_semantic_clustering_results.ipynb`](./02_b_semantic_clustering_results.ipynb): compact presentation of the final results;
- [`02_c_semantic_clustering_interactive_map.html`](./02_c_semantic_clustering_interactive_map.html): interactive Plotly visualization of the semantic space.

> **Reproducibility note:** the complete semantic pipeline is computationally intensive and was developed using a notebook/Colab-style workflow. The dedicated results notebook is included to make the final analysis easier to inspect without rerunning the full embedding pipeline.

### 4. Classification

The classification task predicts the discretized `Rating` variable using:

- K-Nearest Neighbors;
- Naive Bayes;
- Decision Trees.

Models are evaluated using accuracy, precision, recall, F1-score, confusion matrices, and One-vs-Rest ROC curves.

The strongest observed test accuracy was approximately **71.8%**.

### 5. Regression

Regression models are used to study the relationship between board game characteristics and `GameWeight`.

The analysis compares:

- Linear Regression;
- Decision Tree Regression;
- Random Forest Regression;
- Gradient Boosting Regression.

`AvgPlaytime` is one of the most influential predictors of `GameWeight`. In the multivariate experiment including `AvgPlaytime`, **Gradient Boosting achieved an R² of approximately 0.678**.

### 6. Pattern Mining

The final stage includes:

- semantic discretization of numerical attributes;
- frequent itemset extraction;
- association rule mining;
- analysis of high-lift rules;
- construction of a rule-based classifier.

The reported rule-based classifier achieved approximately **68% accuracy** with **83.1% coverage** in the final selected configuration.

## Main Results

- **Bisecting K-Means with 4 clusters** provided the clearest numerical clustering structure used for interpretation.
- Semantic clustering identified **60 thematic groups** with several highly interpretable board game topics.
- Classification reached approximately **71.8% test accuracy** in the strongest observed configuration.
- `AvgPlaytime` emerged as a particularly important predictor of `GameWeight`.
- The multivariate **Gradient Boosting** regression model achieved approximately **R² = 0.678**.
- The final rule-based classifier achieved approximately **68% accuracy** with **83.1% coverage**.

## Project Report

The complete discussion of the methodology, parameter selection, experiments, figures, and conclusions is available in [`Project_report.pdf`](./Project_report.pdf).

## Installation

Clone the repository and install the required Python packages:

```bash
git clone <repository-url>
cd Board_games_data_Mining
pip install -r requirements.txt
```

## Notes

Some notebooks contain computationally intensive experiments and may require additional execution time or memory. The saved notebook outputs and the project report are provided to make the main results directly inspectable.
