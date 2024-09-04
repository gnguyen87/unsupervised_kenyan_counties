# An unsupervised Analysis of Kenyan Counties

In this paper, I conducted 3 unsupervised learning analysis methods o uncover significant agricultural, demographic, and geographic patterns across 41 counties in Kenya. 

From our findings through investigating the first 2 PCs and our Hierarchical Clustering Model, we observed that our data exhibits high variability, high separatedness, and rather complex patterns. This indicate that we might need to retain more variability to capture the nuances in the data. Therefore, we would suggest moving forward with 4 PCs, with which we will retain 75% of our original information.From our findings through investigating the first 2 PCs and our Hierarchical Clustering Model, we observed that our data exhibits high variability, high separatedness, and rather complex patterns. This indicate that we might need to retain more variability to capture the nuances in the data. Therefore, we would suggest moving forward with 4 PCs, with which we will retain 75% of our original information.

# Clustering analysis

## Write-up

### K-means Clustering

When performing the K-means model, we first use a silhouette method that chooses K to maximize the distance between clusters and minimizes distance within clusters. This resulted in K equals to 9 clusters. This is a very large value for K given that our dataset only has 41 counties. This might be due to the small size of our dataset and data points being too well-separated. 9 clusters, consequently, cannot give us the best grouping and interpretability for our dataset. Rather, the algorithm might be creating clusters that capture noise or irrelevant patterns in the data, leading to inflated silhouette scores. Hence, given the size and context of the dataset , which results in difficulties when choosing K, and an unreasonable value of K using the silhouette method, we'll continue our analysis using a hierarchical clustering method, which we believe is a better approach.

![image](https://github.com/user-attachments/assets/ca3da977-acf0-480e-9a0d-3b92d305dc41)


### Hierarchical Clustering

According to the hierarchical clustering model, roughly 4 natural clusters can be seen in the dendogram. 4 seems like an appropriate number of clusters given the fact that the dataset contains only 41 observations which could lead to clusters with roughly 10 counties each on average. Furthermore, maximum distance within clusters is 7.5, which is where cluster 2 (colored in purple) fuses, whereas other 3 clusters fuse at roughly a height of 6. Given the context of the data with maximum distance between any two pairs of counties in the dendogram being 10, the height of 6 allows to reduce amount of variability by 40 percent within each cluster. Thus, we examine 4 clusters in the dataset.

Hierarchical clustering further allows for open and different interpretation of the dendogram while visualizing structures within the clusters. Cluster 3 (in green) includes sub-groups whereas cluster 2 (in purple) is fused at the highest point which shows greater variability within the cluster. We further used complete linkage since we want all our clusters to have similar characteristics.

![image](https://github.com/user-attachments/assets/b25ec1a5-79bb-4f74-8d92-8d97120f629b)


The first cluster of counties is not a farming cluster and does not specialize in growing any crops. However, this is the cluster with the highest average household size and contains the second highest number of counties (11). Therefore, it is probably a cluster of urban counties. Counties such as Mombasa, Garissa, Wajir, etc that are included in cluster 1 are all urban cities or towns.

- Cluster 2,3, and 4 are farming oriented counties that each specialize in a variety of crops.
- Cluster 2 is the smallest cluster with 4 counties and specializes in cashew, coconut and mango production.
- Cluster 3 is the largest cluster with 20 counties and primarily produce avocado along with tea and mango.
- Cluster 4 produces avocado, coffee, khatmiraa, macadamia, and tea.
- The male and female gender distribution is roughly the same across all clusters. However, cluster 1 has the largest proportion of intersex population with cluster 2 and 3 having lowest proportion.

![image](https://github.com/user-attachments/assets/331dd80c-3306-4fbf-a933-70cf9a8c29fb)

Considering the size of our dataset, we would move forward with our Hierarchical Clustering Model with 4 clusters as the approach to identify similarities between each county in Kenya. Furthermore, as seen in the hierarchical clustering map, clusters of counties identified are also geographically close to each other. This approach gives meaningful clusters in terms of agricultural expertise and geographical locations (urban vs rural).

![image](https://github.com/user-attachments/assets/ab411441-d703-4cf9-864b-dfd423e4dac4)


# Dimension reduction analysis

## Write-up

### The features of the first 2 PCs

![image](https://github.com/user-attachments/assets/802efec2-c5a5-49fc-bc94-924308f062ba)

- **Principle component 1**: PC1 is driven by `Farming` (negative contribution) and crop features such as `Avocado` and `Coffee` (negative contribution), `Male`(positive contribution), and `Female` (negative contribution). When observing our score plot, there is a cluster of cities that have a large positive PC1 value between 2.5 and 5. For example, mandera, mombasa, turkana, marsabit, wajir, isiolo, and garissa. This means that these observations either have a large negative `Farming` PC value, a large negative crop feature PC value (e.g., `Avocado`, `Coffee`, and `Tea`), a large positive `Male` PC value, and/or a large negative `Female` PC value. 

These observations overlap with our findings from our K-Means model results, wherein cluster 1 include counties such as Mombasa, Garissa, Wajir,...- which are all urban cities or towns. In other words, this cluster of counties is not a farming cluster and does not specialize in growing any crops i.e. a large negative `Farming` and/or crop-related features PC value. 

![image](https://github.com/user-attachments/assets/1115a2c2-1b5a-4f49-a759-546b9de9daf9)


- **Principle component 2**: PC2 is driven by fruit/nut-bearing crop features such as `Citrus`, `Mango`, `Coconut`, and `Cashew Nut` (negative contribution). When observing our score plot, there is a cluster of cities that have a large negative PC2 value between -3 and -5. For example makueni, kilifi, kwale, and lamu. This means that these observations either have a large positive `Citrus`, `Mango`, `Coconut`, and/or `Cashew Nut` PC value.

  ![image](https://github.com/user-attachments/assets/e1108760-137a-4074-abac-0bffb1be21d9)
   ![image](https://github.com/user-attachments/assets/35bd3534-2204-4ad5-91f7-523ad81b5cc8)


These observations overlap with our findings from our K-Means model results as well, wherein cluster 4 include counties such as Makueni, Kilifi, Kwale, and Lamu which are scounties that pecializes in cashew, coconut and mango production.

### Final PCs and information retained

From our findings through investigating the first 2 PCs and our Hierarchical Clustering Model, we observed that our data exhibits high variability, high separatedness, and rather complex patterns. This indicate that we might need to retain more variability to capture the nuances in the data. Therefore, we would suggest moving forward with 4 PCs, with which we will retain 75% of our original information.

# Code and plots
All codes, plots, and data can be found in the repository
