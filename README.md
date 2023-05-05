

<br>
<div align="center">
    <img src="docs/plane_outlier_detection.jpeg" width="50%" alt="unsupervised-outline-detection-logo" align="center" />
</div>
<!-- Badge section -->
<!--<div align="center">
    <a href="#">
        <img src="https://img.shields.io/badge/Python-3.6, 3.7, 3.8-efefef">
    </a>
    <a href="#">
        <img src="https://img.shields.io/badge/License-MIT-efefef">
    </a>
</div>-->
<br>


This notebook explores a plane dataset to see if we can extract **abnormal functionning**.
The goal is to detect elements in the dataset that differs significantly from the majority of the data.
You can find all of this work in the notebook 🚀 [Notebook - **outlier detection**](anomalies.ipynb).

# 📚 Table of contents
-  [✈️ Detection of Abnormal Aircraft Window Measurements](#dim)
-  [⚙️ Exploration of the dataset](#exp)
-  [🛠️ Windows and measures](#For) 
-  [👀 Extrem values windows](#Extrem)   
-  [🔥 Outlier validation with PCA per window and clustering](#pcaPerWindow)
-  [📝 Conclusion](#conclusion_finale)

#  <a id="dim"></a> ✈️ Detection of Abnormal Aircraft Window Measurements
This project aims to build an algorithm to detect abnormal window measurements in aircraft systems. The system records parameters such as speed, temperature, pressure, and electrical current values, and a window is defined as a section of up to 100 measurements.

# <a id="exp"></a> ⚙️ Data Exploration
Data exploration is a critical phase in data analysis that enables us to gain a deeper understanding of our data by examining its distribution, correlations, and inconsistencies across different features. 
- Correlation analysis help me identify relationships between different features. By examining the relationships between features, it can give me an indication for the following work (model selection). 
- Distribution analysis help me identify potential inconsistencies or errors in the data that might require normalization, correction or cleaning. 

# <a id="For"></a> 🛠️ Windows and Measures
This phase allows for a very specific approach to the problem and enables the data to be organized in a way that can be easily manipulated later on. 
A plane records a total of 11 features. For reasons of anonymisation we do not know the meaning of these features. We do however have an index that represents the time dimension: day-cycle-window.
    
    
Data are divide by day: <br> 
* That are divide by cycle:  
  * That are divide by window:  
    * That are divide by measures. 
    
# <a id="Extrem"></a> 👀 Extreme Window Values
This analysis is typically performed manually using visualization graphs and descriptive statistics to examine the distribution of the data to can also be used to identify potential outliers or anomalies. By visually inspecting the data and comparing it to the expected distribution, 
I can identify data points that are significantly different from the majority of the data and may require further investigation.

I also compared this manually-finded extrem window value with the **Isolation Forest** algorithm. 
Isolation Forest is a useful algorithm for outlier detection because it is: efficient, scalable, and able to handle high-dimensional data. It works by randomly partitioning the data into subsets and then recursively isolating outliers by constructing a tree-based structure. 

The algorithm isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature. This process is repeated until the desired number of trees is generated, and the algorithm then assigns an anomaly score to each observation based on the average path length in the trees.
I presented the results and commented on the differences.

# <a id="pcaPerWindow"></a> 🔥 Outlier Validation with PCA and Clustering
I applied Principal Component Analysis (PCA) and clustering to validate the outlier values in the windows.
Algorithms where choosen thanks to sklearn [documentation](http://scikit-learn.org/stable/auto_examples/cluster/plot_cluster_comparison.html).
When choosing clustering algorithms, it is important to consider several factors such as the size of the dataset, the number of features, the distribution of data points, and the type of outliers you are trying to detect. 
In this case, there is a small dataset with 11 features and the PCA data forms a large cluster in the center with scattered data points around it, I can consider the following algorithms:

* K-means clustering: This algorithm is a popular choice for small datasets with well-defined clusters. It works by partitioning the data into a pre-specified number of clusters, with each data point assigned to the closest cluster center. K-means clustering can help identify outliers that are far away from any cluster center.

* DBSCAN (Density-Based Spatial Clustering of Applications with Noise): This algorithm is useful for detecting clusters of arbitrary shapes and can handle outliers effectively. DBSCAN identifies clusters based on density and can separate the central cluster from the scattered data points around it.

* OPTICS (Ordering Points To Identify the Clustering Structure): This algorithm is similar to DBSCAN and can handle outliers effectively by generating a hierarchical clustering structure. OPTICS can also identify clusters of arbitrary shapes and does not require the user to specify the number of clusters beforehand.

In summary, K-means, DBSCAN, and OPTICS are all good options for detecting outliers in my dataset. It's always a good practice to try multiple clustering algorithms and compare their results to see which one performs the best for your dataset. So I will presented the results and commented on the differences.


# <a id="conclusion_finale"></a> 📝 Conclusion
In conclusion, clustering algorithm K-means is an effective tools for detecting elements in this dataset that differ significantly from the majority of the data, and can help to identify potential outliers. However, it is important to note that the presence of such outliers does not necessarily imply that they are anomalous or novel. In many cases, a **human expert** must intervene to analyze the results of the clustering algorithms, interpret the meaning of the detected outliers, and decide whether they represent true anomalies or merely noise in the data. Thus, while clustering algorithms can provide a valuable first step in detecting potential outliers, the final decision about whether an observation is truly anomalous or novel ultimately rests with human judgment and expertise.

# 🎓 Authors

Noémie Cohen
