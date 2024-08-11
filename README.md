# Credit Card Fraud Detection

## Project Overview
This project is focused on detecting fraudulent credit card transactions using supervised machine learning techniques. The dataset used is highly imbalanced, with a small proportion of fraudulent transactions compared to legitimate ones. The goal is to build a reliable model that can accurately detect fraud while minimizing false positives and false negatives.

## Dataset Overview
**Source**: The dataset used in this analysis is a 50% random subset of the original credit card fraud dataset from [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud).

**Original Dataset**:
- 284,807 transactions
- 492 fraudulent transactions

**Subset Used**:
- 142,403 transactions
- Approximately 246 fraudulent transactions

**Features**:
- **Time**: The time elapsed between the first transaction in the dataset and each subsequent transaction.
- **Amount**: The transaction amount.
- **V1 to V28**: Principal components obtained with PCA (anonymized features).
- **Class**: The target variable (0 = legitimate transaction, 1 = fraudulent transaction).

## Project Goals
- **Compare Different Models**: Evaluate the performance of various machine learning models to identify the most effective one for fraud detection.
- **Handle Class Imbalance**: Implement techniques such as SMOTE to address the imbalance in the dataset.
- **Deploy the Best Model**: Select and finalize the best-performing model for potential deployment in a real-world fraud detection system.

## Data Preprocessing
- **Scaling**: The `Amount` and `Time` features were scaled using `StandardScaler` to normalize the values.
- **Class Imbalance Handling**: The `SMOTE` (Synthetic Minority Over-sampling Technique) was applied to oversample the minority class.

## Models Used
- **Logistic Regression**: A simple and interpretable model used as a baseline.
- **Random Forest**: A robust model known for handling imbalanced datasets well, and providing feature importance insights.
- **Gradient Boosting**: A powerful model for classification tasks, especially on imbalanced datasets.

## Results Comparison

| Model                | Precision (0) | Precision (1) | Recall (0) | Recall (1) | F1-Score (0) | F1-Score (1) | AUC-ROC |
|----------------------|---------------|---------------|------------|------------|--------------|--------------|---------|
| Logistic Regression   | 0.91          | 0.97          | 0.97       | 0.91       | 0.94         | 0.94         | 0.99    |
| Random Forest         | 1.00          | 1.00          | 1.00       | 1.00       | 1.00         | 1.00         | 1.00    |
| Gradient Boosting     | 0.99          | 0.99          | 0.99       | 0.99       | 0.99         | 0.99         | 0.999   |

**Final Model**: The Random Forest model was selected as the final model for deployment due to its perfect metrics across all evaluation criteria.

## How to Run the Project

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/Credit-Card-Fraud-Detection.git
