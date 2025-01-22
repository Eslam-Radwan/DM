# Data Mining  
## Density Based Clustering  
- **Dr. Wedad Hussein**  
  - Email: wedad.hussein@cis.asu.edu.eg  
- **Dr. Mahmoud Mounir**  
  - Email: mahmoud.mounir@cis.asu.edu.eg  

---

# TYPES OF CLUSTERING  
Clustering algorithms can be categorized into:  
- **Connectivity-based Clustering**  
- **Centroid-based Clustering**  
- **Distribution-based Clustering**  
- **Density-based Clustering**  
- **Graph-based Clustering**  

---

# DBSCAN  

- **K-Means** is suitable for finding spherical-shaped clusters or convex clusters.  
  - Works well for compact and well-separated clusters.  
  - Severely affected by noise and outliers.  
  - **Real-life data challenges**:  
    - Clusters can be of arbitrary shape (oval, linear, “S” shape).  
    - Data may contain noise and outliers.  

- **Example Plot**:  
  - Contains 5 clusters and outliers.  
  - Includes:  
    - 2 oval clusters.  
    - 2 linear clusters.  
    - 1 compact cluster.  

---

# DBSCAN  

- **K-Means Limitations**:  
  - Struggles to identify clusters with arbitrary shapes.  
  - Example: K-means inaccurately identifies 5 clusters in the data.  

- **Cluster Plot**:  
  - [FIGURE]  

---

# DBSCAN  

- **DBSCAN Performance**:  
  - DBSCAN performs better for datasets with arbitrary shapes and noise.  
  - Correctly identifies clusters compared to K-means.  

- **Cluster Plot**:  
  - [FIGURE]  

---

# DBSCAN  

- **DBSCAN Overview**:  
  - **Density-Based Spatial Clustering of Applications with Noise (DBSCAN)**.  
  - Can identify clusters of any shape in datasets containing noise and outliers.  

- **Advantages of DBSCAN**:  
  - Does not require the user to specify the number of clusters.  
  - Can find clusters of any shape (not limited to circular clusters).  
  - Can identify outliers.  

---

# DBSCAN  

- **Basic Idea**:  
  - Derived from a human intuitive clustering method.  
  - Clusters are dense regions in the data space, separated by regions of lower density.  
  - **Key Idea**: For each point in a cluster, the neighborhood of a given radius must contain at least a minimum number of points.  

- **Example Figure**:  
  - [FIGURE]  

---

# Algorithm of DBSCAN  

- **Goal**: Identify dense regions based on the number of objects close to a given point.  
- **Parameters**:  
  - **Epsilon (eps)**: Radius of the neighborhood around a point.  
  - **Minimum Points (MinPts)**: Minimum number of neighbors within the eps radius.  

- **Point Classification**:  
  - **Core Point**: A point with at least MinPts neighbors within eps radius.  
  - **Border Point**: A point with fewer than MinPts neighbors but belongs to the neighborhood of a core point.  
  - **Noise Point**: A point that is neither a core nor a border point.  

- **Example Figure**:  
  - [FIGURE]  

---

# Algorithm of DBSCAN  

- **Point Classification Details**:  
  - A point \( p \) is a **core point** if at least **MinPts** points are within distance **eps** of it.  
  - A point \( q \) is **directly reachable** from \( p \) if \( q \) is within distance **eps** from core point \( p \).  
  - A point \( q \) is **density reachable** from \( p \) if there is a path \( p_1, ..., p_n \) where each \( p_{i+1} \) is directly reachable from \( p_i \).  
  - Two points \( p \) and \( q \) are **density connected** if there is a core point \( x \) such that both \( p \) and \( q \) are density reachable from \( x \).  
  - All points not reachable from any other point are **outliers** or **noise points**.  

- **Example Figure**:  
  - [FIGURE]  

---

# Algorithm of DBSCAN  

- **Cluster Definition**:  
  - A density-based cluster is a group of density-connected points.  
  - If \( A \) is a core point, it forms a cluster with all points (core or non-core) that are reachable from it.  

- **Algorithm Steps**:  
  1. For each point \( x_i \), compute the distance between \( x_i \) and other points.  
  2. Find all neighbor points within distance **eps** of \( x_i \).  
  3. Mark points with a neighbor count greater than or equal to **MinPts** as core points or visited.  
  4. For each core point, if not already assigned to a cluster, create a new cluster. Recursively find all density-connected points and assign them to the same cluster.  
  5. Iterate through the remaining unvisited points.  
  6. Points not belonging to any cluster are treated as outliers or noise.  

---

# DBSCAN Example  

- **Given 8 data points**:  
  - A1 = (2, 10), A2 = (2, 5), A3 = (8, 4), A4 = (5, 8), A5 = (7, 5), A6 = (6, 4), A7 = (1, 2), A8 = (4, 9).  

- **Tasks**:  
  1. Apply DBSCAN with **eps = 2** and **MinPts = 2** (Euclidean distance).  
  2. Apply DBSCAN with **eps = \(\sqrt{10}\)** and **MinPts = 2**.  
  3. Draw a 10x10 grid to illustrate the clusters and outliers for each epsilon value.  

---

# DBSCAN Example (eps = 2, MinPts = 2)  

- **Step 1: Construct Distance Matrix**  
  - [FIGURE]  

- **Step 2: Find Epsilon Neighborhood**  
  - [FIGURE]  

- **Step 3: Identify Clusters and Outliers**  
  - **Cluster (1)**: {A3, A5, A6}  
  - **Cluster (2)**: {A4, A8}  
  - **Outliers**: {A1, A2, A7}  

---

# DBSCAN Example (eps = \(\sqrt{10}\), MinPts = 2)  

- **Step 1: Construct Distance Matrix**  
  - [FIGURE]  

- **Step 2: Find Epsilon Neighborhood**  
  - [FIGURE]  

- **Step 3: Identify Clusters and Outliers**  
  - **Cluster (1)**: {A1, A4, A8}  
  - **Cluster (2)**: {A3, A5, A6}  
  - **Cluster (3)**: {A2, A7}  
  - **No Outliers**  

---

# Parameter Estimation of DBSCAN  

- **Optimal Values for eps and MinPts**:  
  - **MinPts**:  
    - General rule: Derived from the number of dimensions \( D \) in the dataset.  
    - Minimum value for MinPts is 3, but larger values may be needed for large datasets.  
    - If too small, a large part of the data will be considered outliers.  
    - If too high, clusters will merge, and most objects will be in the same cluster.  
  - **eps**:  
    - Small values are preferable.  

- **Example Figure**:  
  - [FIGURE]  

--- 

This document provides a comprehensive overview of DBSCAN, including its advantages, algorithm, and examples with different parameter settings.