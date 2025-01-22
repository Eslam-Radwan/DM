# Data Mining  
## Unsupervised Learning  
**Dr. Wedad Hussein**  
wedad.hussein@cis.asu.edu.eg  
**Dr. Mahmoud Mounir**  
mahmoud.mounir@cis.asu.edu.eg  

---

# CLUSTERING  

---

## INTRODUCTION  
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

## INTRODUCTION (with Class Labels)  
Given the following dataset of objects with class labels:  

| Objects | Attribute 1 (X) | Attribute 2 (Y) | Attribute 3 (Z) | Class |     |
| ------- | --------------- | --------------- | --------------- | ----- | --- |
| OB-1    | 1               | 4               | 1               | A     |     |
| OB-2    | 1               | 2               | 2               | B     |     |
| OB-3    | 1               | 4               | 2               | B     |     |
| OB-4    | 2               | 1               | 2               | A     |     |
| OB-5    | 1               | 1               | 1               | A     |     |
| OB-6    | 2               | 4               | 2               | B     |     |
| OB-7    | 1               | 1               | 2               | A     |     |
| OB-8    | 2               | 1               | 1               | A     |     |


---

## INTRODUCTION  
The types of Learning can broadly be classified into two types:  
- **Supervised Learning**  
- **Unsupervised Learning**  

In **Unsupervised Learning**, there is no variable to predict tied to the data. Instead of having an output, the data only has an input which would be multiple variables that describe the data. This is where clustering comes in.  

---

## INTRODUCTION  
### What is Clustering?  
Clustering is the classification of objects into different groups, or more precisely, the partitioning of a dataset into subsets (clusters), so that the data in each subset (ideally) share some common trait - often according to some defined distance measure.  

---

## INTRODUCTION  
### Characteristics of Clustering:  
- Objects in the same cluster are more similar to each other than to objects in other clusters.  
- Similarity is a metric that reflects the strength of the relationship between two data objects.  
- Clustering is mainly used for exploratory data mining. It has manifold usage in many fields such as machine learning, pattern recognition, image analysis, information retrieval, bioinformatics, data compression, and computer graphics.  

---

## Types of Clustering:  
Clustering algorithms can be categorized based on their cluster model, that is based on how they form clusters or groups.  

- **Connectivity-based Clustering**  
- **Centroid-based Clustering**  
- **Distribution-based Clustering**  
- **Density-based Clustering**  

---

### Connectivity-based Clustering  
- Data points that are closer in the data space are more related (similar) than to data points farther away.  
- The clusters are formed by connecting data points according to their distance. At different distances, different clusters will form and can be represented using a dendrogram, which gives away why they are also commonly called "hierarchical clustering".  
- These methods do not produce a unique partitioning of the dataset, rather a hierarchy from which the user still needs to choose appropriate clusters by choosing the level where they want to cluster.  
- They are also not very robust towards outliers, which might show up as additional clusters or even cause other clusters to merge.  

---

### Connectivity-based Clustering  
#### Hierarchical Algorithms:  
- **Agglomerative ("bottom-up")**: Begins with each element as a separate cluster and merges them into successively larger clusters.  
- **Divisive ("top-down")**: Begins with the whole set and proceeds to divide it into successively smaller clusters.  

---

### Centroid-based Clustering  
- Clusters are represented by a central vector or a centroid.  
- This centroid might not necessarily be a member of the dataset.  
- This is an iterative clustering algorithm in which the similarity is derived by how close a data point is to the centroid of the cluster.  
- It is called partitional clustering.  
- Examples are K-means and fuzzy k-means clustering.  

---

### Distribution-based Clustering  
- This clustering is very closely related to statistics: distributional modeling.  
- Clustering is based on the notion of how probable it is for a data point to belong to a certain distribution, such as the Gaussian distribution, for example. Data points in a cluster belong to the same distribution.  
- Example: Gaussian mixture models, using the expectation-maximization algorithm is a famous distribution-based clustering method.  

---

### Density-based Clustering  
- Search the data space for areas of varied density of data points.  
- Clusters are defined as areas of higher density within the data space compared to other regions.  
- Examples: DBSCAN and OPTICS.  

---

## Common Distance Measures:  
Distance measures will determine how the similarity of two elements is calculated and will influence the shape of the clusters.  

1. **Euclidean Distance (also called 2-norm distance)**:  
   \[
   d = \sqrt{(X_2 - X_1)^2 + (Y_2 - Y_1)^2 + (Z_2 - Z_1)^2}
   \]  

2. **Manhattan Distance (also called taxicab norm or 1-norm)**:  
   \[
   d = |X_2 - X_1| + |Y_2 - Y_1| + |Z_2 - Z_1|
   \]  

3. **Maximum Norm**:  
   \[
   d = \max(|X_2 - X_1|, |Y_2 - Y_1|, |Z_2 - Z_1|)
   \]  

4. **Inner Product Space**: The angle between two vectors can be used as a distance measure when clustering high-dimensional data.  

5. **Hamming Distance (sometimes edit distance)**: Measures the minimum number of substitutions required to change one member into another.  

---

## K-MEANS CLUSTERING  
The k-means algorithm is an algorithm to cluster n objects based on attributes into k partitions, where k is a positive integer number.  

- It is similar to the expectation-maximization algorithm for mixtures of Gaussians in that they both attempt to find the centers of natural clusters in the data.  
- It assumes that the object attributes form a vector space.  

---

### K-MEANS CLUSTERING  
An algorithm for partitioning (or clustering) N data points into K disjoint subsets \( S_j \) containing data points so as to minimize the sum-of-squares criterion:  
\[
J = \sum_{j=1}^{K} \sum_{x \in S_j} \|x - \mu_j\|^2
\]  
where \( x \) is a vector representing the nth data point and \( \mu_j \) is the geometric centroid of the data points in \( S_j \).  

---

### K-MEANS CLUSTERING  
Simply speaking, k-means clustering is an algorithm to classify or to group the objects based on attributes/features into K number of groups.  

- K is a positive integer number.  
- The grouping is done by minimizing the sum of squares of distances between data and the corresponding cluster centroid.  

---

### How the K-Means Clustering Algorithm Works?  
1. **Start**: Decide on the number of clusters \( K \).  
2. **Initialize Centroids**: Randomly or systematically assign initial centroids.  
3. **Assign Objects to Clusters**: Assign each object to the cluster with the nearest centroid.  
4. **Update Centroids**: Recalculate the centroids of the clusters.  
5. **Repeat**: Repeat steps 3 and 4 until convergence is achieved (no more changes in cluster assignments).  

---

### A Simple Example Showing the K-Means Algorithm (Using K=2) and the Manhattan Distance as a Similarity Measure  
Given the points:  
- A = (0, 3)  
- B = (1, 3)  
- C = (3, 1)  
- D = (3, 0.5)  
- E = (5, 0)  
- F = (6, 0)  

Starting from initial clusters:  
- Cluster1 = {A}  
- Cluster2 = {D}  

Apply the K-means clustering algorithm and report the final clusters.  

---

### First Iteration (K=2)  
Initial Centroids:  
- C1 = A = (0, 3)  
- C2 = D = (3, 0.5)  

| Objects | Distance from C1=(0,3) | Distance from C2=(3,0.5) | Cluster |  
|---------|------------------------|--------------------------|---------|  
| A = (0, 3)    | 0                      | 5.5                      | 1       |  
| B = (1, 3)    | 1                      | 4.5                      | 1       |  
| C = (3, 1)    | 5                      | 0.5                      | 2       |  
| D = (3, 0.5)  | 5.5                    | 0                        | 2       |  
| E = (5, 0)    | 8                      | 2.5                      | 2       |  
| F = (6, 0)    | 9                      | 3.5                      | 2       |  

---

### Second Iteration (K=2)  
New Centroids:  
- C1 = (0.5, 3)  
- C2 = (4.25, 0.375)  

| Objects | Distance from C1=(0.5,3) | Distance from C2=(4.25,0.375) | Cluster |  
|---------|--------------------------|------------------------------|---------|  
| A = (0, 3)    | 0.5                      | 6.875                        | 1       |  
| B = (1, 3)    | 0.5                      | 5.875                        | 1       |  
| C = (3, 1)    | 4.5                      | 1.875                        | 2       |  
| D = (3, 0.5)  | 5                        | 1.375                        | 2       |  
| E = (5, 0)    | 7.5                      | 1.125                        | 2       |  
| F = (6, 0)    | 8.5                      | 2.125                        | 2       |  

---

### Final Clusters (K=2)  
- **Cluster 1**: A = (0, 3), B = (1, 3)  
- **Cluster 2**: C = (3, 1), D = (3, 0.5), E = (5, 0), F = (6, 0)  

---

## Weaknesses of K-Means Clustering  
1. When the number of data points is small, the initial grouping will significantly determine the cluster.  
2. The number of clusters, \( K \), must be determined beforehand. Its disadvantage is that it does not yield the same result with each run, since the resulting clusters depend on the initial random assignments.  
3. We never know the real cluster, using the same data, because if it is inputted in a different order it may produce different clusters if the number of data points is few.  
4. It is sensitive to the initial condition. Different initial conditions may produce different results of clusters. The algorithm may be trapped in the **local optimum**.  

---

## Applications of K-Means Clustering  
- It is relatively efficient and fast. It computes results at \( O(tkn) \), where \( n \) is the number of objects or points, \( k \) is the number of clusters, and \( t \) is the number of iterations.  
- K-means clustering can be applied to machine learning or data mining.  
- Used on acoustic data in speech understanding to convert waveforms into one of \( k \) categories (known as Vector Quantization or Image Segmentation).  
- Also used for choosing color palettes on old-fashioned graphical display devices and Image Quantization.  

---

## CONCLUSION  
K-means algorithm is useful for undirected knowledge discovery and is relatively simple. K-means has found widespread usage in many fields, ranging from unsupervised learning of neural networks, pattern recognition, classification analysis, artificial intelligence, image processing, machine vision, and many others.  

---

## References  
- Tutorial-Tutorial with an introduction to Clustering Algorithms (k-means, fuzzy-c-means, hierarchical, mixture of Gaussians) + some interactive demos (Java applets).  
- Digital Image Processing and Analysis by B. Chanda and D. Dutta Majumdar.  
- H. Zha, C. Ding, M. Gu, X. He, and H. D. Simon. "Spectral Relaxation for K-means Clustering", Neural Information Processing Systems vol.14 (NIPS 2001), pp.1057-1064, Vancouver, Canada, Dec. 2001.  
- J. A. Hartigan (1975) "Clustering Algorithms". Wiley.  
- J. A. Hartigan and M. A. Wong (1979) "A K-Means Clustering Algorithm", Applied Statistics, Vol.28, No.1, p100-108.  
- D. Arthur, S. Vassilvitskii (2006): "How Slow is the k-means Method?"  
- D. Arthur, S. Vassilvitskii: "k-means++ The Advantages of Careful Seeding" (2007 Symposium on Discrete Algorithms (SODA)).  
- www.wikipedia.com  

---

# Thank You