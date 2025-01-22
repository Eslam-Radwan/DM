### Data Mining  
**Naive Bayes Classification**  
- **Dr. Wedad Hussein**  
  - Email: wedad.hussein@cis.asu.edu.eg  
- **Dr. Mahmoud Mounir**  
  - Email: mahmoud.mounir@cis.asu.edu.eg  

---

### Data Mining: Concepts and Techniques (3rd ed.)  
- **Chapter 8**  
  - Authors: Jiawei Han, Micheline Kamber, and Jian Pei  
  - Universities: University of Illinois at Urbana-Champaign & Simon Fraser University  
  - Year: 2011  
  - Rights: 2011 Han, Kamber & Pei. All rights reserved.  

---

### Chapter 8. Classification: Basic Concepts  
- **Topics Covered:**  
  - Classification: Basic Concepts  
  - Decision Tree Induction  
  - Bayes Classification Methods  
  - Model Evaluation and Selection  
  - Summary  

---

### Bayesian Classification: Why?  
- **Statistical Classifier:**  
  - Performs probabilistic prediction (predicts class membership probabilities).  
- **Foundation:**  
  - Based on Bayes' Theorem.  
- **Performance:**  
  - Naive Bayesian classifier has comparable performance with decision tree and selected neural network classifiers.  
- **Incremental:**  
  - Each training example can incrementally increase/decrease the probability that a hypothesis is correct.  
  - Prior knowledge can be combined with observed data.  
- **Standard:**  
  - Even when Bayesian methods are computationally intractable, they provide a standard of optimal decision making against which other methods can be measured.  

---

### Bayes’ Theorem: Basics  
- **Total Probability Theorem:**  
  \[ P(B) = \sum_{i=1}^{M} P(B|A_i)P(A_i) \]  
- **Bayes’ Theorem:**  
  \[ P(H | X) = \frac{P(X | H)P(H)}{P(X)} = P(X | H) \times P(H)/P(X) \]  
- **Definitions:**  
  - Let \(X\) be a data sample (“evidence”): class label is unknown.  
  - Let \(H\) be a hypothesis that \(X\) belongs to class \(C\).  
  - **Classification:** Determine \(P(H | X)\), the posteriori probability (probability that the hypothesis holds given the observed data sample \(X\)).  
  - \(P(H)\) (prior probability): The initial probability (e.g., \(X\) will buy a computer, regardless of age, income, etc.).  
  - \(P(X)\): Probability that sample data is observed.  
  - \(P(X | H)\) (likelihood): The probability of observing the sample \(X\), given that the hypothesis holds (e.g., Given that \(X\) will buy a computer, the probability that \(X\) is 31.40, medium income).  

---

### Prediction Based on Bayes' Theorem  
- Given training data \(X\), posteriori probability of a hypothesis \(H\), \(P(H|X)\), follows Bayes' theorem:  
  \[ P(H|X) = \frac{P(X|H)P(H)}{P(X)} \]  
- **Informally:**  
  \[ \text{posteriori} = \frac{\text{likelihood} \times \text{prior}}{\text{evidence}} \]  
- **Prediction:**  
  - Predicts \(X\) belongs to \(C\) iff the probability \(P(C|X)\) is the highest among all the \(P(C_k|X)\) for all the \(k\) classes.  
- **Practical Difficulty:**  
  - Requires initial knowledge of many probabilities, involving significant computational cost.  

---

### Classification Is to Derive the Maximum Posteriori  
- Let \(D\) be a training set of tuples and their associated class labels, and each tuple is represented by an \(n\)-D attribute vector \(X = (x_1, x_2, ..., x_n)\).  
- Suppose there are \(m\) classes \(C_1, C_2, ..., C_m\).  
- **Classification:** Derive the maximum posteriori, i.e., the maximal \(P(C|X)\).  
- This can be derived from Bayes' theorem.  
- Since \(P(X)\) is constant for all classes, only \(P(X|C)P(C)\) needs to be maximized.  

---

### Naïve Bayes Classifier  
- **Simplified Assumption:**  
  - Attributes are conditionally independent (no dependence relation between attributes):  
    \[ P(X | C_i) = \prod_{k=1}^{n} P(x_k | C_i) = P(x_1 | C_i) \times P(x_2 | C_i) \times \ldots \times P(x_n | C_i) \]  
- **Reduced Computation Cost:**  
  - Only counts the class distribution.  
- **Categorical Attributes:**  
  - If \(A_k\) is categorical, \(P(x_k | C_i)\) is the number of tuples in \(C_i\) having value \(x_k\) for \(A_k\) divided by \(|C_i, D|\) (number of tuples of \(C_i\) in \(D\)).  
- **Continuous-Valued Attributes:**  
  - If \(A_k\) is continuous-valued, \(P(x_k | C_i)\) is usually computed based on Gaussian distribution with a mean \(\mu\) and standard deviation \(\sigma\):  
    \[ P(x_k | C_i) = g(x, \mu, \sigma) = \frac{1}{\sqrt{2\pi}\sigma} e^{-\frac{(x-\mu)^2}{2\sigma^2}} \]  
    \[ P(X | C_i) = g(x_k, \mu_{C_i}, \sigma_{C_i}) \]  

---

### Naive Bayes Classifier: Training Dataset  
- **Example Dataset:**  

| age | income | student | credit rating | buys_computer |  
|---|---|---|---|---|  
| <=30  | high   | no    | fair    | no    |  
| <=30  | high   | no    | excellent    | no    |  
| 31...40 | high   | no    | fair    | yes    |  
| >40   | medium   | no    | fair    | yes    |  
| >40   | low   | yes    | fair    | yes    |  
| >40   | low   | yes    | excellent    | no    |  
| 31...40 | low   | yes    | excellent    | yes    |  
| <=30  | medium   | no    | fair    | no    |  
| <=30  | low   | yes    | fair    | yes    |  
| >40   | medium   | yes    | fair    | yes    |  
| <=30  | medium   | yes    | excellent    | yes    |  
| 31...40 | medium   | no    | excellent    | yes    |  
| 31...40 | high   | yes    | fair    | yes    |  
| >40   | medium   | no    | excellent    | no    |  

- **Classes:**  
  - \(C1\): buys_computer = ‘yes’  
  - \(C2\): buys_computer = ‘no’  

- **Data to be Classified:**  
  - \(X = (\text{age} <=30, \text{Income} = \text{medium}, \text{Student} = \text{yes}, \text{Credit\_rating} = \text{Fair})\)  

---

### Naive Bayes Classifier: Training Dataset (Continued)  
- **Compute \(P(C)\) for each class:**  
  - \(P(C1) = P(\text{buys\_computer} = \text{yes}) = 9/14 = 0.643\)  
  - \(P(C2) = P(\text{buys\_computer} = \text{no}) = 5/14 = 0.357\)  

- **Compute \(P(X|C)\) for each class:**  
  - \(P(X|C1) = P(X| \text{buys\_computer} = \text{yes})\)  
  - \(P(X|C2) = P(X| \text{buys\_computer} = \text{no})\)  

---

### Naive Bayes Classifier: Training Dataset (Continued)  
- **Conditional Probabilities:**  

| Age | Buys Computer | Count | Total | Conditional Probability |  
|---|---|---|---|---|  
| <= 30   | Yes    | 2    | 9    | 0.222222222    |  
| <= 30   | No    | 3    | 5    | 0.6    |  
| 31-40  | Yes    | 4    | 9    | 0.444444444    |  
| 31-40  | No    | 0    | 5    | 0    |  
| > 40   | Yes    | 3    | 9    | 0.333333333    |  
| > 40   | No    | 2    | 5    | 0.4    |  

---

### Naive Bayes Classifier: Training Dataset (Continued)  
- **Income Conditional Probabilities:**  

| Income | Buys Computer | Count | Total | Conditional Probability |  
|---|---|---|---|---|  
| High    | Yes    | 2    | 9    | 0.22222222    |  
| High    | No    | 2    | 5    | 0.4    |  
| Medium   | Yes    | 4    | 9    | 0.44444444    |  
| Medium   | No    | 2    | 5    | 0.4    |  
| Low    | Yes    | 3    | 9    | 0.33333333    |  
| Low    | No    | 1    | 5    | 0.2    |  

---

### Naive Bayes Classifier: Training Dataset (Continued)  
- **Student Conditional Probabilities:**  

| Student | Buys Computer | Count | Total | Conditional Probability |  
|---|---|---|---|---|  
| Yes    | Yes    | 6    | 9    | 0.666666667    |  
| Yes    | No    | 1    | 5    | 0.2    |  
| No    | Yes    | 3    | 9    | 0.333333333    |  
| No    | No    | 4    | 5    | 0.8    |  

---

### Naive Bayes Classifier: Training Dataset (Continued)  
- **Credit Rating Conditional Probabilities:**  

| Credit Rating | Buys Computer | Count | Total | Conditional Probability |  
|---|---|---|---|---|  
| Fair    | Yes    | 6    | 9    | 0.666666667    |  
| Fair    | No    | 2    | 5    | 0.4    |  
| Excellent   | Yes    | 3    | 9    | 0.333333333    |  
| Excellent   | No    | 3    | 5    | 0.6    |  

---

### Naive Bayes Classifier: An Example  
- **Class:**  
  - \(C1\): buys_computer = ‘yes’  
  - \(C2\): buys_computer = ‘no’  

- **Compute \(P(X | C_i)\) for each class:**  
  - \(P(X | C1) = P(X | \text{buys\_computer} = \text{yes}) = 0.222 \times 0.444 \times 0.667 \times 0.667 = 0.044\)  
  - \(P(X | C2) = P(X | \text{buys\_computer} = \text{no}) = 0.6 \times 0.4 \times 0.2 \times 0.4 = 0.019\)  

- **Compute \(P(X|C) \times P(C)\) for each class:**  
  - \(P(X|C1) \times P(C1) = 0.044 \times 0.643 = 0.028\)  
  - \(P(X|C2) \times P(C2) = 0.019 \times 0.357 = 0.007\)  

- **Decision:**  
  - \(X\) belongs to class \(C1\) (“buys_computer = yes”).  

---

### Avoiding the Zero-Probability Problem  
- **Problem:**  
  - Naïve Bayesian prediction requires each conditional probability to be non-zero. Otherwise, the predicted probability will be zero.  
  - Example: Suppose a dataset with 1000 tuples, income=low (0), income=medium (990), and income=high (10).  

- **Solution:**  
  - Use **Laplacian correction** (or Laplacian estimator):  
    - Add 1 to each case:  
      - Prob(income = low) = 1/1003  
      - Prob(income = medium) = 991/1003  
      - Prob(income = high) = 11/1003  
    - The “corrected” probability estimates are close to their “uncorrected” counterparts.  

---

### Naive Bayes Classifier: Comments  
- **Advantages:**  
  - Easy to implement.  
  - Good results obtained in most cases.  

- **Disadvantages:**  
  - Assumption: Class conditional independence, therefore loss of accuracy.  
  - Practically, dependencies exist among variables (e.g., hospitals: patients’ profile, symptoms, disease).  
  - Dependencies among these cannot be modeled by Naive Bayes Classifier.  
  - **Solution:** Bayesian Belief Networks (Chapter 9).  

---

### Decision Tree Example: Real-Valued Attributes  
- **Problem:**  
  - Calculate the information gain for potential splitting thresholds and determine the best one.  

- **Dataset:**  

| Height | Gender |  
|---|---|  
| 161 | F |  
| 164 | F |  
| 169 | M |  
| 175 | M |  
| 176 | F |  
| 179 | F |  
| 180 | M |  
| 184 | M |  
| 185 | F |  

- **Potential Cut Points:**  
  - Must lie in the intervals \((164, 169), (175, 176), (179, 180), \text{or} (184, 185)\).  

---

### Decision Tree Example: Information Gain Calculation  
- **Calculate the information gain for the potential splitting thresholds:**  
  - \(C_1 \in (164, 169)\)  
    - Resulting class distribution: if \(x < C_1\) then \(2 - 0\) else \(3 - 4\).  
    - Conditional entropy: if \(x < C_1\) then \(E = 0\) else \(E = -\frac{3}{7} \log_2 \frac{3}{7} - \frac{4}{7} \log_2 \frac{4}{7} = 0.985\).  
    - Entropy: \(E(C_1|S) = \frac{3}{9} \cdot 0 + \frac{7}{5} \cdot 0.985 = 0.766\).  
  - \(C_2 \in (175, 176)\)  
    - Resulting class distribution: if \(x < C_2\) then \(2 - 2\) else \(3 - 2\).  
    - Entropy: \(E(C_2|S) = \frac{4}{9} \cdot 1 + \frac{5}{9} \cdot 0.971 = 0.984\).  
  - \(C_3 \in (179, 180)\)  
    - Resulting class distribution: if \(x < C_3\) then \(4 - 2\) else \(1 - 2\).  
    - Entropy: \(E(C_3|S) = \frac{6}{9} \cdot 0.918 + \frac{3}{9} \cdot 0.918 = 0.918\).  
  - \(C_4 \in (184, 185)\)  
    - Resulting class distribution: if \(x < C_4\) then \(4 - 4\) else \(1 - 0\).  
    - Entropy: \(E(C_4|S) = \frac{8}{9} \cdot 1 + \frac{1}{9} \cdot 0 = 0.889\).  

---