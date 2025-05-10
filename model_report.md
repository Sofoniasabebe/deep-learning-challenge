
# 📊 AlphabetSoupCharity Deep Learning Model Report

## 🧾 Overview of the Analysis

This analysis aims to create a deep learning binary classification model to predict if a charitable organization will be successful if funded by Alphabet Soup, using features from the charity_data.csv dataset. The goal is to exceed 75% prediction accuracy through various model architectures and data preprocessing strategies.

## 📌 Results
### 🔍 Data Preprocessing

- **Target Variable:**
  - `IS_SUCCESSFUL`: Indicates whether the funding application was approved (`1`) or not (`0`).

- **Feature Variables:**
  - All columns except `EIN` and `NAME`, which were removed.
  - Features include: `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, `ASK_AMT`, etc.

- **Preprocessing Steps:**
  - Dropped uninformative columns (`EIN`, `NAME`)
  - Binned rare categorical values as `"Other"`
  - Converted categorical data into a numerical format that machine learning models can process
  - Scaled numeric features with `StandardScaler`

---

### 🧠 Model Architectures and Evaluation

| Attempt | Layers / Neurons        | Activations         | Dropout | Accuracy | Loss   |
|--------:|--------------------------|----------------------|---------|----------|--------|
| 1       |80 → 30 → → 1        | relu / relu / sigmoid | ❌      | **0.7306** | 0.5612 |
| 2       | 128 → 64 → 32 → 1        | relu / relu / relu / sigmoid | ❌ | 0.7291   | 0.5812 |
| 3       | 128 → 64 → 32 → 1 | relu / relu / relu / sigmoid | ✅ 0.3  | 0.7271   | 0.5713 |
| 4       | Similar structure with batch normalization | relu / relu / relu / sigmoid | ✅ 0.2     | 0.7298   | 0.5578 |

> ✅ **Best accuracy: 73.06%** using the simplest ReLU model without dropout.

### Summary of steps taken to icrease model performance
* Increased the number of neurons in the first few hidden layers (up to 128) to enhance learning capacity
* Stacked multiple hidden layers (up to 3 before output), adding depth to the network to capture more complex patterns
* Used relu for all hidden layers to avoid vanishing gradients and improve training stability
* Used sigmoid in the output layer for binary classification
* Introduced Dropout(0.3) in Attempt #2 and Dropout(0.2) in Attempt #3 to reduce overfitting
* Trained all models for 100 epochs to ensure convergence
* Compared multiple models with/without dropout
* Tested slight architectural changes in each attempt to evaluate generalization 

Despite these efforts, the best model achieved an accuracy of 73.06%, just below the 75% target. 

---

## ✅ Overall Summary and Recommendation

- The final models **did not reach the 75% target**.
- The highest test accuracy was **73.06%**, from Attempt #1.
- Increasing model depth or adding dropout did not lead to better performance.
- The model was well-preprocessed and structured, but the neural network's performance plateaued.

### 🔄 Future Recommendations

- Try **non-neural models** better suited for structured/tabular data like **Random Forest**: lterature shows that neural networks are not always ideal for tabular data. Neural networks excel at recognizing complex spatial patterns like in images, speech, or sequences. However, tabular datasets, craity dataset in this case, often have many categorical values and may lack the spatial structure that deep learning exploits.  
- Use **Keras Tuner** for automated hyperparameter search: as alibrary that automatically builds and evaluates multiple model architectures, **Keras Tuner** might help one go beyond manual trial-and-error to find optimal configuraations systematically. Some tunable hyperparametrs that can be used include the number of neurons, layers, activation functions, dropout rate, optimizer choice, and learning rate. A combination of some of these hyperparametrs could significantly affect a model’s ability to learn and generalize.



