

# Bank Customers Churn Prediction using ANN

This project builds an **Artificial Neural Network (ANN)** using **TensorFlow and Keras** to predict **bank customer churn**. The goal is to analyze which customers are likely to leave (churn) and help the bank take proactive measures.

---

##  About Dataset

* The dataset contains **10,000 bank customers**.
* Each row corresponds to a customer, and the target column is:

  * **Exited = 1 → Customer left the bank**
  * **Exited = 0 → Customer stayed with the bank**

### **Features**

| Column          | Description                                |
| --------------- | ------------------------------------------ |
| RowNumber       | Index (not useful for modeling)            |
| CustomerId      | Unique ID (not useful for modeling)        |
| Surname         | Customer surname                           |
| CreditScore     | Credit score                               |
| Geography       | Customer location (France, Spain, Germany) |
| Gender          | Male/Female                                |
| Age             | Customer age                               |
| Tenure          | Years with bank                            |
| Balance         | Account balance                            |
| NumOfProducts   | Number of products used                    |
| HasCrCard       | Has a credit card (0/1)                    |
| IsActiveMember  | Active membership (0/1)                    |
| EstimatedSalary | Estimated salary                           |
| Exited          | Target variable (0 = No churn, 1 = Churn)  |

---

##  Data Preprocessing

1. Checked for missing values → **None found**.
2. **One-hot encoded** categorical columns: *Geography* and *Gender*.
3. **Standardized features** using `StandardScaler`.
4. Split dataset into **80% training** and **20% testing** sets.

---

##  Model Architecture

The ANN model was built using **Keras Sequential API**:

* **Dense (64 neurons, ReLU)** – Input layer
* **Dense (64 neurons, ReLU)** – Hidden layer
* **Dense (1 neuron, Sigmoid)** – Output layer (binary classification)

**Compilation**:

* Optimizer: `adam`
* Loss: `binary_crossentropy`
* Metrics: `accuracy`

---

##  Model Training

* Trained for **300 epochs** initially → observed **overfitting** (Train acc ≈ 99.6%, Val acc ≈ 81.6%).
* Applied **regularization** and reduced epochs → trained for **50 epochs**.

###  Final Model Performance

* **Training Accuracy**: 87.56%
* **Validation Accuracy**: 85.56%
* **Test Accuracy**: 85.75%
* **Test Loss**: 0.3627

Model generalizes well and avoids overfitting.

---

##  Evaluation Metrics

Confusion Matrix results:
<img width="658" height="547" alt="image" src="https://github.com/user-attachments/assets/21ae65ca-8214-4d6e-b16c-0720c5ac8b1f" />


* **Correctly classified churn (1s)**: 217
* **Incorrectly classified churn (false negatives)**: 188
* **Correctly classified non-churn (0s)**: 1498
* **Incorrectly classified non-churn (false positives)**: 97

###  Classification Report

| Metric    | Class 0 (Stayed) | Class 1 (Churned) |
| --------- | ---------------- | ----------------- |
| Precision | 0.89             | 0.69              |
| Recall    | 0.94             | 0.54              |
| F1-Score  | 0.91             | 0.60              |
| Support   | 1595             | 405               |

* **Overall Accuracy**: **86%**
* **Macro Avg F1**: 0.76
* **Weighted Avg F1**: 0.85

---

##  How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/Bank-Customers-Churn-ANN.git
   cd Bank-Customers-Churn-ANN
   ```


