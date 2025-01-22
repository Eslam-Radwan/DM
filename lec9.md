### Data Mining: Supervised Learning  
**Dr. Wedad Hussein**  
wedad.hussein@cis.asu.edu.eg  
**Dr. Mahmoud Mounir**  
mahmoud.mounir@cis.asu.edu.eg  

---

### Data Mining: Concepts and Techniques (3rd ed.)  
**Chapter 8**  
Jiawei Han, Micheline Kamber, and Jian Pei  
University of Illinois at Urbana-Champaign & Simon Fraser University  
2011 Han, Kamber & Pei. All rights reserved.  

---

### Chapter 8. Classification: Basic Concepts  
- **Classification: Basic Concepts**  
- **Decision Tree Induction**  
- **Bayes Classification Methods**  
- **Rule-Based Classification**  
- **Model Evaluation and Selection**  
- **Techniques to Improve Classification Accuracy: Ensemble Methods**  
- **Summary**  

---

### INTRODUCTION  
Given the following dataset of objects:  

| Objects | Attribute 1 (X) | Attribute 2 (Y) | Attribute 3 (Z) |  
|---------|-----------------|-----------------|-----------------|  
| OB-1    | 1               | 4               | 1               |  
| OB-2    | 1               | 2               | 2               |  
| OB-3    | 1               | 4               | 2               |  
| OB-4    | 2               | 1               | 2               |  
| OB-5    | 1               | 1               | 1               |  
| OB-6    | 2               | 4               | 2               |  
| OB-7    | 1               | 1               | 2               |  
| OB-8    | 2               | 1               | 1               |  

---

### INTRODUCTION (with Class Labels)  
Given the following dataset of objects:  

| Objects | Attribute 1 (X) | Attribute 2 (Y) | Attribute 3 (Z) | Class |  
|---------|-----------------|-----------------|-----------------|-------|  
| OB-1    | 1               | 4               | 1               | A     |  
| OB-2    | 1               | 2               | 2               | B     |  
| OB-3    | 1               | 4               | 2               | B     |  
| OB-4    | 2               | 1               | 2               | A     |  
| OB-5    | 1               | 1               | 1               | A     |  
| OB-6    | 2               | 4               | 2               | B     |  
| OB-7    | 1               | 1               | 2               | A     |  
| OB-8    | 2               | 1               | 1               | A     |  

---

### Supervised vs. Unsupervised Learning  
- **Supervised Learning (Classification):**  
  - Supervision: The training data (observations, measurements, etc.) are accompanied by labels indicating the class of the observations.  
  - New data is classified based on the training set.  

- **Unsupervised Learning (Clustering):**  
  - The class labels of training data are unknown.  
  - Given a set of measurements, observations, etc., with the aim of establishing the existence of classes or clusters in the data.  

---

### Prediction Problems: Classification vs. Numeric Prediction  
- **Classification:**  
  - Predicts categorical class labels (discrete or nominal).  
  - Classifies data (constructs a model) based on the training set and the values (class labels) in a classifying attribute and uses it in classifying new data.  

- **Numeric Prediction:**  
  - Models continuous-valued functions, i.e., predicts unknown or missing values.  

**Typical Applications:**  
- Credit/loan approval.  
- Medical diagnosis: if a tumor is cancerous or benign.  
- Fraud detection: if a transaction is fraudulent.  
- Web page categorization: which category it is.  

---

### Classification - A Two-Step Process  
1. **Model Construction:**  
   - Describing a set of predetermined classes.  
   - Each tuple/sample is assumed to belong to a predefined class, as determined by the class label attribute.  
   - The set of tuples used for model construction is the training set.  
   - The model is represented as classification rules, decision trees, or mathematical formulae.  

2. **Model Usage:**  
   - For classifying future or unknown objects.  
   - Estimate the accuracy of the model.  
   - The known label of the test sample is compared with the classified result from the model.  
   - Accuracy rate is the percentage of test set samples that are correctly classified by the model.  
   - Test set is independent of the training set (otherwise overfitting).  
   - If the accuracy is acceptable, use the model to classify new data.  

**Note:** If the test set is used to select models, it is called a validation (test) set.  

---

### Process (1): Model Construction  
**Classification Algorithms**  
- **Training Data:**  
  - NAME: Mike, Mary, Bill, Jim, Dave, Anne  
  - RANK: Assistant Prof, Assistant Prof, Professor, Associate Prof, Assistant Prof, Associate Prof  
  - YEARS: 3, 7, 2, 7, 6, 3  
  - Qualified: no, yes, yes, yes, no, no  

- **Classifier (Model):**  
  - IF rank = 'professor' OR years > 6 THEN qualified = 'yes'  

---

### Process (2): Using the Model in Prediction  
**Classifier**  
- **Testing Data:**  
  - NAME: Tom, Merlisa, George, Joseph  
  - RANK: Assistant Prof, Associate Prof, Professor, Assistant Prof  
  - YEARS: 2, 7, 5, 7  
  - Qualified: no, no, yes, yes  

- **Unseen Data:**  
  - Jeff, Professor, 4  
  - Qualified? Yes  

---

### Chapter 8. Classification: Basic Concepts  
- **Classification: Basic Concepts**  
- **Decision Tree Induction**  
- **Bayes Classification Methods**  
- **Rule-Based Classification**  
- **Model Evaluation and Selection**  
- **Techniques to Improve Classification Accuracy: Ensemble Methods**  
- **Summary**  

---

### Decision Tree Induction: An Example  
- **Training Data Set:** Buys_computer  
- The data set follows an example of Quinlan’s ID3 (Playing Tennis).  
- **Resulting Tree:**  
  - age?  
    - <=30  
      - student?  
        - yes  
        - no  
    - 31...40  
    - >40  
      - credit rating?  
        - excellent  
        - fair  

| age | income | student | credit rating | buys_computer |  
|-----|--------|---------|---------------|---------------|  
| <=30 | high   | no      | fair          | no            |  
| <=30 | high   | no      | excellent     | no            |  
| 31...40 | high   | no      | fair          | yes           |  
| >40 | medium | no      | fair          | yes           |  
| >40 | low    | yes     | fair          | yes           |  
| >40 | low    | yes     | excellent     | no            |  
| 31...40 | low    | yes     | excellent     | yes           |  
| <=30 | medium | no      | fair          | no            |  
| <=30 | low    | yes     | fair          | yes           |  
| >40 | medium | yes     | fair          | yes           |  
| <=30 | medium | yes     | excellent     | yes           |  
| 31...40 | high   | yes     | fair          | yes           |  
| >40 | medium | no      | excellent     | no            |  

---

### Algorithm for Decision Tree Induction  
- **Basic Algorithm (a greedy algorithm):**  
  - Tree is constructed in a top-down recursive divide-and-conquer manner.  
  - At start, all the training examples are at the root.  
  - Attributes are categorical (if continuous-valued, they are discretized in advance).  
  - Examples are partitioned recursively based on selected attributes.  
  - Test attributes are selected on the basis of a heuristic or statistical measure (e.g., information gain).  

- **Conditions for Stopping Partitioning:**  
  - All samples for a given node belong to the same class.  
  - There are no remaining attributes for further partitioning - majority voting is employed for classifying the leaf.  
  - There are no samples left.  

---

### Brief Review of Entropy  
- **Entropy = H(D) = -P Log2 P**  
- **Attribute 1:**  
  - 4 Class A  
  - 4 Class B  
  - Entropy = H(Attribute 1) = - log2 ( ) - log2 ( ) = 1  

- **Attribute 2:**  
  - 8 Class A  
  - 8 Class B  
  - Entropy = H(Attribute 2) = - log2 ( ) - log2 ( ) = 0  

---

### Brief Review of Entropy (Continued)  
- **Attribute 3:**  
  - 5 Class A  
  - 3 Class B  
  - Entropy = H(Attribute 3) = - log2 ( ) - log2 ( ) = 0.424 + 0.531 = 0.955  

- **Attribute 4:**  
  - 2 Class A  
  - 6 Class B  
  - Entropy = H(Attribute 4) = - log2 (2) - log2 (6) = 0.811  

---

### Brief Review of Entropy (Information Theory)  
- **Entropy:**  
  - A measure of uncertainty associated with a random variable.  
  - Calculation: For a discrete random variable Y taking m distinct values y1,...,ym,  
    - H(Y) = -P log(pi), where pi = P(Y = yi).  
  - Interpretation:  
    - Higher entropy => higher uncertainty.  
    - Lower entropy => lower uncertainty.  

- **Conditional Entropy:**  
  - [FIGURE]  

---

### Attribute Selection Measure: Information Gain (ID3/C4.5)  
- Select the attribute with the highest information gain.  
- Let p be the probability that an arbitrary tuple in D belongs to class C, estimated by |C,D|/|D|.  
- Expected information (entropy) needed to classify a tuple in D:  
  - Info(D) = -P log2 p;  
- Information needed (after using A to split D into v partitions) to classify D:  
  - InfoA(D) = Σ (|Di| / |D|) * Info(Di)  
- Information gained by branching on attribute A:  
  - Gain(A) = Info(D) - InfoA(D)  

---

### Decision Trees Using ID3 Algorithm  
- **a. What is the entropy of buys_computer?**  
  - [FIGURE]  
  - Entropy(Buys Computer) = H(Buys Computer) = - (5/14) log2 (5/14) - (9/14) log2 (9/14) = 0.531 + 0.41 = 0.941  

- **b. Which attribute should you choose as the root of a decision tree?**  
  - [FIGURE]  
  - Age is the root of the tree because it has the greatest information gain value.  

---

### Decision Trees Using ID3 Algorithm (Continued)  
- **b. Which attribute should you choose as the root of a decision tree?**  
  - [FIGURE]  
  - Age is the root of the tree because it has the greatest information gain value.  

---

### Attribute Selection: Information Gain  
- **Class P:** buys_computer = “yes”  
- **Class N:** buys_computer = “no”  
- Info(D) = I(9,5) = (9/14) log2 (9/14) - (5/14) log2 (5/14) = 0.940  
- Info_age(D) = (5/14) I(2,3) + (4/14) I(4,0) + (5/14) I(3,2) = 0.694  
- Gain(age) = Info(D) - Info_age(D) = 0.246  
- Gain(income) = 0.029  
- Gain(student) = 0.151  
- Gain(credit_rating) = 0.048  

---

### Decision Trees Using ID3 Algorithm  
- **You are stranded on a deserted island. Mushrooms of various types grow widely all over the island, but no other food is anywhere to be found. Some of the mushrooms have been determined as poisonous and others as not (determined by your former companions’ trial and error). You are the only one remaining on the island. You have the following data to consider:**  

| Example | NotHeavy | Smelly | Spotted | Smooth | Edible |  
|---------|----------|--------|---------|--------|--------|  
| A       | 1        | 0      | 0       | 0      | Yes    |  
| B       | 1        | 0      | 1       | 0      | Yes    |  
| C       | 0        | 1      | 0       | 1      | Yes    |  
| D       | 0        | 0      | 0       | 1      | No     |  
| E       | 1        | 1      | 1       | 0      | No     |  
| F       | 1        | 0      | 1       | 1      | No     |  
| G       | 1        | 0      | 0       | 1      | No     |  
| H       | 0        | 1      | 0       | 0      | No     |  

---

### Decision Trees Using ID3 Algorithm  
- **a. What is the entropy of Edible?**  
  - [FIGURE]  
  - Entropy(Edible) = H(Edible) = - (5/8) log2 (5/8) - (3/8) log2 (3/8) = 0.4238 + 0.5306 = 0.9544  

- **b. Which attribute should you choose as the root of a decision tree?**  
  - [FIGURE]  
  - Smooth is the root of the tree because it has the greatest information gain value.  

---

### Computing Information-Gain for Continuous-Valued Attributes  
- Let attribute A be a continuous-valued attribute.  
- Must determine the best split point for A.  
- Sort the value A in increasing order.  
- Typically, the midpoint between each pair of adjacent values is considered as a possible split point.  
- The point with the minimum expected information requirement for A is selected as the split-point for A.  
- D1 is the set of tuples in D satisfying A ≤ split-point, and D2 is the set of tuples in D satisfying A > split-point.  

---

### Overfitting and Tree Pruning  
- **Overfitting:**  
  - An induced tree may overfit the training data.  
  - Too many branches, some may reflect anomalies due to noise or outliers.  
  - Poor accuracy for unseen samples.  

- **Two Approaches to Avoid Overfitting:**  
  - **Prepruning:** Halt tree construction early - do not split a node if this would result in the goodness measure falling below a threshold.  
    - Difficult to choose an appropriate threshold.  
  - **Postpruning:** Remove branches from a "fully grown" tree - get a sequence of progressively pruned trees.  
    - Use a set of data different from the training data to decide which is the "best pruned tree."  

---

### Enhancements to Basic Decision Tree Induction  
- Allow for continuous-valued attributes.  
- Dynamically define new discrete-valued attributes that partition the continuous attribute value into a discrete set of intervals.  
- Handle missing attribute values:  
  - Assign the most common value of the attribute.  
  - Assign probability to each of the possible values.  
- Attribute construction:  
  - Create new attributes based on existing ones that are sparsely represented.  
  - This reduces fragmentation, repetition, and replication.  

---

### Example  
Apply the ID3 algorithm. Suppose we want to train a decision tree using the following instances:  

| Weekend | Weather | ParentsMoney | Decision |  
|---------|---------|--------------|----------|  
| W1      | Sunny   | Yes          | Rich     | Cinema |  
| W2      | Sunny   | No           | Rich     | Tennis |  
| W3      | Windy   | Yes          | Rich     | Cinema |  
| W4      | Rainy   | Yes          | Poor     | Cinema |  
| W5      | Rainy   | No           | Rich     | Stay in |  
| W6      | Rainy   | Yes          | Poor     | Cinema |  
| W7      | Windy   | No           | Poor     | Cinema |  
| W8      | Windy   | No           | Rich     | Shopping |  
| W9      | Windy   | Yes          | Rich     | Cinema |  
| W10     | Sunny   | No           | Rich     | Tennis |  

**Which attribute from the previously mentioned table will be the first node in the tree?**  
- Use your selected root node to partition the previously mentioned instances. Sketch your answer.  

---

### Real-Valued Attributes in Decision Trees  
- **Example:**  
  - The table below shows the relationship between the body height and the gender of a group of persons (the records have been sorted with respect to the value of *height* in cm).  
  - Calculate the information gain for potential splitting thresholds and determine the best one.  

| Height | Gender |  
|--------|--------|  
| 161    | F      |  
| 164    | F      |  
| 169    | M      |  
| 175    | M      |  
| 176    | F      |  
| 179    | F      |  
| 180    | M      |  
| 184    | M      |  
| 185    | F      |  

- **Potential cut points must lie in the intervals (164, 169), (175, 176), (179, 180), or (184, 185).**  

---

### Calculate the Information Gain for Potential Splitting Thresholds  
- **C1 ∈ (164, 169):**  
  - Resulting class distribution: if x < C1 then 2 - 0 else 3 - 4.  
  - Conditional entropy: if x < C1 then E = 0 else E = - (3/7) log2 (3/7) - (4/7) log2 (4/7) = 0.985.  
  - Entropy: E(C1|S) = (3/9) * 0 + (7/5) * 0.985 = 0.766.  

- **C2 ∈ (175, 176):**  
  - Resulting class distribution: if x < C2 then 2 - 2 else 3 - 2.  
  - Entropy: E(C2|S) = (4/9) * 1 + (5/9) * 0.971 = 0.984.  

- **C3 ∈ (179, 180):**  
  - Resulting class distribution: if x < C3 then 4 - 2 else 1 - 2.  
  - Entropy: E(C3|S) = (6/9) * 0.918 + (3/9) * 0.918 = 0.918.  

- **C4 ∈ (184, 185):**  
  - Resulting class distribution: if x < C4 then 4 - 4 else 1 - 0.  
  - Entropy: E(C4|S) = (8/9) * 1 + (1/9) * 0 = 0.889.  

--- 

This document provides a comprehensive overview of classification, decision tree induction, and related concepts in data mining.