# Mobile Price Classification using Support Vector Machine (SVM)

## Overview

When buying a smartphone, people often compare specifications such as RAM, Storage, Battery Capacity, and Screen Size before making a decision. In this project, I explored whether these technical specifications alone can help predict whether a mobile phone belongs to a **High Price** or **Low Price** category.

Instead of directly predicting the exact price, I transformed the problem into a classification task and used **Support Vector Machine (SVM)** to learn the patterns hidden inside the data. The project follows a complete machine learning workflow, starting from raw data cleaning and ending with model training, evaluation, and visualization.

---

## Project Goal

The original dataset contains mobile phone specifications along with their market prices. Since SVM is primarily used for classification, I created a new target column called **Category**.

* Phones priced above the median price were labeled as **High Price (1)**
* Phones priced below the median price were labeled as **Low Price (0)**

The objective was to train a model capable of distinguishing expensive smartphones from budget smartphones based on their specifications.

---

## Dataset Understanding

The dataset contains information about smartphones from different brands and models. Important features include:

* Brand
* Model
* RAM
* Storage
* Screen Size
* Battery Capacity
* Price

These features provide valuable information about a phone's overall capability and market value.

---

## Data Preparation & Cleaning

Real-world datasets are rarely ready for machine learning directly. Before training the model, several preprocessing steps were performed:

### Data Inspection

The dataset was explored using shape, information, and descriptive statistics to understand its structure.

### Missing Values Analysis

Missing values were checked numerically and visually using a heatmap. The dataset was already complete and required no missing-value treatment.

### Duplicate Analysis

Duplicate rows were inspected carefully. Since the repeated entries did not significantly affect data quality, they were intentionally retained.

### Encoding Categorical Features

Machine learning models work with numbers rather than text. Therefore:

* Brand names were converted into numerical labels.
* Model names were encoded into machine-readable form using Label Encoding.

### Feature Cleaning

Several columns contained text mixed with numeric values.

Examples:

* `8GB → 8`
* `256GB → 256`
* `$1,299 → 1299`

Additional cleaning was performed for inconsistent screen size values to ensure numerical consistency across the dataset.

### Feature Selection

The Camera column contained inconsistent formatting and was removed to avoid unnecessary complexity during model training.

---

## Outlier Detection & Treatment

Outliers can distort learning and negatively affect model performance.

To address this:

* Boxplots were used to visually identify extreme values.
* The **Interquartile Range (IQR)** technique was applied to detect unusual observations.
* Outliers were analyzed in key features such as:

  * Storage
  * RAM
  * Battery Capacity
  * Price

This step helped create a cleaner and more reliable dataset.

---

## Feature Scaling

Support Vector Machines are highly sensitive to feature scales.

To ensure fair contribution from every feature:

**Min-Max Scaling** was applied.

This transformed all feature values into a common range between **0 and 1**, preventing large-scale features from dominating smaller ones.

---

## Exploratory Data Analysis

Before training the model, I explored relationships between features through visual analysis.

### Correlation Analysis

A correlation heatmap was generated to identify relationships between variables and understand how different smartphone specifications interact with one another.

### Scatter Visualization

Storage and RAM were visualized using scatter plots to observe whether expensive and inexpensive phones formed distinguishable groups.

This provided intuition about how separable the classes might be before applying SVM.

---

## Model Training

The dataset was divided into:

* **80% Training Data**
* **20% Testing Data**

The model learned patterns from the training set and was later evaluated on unseen testing data.

Three SVM kernels were explored:

### Linear Kernel

Attempts to separate classes using a straight decision boundary.

### Polynomial Kernel

Creates more flexible curved boundaries capable of capturing non-linear relationships.

### RBF (Radial Basis Function) Kernel

The most powerful and commonly used kernel, capable of learning complex decision boundaries and non-linear patterns.

Comparing multiple kernels helped understand how different SVM configurations behave on the same dataset.

---

## Model Evaluation

The trained models were evaluated using:

* Mean Absolute Error (MAE)
* Mean Squared Error (MSE)
* R² Score

Predicted results were compared with actual values to measure how effectively the model learned from the data.

---

## Understanding SVM Intuition

One of the main goals of this project was not only to apply SVM but also to understand how it works.

Support Vector Machine does not simply draw a boundary between classes. Instead, it searches for the boundary that maximizes the distance between different classes.

The data points closest to this boundary are called **Support Vectors**, and they play the most important role in determining where the decision boundary is placed.

This idea allows SVM to generalize well even when the data becomes more complex.

---

## Technologies Used

| Technology       | Purpose                                 |
| ---------------- | --------------------------------------- |
| Python           | Core Programming Language               |
| Pandas           | Data Loading & Manipulation             |
| NumPy            | Numerical Operations                    |
| Matplotlib       | Data Visualization                      |
| Seaborn          | Heatmaps & Exploratory Analysis         |
| Scikit-learn     | Preprocessing, Scaling, SVM, Evaluation |
| Jupyter Notebook | Interactive Development Environment     |

---

## Key Learning Outcomes

Through this project, I learned:

* How to convert a regression-style dataset into a classification problem.
* How to clean and prepare real-world smartphone datasets.
* How Label Encoding and Feature Scaling affect machine learning models.
* How different SVM kernels behave on the same dataset.
* How Support Vectors and decision boundaries work conceptually.
* How preprocessing directly influences model performance.

---

## Conclusion

This project demonstrates a complete machine learning pipeline for smartphone price classification using Support Vector Machines. Beyond building the model itself, the focus was placed on understanding data preparation, feature engineering, visualization, kernel selection, and the intuition behind SVM decision boundaries.

The notebook serves as both a practical implementation and a learning resource for understanding how SVM can be applied to real-world classification problems.
