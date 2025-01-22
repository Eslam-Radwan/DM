Here is the reformatted and extracted text from the provided PDF file, with figures replaced by "[FIGURE]" and consistent formatting maintained:

---

### Data Mining  
**K-Nearest Neighbors and Classifiers Evaluation**  
- Dr. Wedad Hussein (wedad.hussein@cis.asu.edu.eg)  
- Dr. Mahmoud Mounir (mahmoud.mounir@cis.asu.edu.eg)  

---

### Chapter 8: Classification - Basic Concepts  
- **Classification: Basic Concepts**  
- **Decision Tree Induction**  
- **Bayes Classification Methods**  
- **K-Nearest Neighbors**  
- **Model Evaluation**  

---

### K-Nearest Neighbors (KNN)  
- K-Nearest Neighbors (KNN) is a supervised learning algorithm where the result of a new instance query is classified based on the majority of the K-nearest neighbor category.  
- The purpose of this algorithm is to classify a new object based on attributes and training samples.  
- KNN uses neighborhood classification as the prediction value of the new query instance.  

---

### K-Nearest Neighbors (KNN) Example  
Given data instance:  
- X1 = 3 and X2 = 7  
- Determine the suitable class of this instance using the KNN algorithm.  

[FIGURE]  

---

### Steps to Compute K-Nearest Neighbors (KNN)  
1. **Determine parameter K** = number of nearest neighbors.  
2. **Calculate the distance** between the query-instance and all the training samples.  
3. **Sort the distance** and determine nearest neighbors based on the K-th minimum distance.  
4. **Gather the category** of the nearest neighbors.  
5. **Use simple majority** of the category of nearest neighbors as the prediction value of the query instance.  

---

### K-Nearest Neighbors (KNN) Example with Euclidean Distance  
- Suppose K = 3  
- Calculate the Euclidean distance between the query-instance and all training samples.  

[FIGURE]  

---

### Sorting Distances and Determining Nearest Neighbors  
- Sort the distances and determine the nearest neighbors based on the K-th minimum distance.  

[FIGURE]  

---

### Gathering Categories of Nearest Neighbors  
- Gather the category of the nearest neighbors.  
- Use simple majority of the category of nearest neighbors as the prediction value of the query instance.  

[FIGURE]  

---

### K-Nearest Neighbors (KNN) Conclusion  
- We have 2 "Good" and 1 "Bad" in the nearest neighbors.  
- Conclusion: The data instance X1 = 3 and X2 = 7 is classified as "Good."  

---

### K-Nearest Neighbors (KNN) Example with Training Data  
[FIGURE]  

---

### Model Evaluation and Selection  
- **Evaluation metrics**: How can we measure accuracy? Other metrics to consider?  
- Use validation test set of class-labeled tuples instead of the training set when assessing accuracy.  
- **Methods for estimating a classifier's accuracy**:  
  - Holdout method, random subsampling  
  - Cross-validation  
  - Bootstrap  
- **Comparing classifiers**:  
  - Confidence intervals  
  - Cost-benefit analysis and ROC Curves  

---

### Classifier Evaluation Metrics: Confusion Matrix  
- **Confusion Matrix**:  
  - Actual class vs. Predicted class  
  - Includes True Positives (TP), False Negatives (FN), True Negatives (TN), and False Positives (FP).  

[FIGURE]  

---

### Classifier Evaluation Metrics: Accuracy, Error Rate, Sensitivity, and Specificity  
- **Accuracy**: Percentage of test set tuples that are correctly classified.  
  - Formula: Accuracy = (TP + TN) / ALL  
- **Error Rate**:  
  - Formula: Error rate = 1 - accuracy, or (FP + FN) / ALL  
- **Sensitivity (Recall)**: Percentage of positive tuples labeled as positive.  
  - Formula: Sensitivity = TP / (TP + FN)  
- **Specificity**: Percentage of negative tuples labeled as negative.  
  - Formula: Specificity = TN / (FP + TN)  

---

### Classifier Evaluation Metrics: Precision  
- **Precision**: Percentage of tuples labeled as positive that are actually positive.  
  - Formula: Precision = TP / (TP + FP)  

---

### Classifier Evaluation Metrics: Confusion Matrix Example  
[FIGURE]  

---

### Classifier Evaluation Metrics: Example (1)  
- **Precision** = TP / (TP + FP) = 90 / 230 = 39.13%  
- **Sensitivity (Recall)** = TP / P = 90 / 300 = 30.00%  
- **Specificity** = TN / N = 9560 / 9700 = 98.56%  
- **Accuracy** = (TP + TN) / ALL = (90 + 9560) / 10000 = 96.50%  

[FIGURE]  

---

### Classifier Evaluation Metrics: Example (2)  
- **Recognition rate** = (95 + 90 + 85) / 300 = 90%  
- **Sensitivity (Recall) of Class C** = TP / P = 85 / 100 = 85%  
- **Error rate** = 1 - recognition rate = 1 - 0.9 = 0.1 = 10%  

[FIGURE]  

---

This reformatted text maintains all the content from the original PDF, replaces figures with "[FIGURE]", and organizes the information into bullet points and tables for easier readability.