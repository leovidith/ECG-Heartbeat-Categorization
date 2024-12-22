# ECG Heartbeat Categorization

## **Overview**

This project focuses on the categorization of ECG heartbeat signals into five distinct classes using deep learning models: **Gated Recurrent Units (GRU)** and **Long Short-Term Memory (LSTM)** networks. Both models were evaluated on the MIT-BIH Arrhythmia dataset, consisting of labeled heartbeat signals.

### **Preprocessing**

1. **Data Loading:**
   - The datasets, `mitbih_train.csv` and `mitbih_test.csv`, were loaded into Pandas DataFrames.

2. **Data Inspection:**
   - Checked for null values, duplicates, and class distributions.

3. **Feature-Label Separation:**
   - Extracted features and labels for training and testing.

4. **Data Scaling:**
   - Min-max scaling was applied to normalize the input values to the range [0, 1].

5. **Data Splitting:**
   - Test data was further split into validation and test subsets.

6. **Reshaping:**
   - Reshaped data to be compatible with recurrent layers by adding a third dimension.

### **Models Implemented**

- **GRU:**
  - Two GRU layers with dropout regularization.
  - Dense output layer with softmax activation for multi-class classification.

- **LSTM:**
  - Two LSTM layers with dropout regularization.
  - Dense output layer with softmax activation for multi-class classification.

## **Results**

| Metric                | GRU Model         | LSTM Model       |
|-----------------------|-------------------|------------------|
| **Test Loss**         | 0.0555           | 0.1297          |
| **Test Accuracy**     | 98.45%           | 96.67%          |

### **Classification Report**

| Class | Description                             | GRU Precision | GRU Recall | GRU F1-Score | LSTM Precision | LSTM Recall | LSTM F1-Score |
|-------|-----------------------------------------|---------------|------------|--------------|----------------|-------------|---------------|
| 0     | Normal                                  | 99%           | 99%        | 99%          | 97%            | 99%         | 98%           |
| 1     | Atrial Premature                        | 88%           | 78%        | 82%          | 85%            | 54%         | 66%           |
| 2     | Premature Ventricular Contraction       | 96%           | 95%        | 95%          | 89%            | 91%         | 90%           |
| 3     | Fusion of Ventricular and Normal        | 80%           | 84%        | 82%          | 69%            | 51%         | 59%           |
| 4     | Fusion of Paced and Normal              | 99%           | 99%        | 99%          | 99%            | 93%         | 96%           |

## Loss Curves:
<img src="https://github.com/leovidith/ECG-Heartbeat-Categorization/blob/main/loss%20curves.png" width=1000px>

## **Agile Features**

1. **Iterative Development:**
   - Models were iteratively trained and evaluated to improve performance.

2. **Early Stopping:**
   - Implemented to prevent overfitting by monitoring validation loss.

3. **Learning Rate Adjustment:**
   - Used `ReduceLROnPlateau` to dynamically adjust the learning rate for faster convergence.

4. **Modular Preprocessing Pipeline:**
   - Designed a scalable preprocessing pipeline to adapt easily for future datasets.

5. **Visualization:**
   - Confusion matrices and performance graphs provided insights into model performance.

## **Conclusion**

- The **GRU model** achieved a higher accuracy (98.45%) compared to the LSTM model (96.67%).
- GRU demonstrated superior precision, recall, and F1-scores across most classes, particularly in rare heartbeat categories.
- While LSTM required fewer epochs, its test loss and accuracy suggest GRU’s architecture was more effective for this dataset.
- This project highlights the efficiency of preprocessing and model selection in achieving robust classification results for medical time-series data.

