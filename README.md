# deep-learning-challenge

# Introduction

For this challenge,  the assumption is that the nonprofit foundation Alphabet Soup wanted a tool that could help it select the applicants for funding with the best chance of success in their ventures. Using machine learning and neural networks, the goal was to use the features in the provided dataset to create a binary classifier that could predict whether applicants will be successful if funded by Alphabet Soup.

## 🧾 Overview of the Analysis

This analysis aims to create a deep learning binary classification model to predict if a charitable organization will be successful if funded by Alphabet Soup, using features from the charity_data.csv dataset. The goal is to exceed 75% prediction accuracy through various model architectures and data preprocessing strategies.

### 🧠 Model Architectures and Evaluation

| Attempt | Layers / Neurons        | Activations         | Dropout | Accuracy | Loss   |
|--------:|--------------------------|----------------------|---------|----------|--------|
| 1       |80 → 30 → → 1        | relu / relu / sigmoid | ❌      | **0.7306** | 0.5612 |
| 2       | 128 → 64 → 32 → 1        | relu / relu / relu / sigmoid | ❌ | 0.7291   | 0.5812 |
| 3       | 128 → 64 → 32 → 1 | relu / relu / relu / sigmoid | ✅ 0.3  | 0.7271   | 0.5713 |
| 4       | Similar structure with batch normalization | relu / relu / relu / sigmoid | ✅ 0.2     | 0.7298   | 0.5578 |

> ✅ **Best accuracy: 73.06%** using the simplest ReLU model without dropout.

## ✅ Overall Summary and Recommendation

- The final models **did not reach the 75% target**.
- The highest test accuracy was **73.06%**, from Attempt #1.
- Increasing model depth or adding dropout did not lead to better performance.
- The model was well-preprocessed and structured, but the neural network's performance plateaued.

**Detailed findings and recommendation are included in the `model_reprt.md` in this repository.** 

**Reference**

*IRS. Tax Exempt Organization Search Bulk Data Downloads. https://www.irs.gov/charities-non-profits/tax-exempt-organization-search-bulk-data-downloads*
