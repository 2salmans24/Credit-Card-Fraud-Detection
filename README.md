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


# Credit Card Fraud Detection

**Author:** Sarmad Salman

## Project Overview
This project involves detecting fraudulent credit card transactions using machine learning.

**GitHub Repository**: [Credit Card Fraud Detection](https://github.com/2salmans24/Credit-Card-Fraud-Detection)

### Specific Goals:
- **Compare Different Models**: Evaluate the performance of various machine learning models to identify the most effective one for fraud detection.
- **Handle Class Imbalance**: Implement techniques to address the imbalance in the dataset, ensuring that the model is not biased towards the majority class.
- **Deploy the Best Model**: Select and finalize the best-performing model for potential deployment in a real-world fraud detection system.

## Dataset Overview
**Source**: The dataset used in this analysis is a 50% random subset of the original credit card fraud dataset from [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud). The subset contains 72.0 MB of data.

### Original vs. Subset:
- **Original Dataset**: 284,807 transactions with 492 fraudulent transactions.
- **Subset Used**: 142,403 transactions with approximately 246 fraudulent transactions.

**Features**:
- **Time**: The time elapsed between the first transaction in the dataset and each subsequent transaction.
- **Amount**: The transaction amount.
- **V1 to V28**: Principal components obtained with PCA (anonymized features).
- **Class**: The target variable (0 = legitimate transaction, 1 = fraudulent transaction).

## Data Preprocessing

### Scaling:
- **Why?**: The `Amount` and `Time` features were scaled using `StandardScaler` to normalize the values, which helps improve the performance of certain machine learning models that are sensitive to feature scaling, such as Logistic Regression.

### Handling Class Imbalance:
- **Why?**: The dataset is highly imbalanced, with fraudulent transactions being much rarer than legitimate ones. To address this, the `SMOTE` (Synthetic Minority Over-sampling Technique) was applied to oversample the minority class, ensuring the model does not become biased towards the majority class.

## Model Selection

### Model 1: Logistic Regression
- **Why Chosen?**: Logistic Regression is a simple and interpretable model, making it a good baseline for comparison with more complex models.

### Model 2: Random Forest
- **Why Chosen?**: Random Forest is known for its robustness and ability to handle imbalanced datasets well. It also provides insights into feature importance.

### Model 3: Gradient Boosting
- **Why Chosen?**: Gradient Boosting is powerful for handling imbalanced datasets and often yields strong performance in classification tasks.

## Results Comparison

| Model                | Precision (0) | Precision (1) | Recall (0) | Recall (1) | F1-Score (0) | F1-Score (1) | AUC-ROC |
|----------------------|---------------|---------------|------------|------------|--------------|--------------|---------|
| Logistic Regression   | 0.91          | 0.97          | 0.97       | 0.91       | 0.94         | 0.94         | 0.99    |
| Random Forest         | 1.00          | 1.00          | 1.00       | 1.00       | 1.00         | 1.00         | 1.00    |
| Gradient Boosting     | 0.99          | 0.99          | 0.99       | 0.99       | 0.99         | 0.99         | 0.999   |

**Summary**: The Random Forest model achieved perfect metrics across the board, making it the best candidate for deployment. Gradient Boosting also performed exceptionally well but took longer to process, while Logistic Regression provided strong but slightly lower results.

## Discussion and Conclusion

### Summary of Findings
The Random Forest model was selected as the final model due to its perfect performance metrics. However, it’s important to monitor for potential overfitting, as the model’s perfect scores suggest it may be overly tuned to the specific dataset used in training.

### Potential Limitations
- **Overfitting Risk**: The perfect scores in the Random Forest model could indicate overfitting. This could happen if the model is too complex or if the training data is too similar to the test data. Continuous evaluation on new, unseen data is recommended to ensure the model generalizes well.

### Monitoring Overfitting in Deployment
To effectively monitor and mitigate overfitting in a real-world deployment, the following strategies can be employed:

- **Cross-Validation on New Data**: Regularly perform cross-validation on newly acquired data to assess whether the model's performance remains consistent over time. This helps in identifying if the model starts to overfit as new patterns emerge in the data.

- **Periodic Re-training**: Implement a schedule for periodically re-training the model with fresh data. This can help the model adapt to any changes in transaction patterns or fraudulent behaviors that may arise over time.

- **Monitoring Metrics in Production**: Continuously monitor key performance metrics (such as precision, recall, and AUC-ROC) on live data. Set up alerts for significant drops in performance, which could indicate that the model is overfitting or failing to generalize.

### Future Work
- **Further Model Tuning**: Additional hyperparameter tuning for the Random Forest model could be explored to confirm that the current settings are optimal.
- **Monitoring in Deployment**: If the model is deployed, implement monitoring to track its performance over time and adjust as necessary.
- **Exploring Other Models**: Consider exploring other models or ensemble methods that could potentially offer similar or better performance with lower risks of overfitting.

### Contributing
Contributions are welcome! Please feel free to submit a Pull Request if you have any suggestions for improving this project.

### License
This project is licensed under the MIT License. See the LICENSE file for details.

### Contact
For any questions or inquiries, feel free to contact #Sarmad Salman#.
