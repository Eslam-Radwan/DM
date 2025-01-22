### Data Mining  
#### Recommender Systems  
**Dr. Wedad Hussein**  
wedad.hussein@cis.asu.edu.eg  
**Dr. Mahmoud Mounir**  
Mahmoud.mounir@cis.asu.edu.eg  

---

### Web Personalization  
- **Definition**: The process of customizing a website to the needs of specific users.  
- The success of web personalization depends on its ability to anticipate users' needs or next moves and recommend suitable objects.  

---

### How many times have you seen this statement?  
- "People who downloaded / bought / liked this item also downloaded / bought / liked items X and Y."  
- **Association Rules**  
- **Recommender Systems!**  

---

### Recommender Systems  
- **Definition**: Systems that produce individualized recommendations as output. They guide the user in a personalized way to interesting or useful objects in a large space of possible options.  
- **Recommender Systems vs. Information Retrieval Systems**:  
  - "Individuality" and "personalized recommendations."  

---

### Taxonomy of Recommender Systems  
- **Collaborative Filtering**  
- **Content-Based**  
- **Hybrid**  

---

### Inputs  
1. **Ratings**: The opinions of users on the items available in the system.  
2. **Demographic Data**: Data about the user like age, gender, and education.  
3. **Content Data**: Textual data related to the contents of the items to be recommended.  

---

### Collaborative Filtering Systems  
- **Identify like-minded users**:  
  - Search for the "Neighborhood" of the user; that is, the group of users exhibiting similar behavior to the current user.  
  - Builds a user-item matrix containing the ratings of users to all items whenever available. 
  - e-Commerce systems like eBay and Amazon use collaborative filtering to present users with a recommended list of products.  

---

### Outputs  
Collaborative filtering systems could be used for one of two purposes:  
1. **Prediction**: Generates a value indicating the expected rating of an item by the current user.  
2. **Recommendation**: Produces a list of N items that the user is expected to like (Top-N recommendations).  

---

### User-item Matrix  
[FIGURE]  

---

### Representation  
[FIGURE]  

---

### Neighborhood Formation  
- Similarity between users in the user-item matrix should be calculated.  
- Users similar to the active user will form a proximity-based neighborhood with him.  
- **Implemented in two steps**:  
  1. Similarity between all users is calculated.  
  2. Similarities of users are processed to find neighbors.  

---

### Similarity Measures  
- **Cosine Similarity**:  
$$
  
  \text{cos}(x,y) = \frac{\sum_{i=1}^{n} x_i y_i}{\sqrt{\sum_{i=1}^{n} x_i^2} \sqrt{\sum_{i=1}^{n} y_i^2}}
   
$$
- **Pearson Correlation**:  
$$
 
  \text{Pearson}(x,y) = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n} (x_i - \bar{x})^2} \sqrt{\sum_{i=1}^{n} (y_i - \bar{y})^2}}
  
$$

---

### Predicting Ratings  
- Select from the set of nearest neighbors the users that rated the target item.  
- The predicted rating is given by:  

$$
  \text{pred}_{ui} = \overline{r_u} + \frac{\sum_{j=1}^n (r_{ij} - \overline{r_j}) \text{sim}(u,j)}{\sum_{j=1}^n |\text{sim}(u,j)|}
$$
   
  - Where \(n\) is the neighborhood size and $\text{sim}(u,j)$ is the similarity between current user \( u \) and user \( j \).  

---

### Top-N Recommendation  
- Perform a frequency count of the items that each neighbor user has purchased or rated.  
- Exclude items already rated by the active user.  
- Sort the remaining items according to their frequency counts.  
- Return the N most frequent items as the recommendation for the active user.  

---

### Item-based CF  
- The item-based approach works by comparing items based on their pattern of ratings across users.  
- The similarity of items \( i \) and \( j \) is computed as follows:  
$$
  
  \text{sim}(i,j) = \frac{\sum_{u \in U} (r_{ui} - \bar{r_u})(r_{uj} - \bar{r_u})}{\sqrt{\sum_{u \in U} (r_{ui} - \bar{r_u})^2} \sqrt{\sum_{u \in U} (r_{uj} - \bar{r_u})^2}}
  
$$

---

### Item-based Recommendation  
- After computing the similarity between items, select a set of k most similar items to the target item and generate a predicted value of user \( u \)'s rating:  

$$
  p(u,i) = \frac{\sum_{j \in J} \text{sim}(i,j) \cdot r_{uj}}{\sum_{j \in J} |\text{sim}(i,j)|}
$$

  - Where \( J \) is the set of k similar items.  
- **Advantages**:  
  - Overcomes some limitations of user-based CF.  

---

### Evaluation  
- **Mean Absolute Error (MAE)**:  

$$
  \text{MAE} = \frac{1}{n} \sum_{i=1}^{n} |a_i - p_i|
$$

- **Root Mean Square Error (RMSE)**:  

$$
  \text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (a_i - p_i)^2}
$$

  - Where $a_i$ is the actual rating provided by user $i$ for item $j$, $p_i$ is the predicted rating, and $n$ is the number of items already rated by the user.  

---

### Coverage  
- **Definition**: The percentage of items for which the system can provide recommendations.
  
$$
  \text{Coverage} = \frac{\sum_{i=1}^{m} \text{np}_i}{m \times n}
$$

  - Where \( m \) is the number of users, $\text{np}_i$ is the number of items for which the system was able to provide recommendations, and \( n \) is the number of items already rated by the user.  

---

### Challenges with Collaborative Filtering Systems  
1. **Cold Start Problem**:  
   - Newly added items or users cannot be recommended until they have been rated by a number of users.  
   - **Solution**: Integrating other sources of information or collecting preferences/profiles over multiple sites.  
2. **Sparsity of User-item Matrix**:  
   - Users typically only rate a small portion of items, making predictions inaccurate.  
   - **Solution**: Default voting, clustering, or dimensionality reduction.  
3. **Scalability**:  
   - Calculations grow with the number of users and items.  
   - **Solution**: Clustering.  
4. **Popularity Bias (The Gray Sheep Problem)**:  
   - The system struggles to offer accurate recommendations for users with unique tastes.  

---

### Content-Based Systems  
- **Definition**: The system tries to recommend items that match the user profile.  
- **User Profile**: Based on items the user has liked in the past or explicit interests they define.  
- **Advantage**: Can overcome the cold start problem (new items).  
- **Disadvantage**: Over-specialization.  

---

### Approaches in Content-Based Systems  
1. **Case-Based Reasoning**:  
   - Calculate similarity based on the attributes of the items.  
   - Recommends items most similar to those the user has liked before.  
   - **Disadvantage**: Suffers from the new user problem.  
2. **Attribute-Based Techniques**:  
   - Include information about the user in the recommendation process.  
   - **Advantage**: Overcome the new user problem.  
   - **Disadvantage**: Do not adapt to new ratings added since user information is static.  

---

### Hybrid Systems  
- **Definition**: Combine user ratings and content information to yield better recommendations.  
- **Methods**:  
  1. **Feature Augmentation**:  
     - Based on content features, additional ratings are created.  
     - E.g., User X likes Items 1 and 3; Item 7 is similar to 1 and 3 by a degree of 0.75. Thus, User X likes Item 7 by 0.75.  
  2. **Weighted Hybrid**:  
     - Combine recommendations from two systems using weighted scores.  
     - **Example**:  
       - Recommender 1: Item1 (0.5), Item2 (0.9), Item3 (0.3), Item4 (0.1), Item5 (0).  
       - Recommender 2: Item1 (0.8), Item2 (0.9), Item3 (0.4), Item4 (0), Item5 (0).  
       - Combined Score: Item1 (0.65), Item2 (0.45), Item3 (0.35), Item4 (0.05), Item5 (0.00).  
  3. **Switching Hybrid**:  
     - Select between two recommenders based on user profile or selection criteria.  
  4. **Cascade Hybrid**:  
     - Each recommender system filters the list of items produced by the previous one.  

---

### Other Techniques  
1. **Context-Aware Recommender Systems**:  
   - Recommendations depend on the context (e.g., winter vs. summer vacation, gift vs. personal purchase).  
2. **Social (Trust-based) Systems**:  
   - Users tend to receive advice from people they trust (e.g., friends).  
   - Trusted friends can be defined explicitly or inferred from social networks.  

---

### Challenges in Context-Aware Recommender Systems  
1. Obtaining sufficient and reliable data describing the user context.  
2. Selecting the right information.  
3. Extending collaborative filtering to include contextual dimensions.  

---
