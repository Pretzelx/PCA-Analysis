# Human Protein Sequence Analysis

In this project I attempt to analyse human protein sequences using clustering techniques to explore their subcellular locations. The analysis focuses on cytosolic and membrane proteins, utilising sequence features such as aromaticity and isoelectric point to cluster and visualise these proteins.

## Dataset

The dataset used is `uniprotkb_organism_id_9606_AND_reviewed_2024_09_03.tsv`, which contains protein sequences and their subcellular locations. I obtained this datset from Uniprot [https://www.uniprot.org/] and searched **"(organism_id:9606) AND (reviewed:true) AND (length:[80 TO 500])"**

## Methodology

1. **Data Preprocessing**:
   - **Subcellular Location Filtering**:
     - Proteins were classified into **cytosolic** (cytoplasm) and **membrane** (cell membrane) locations.
   
2. **Feature Extraction**:
   - For each protein sequence, the following features were extracted using the `Bio.SeqUtils.ProtParam` library:
     - **Aromaticity**: The proportion of aromatic amino acids.
     - **Isoelectric Point**: The pH at which the protein has no net charge.

3. **Standardization**:
   - Features were standardized using `StandardScaler` to ensure equal weighting in clustering.

4. **Clustering**:
   - **KMeans Clustering** was performed with different numbers of clusters to determine the optimal number using the elbow method.
   - **Optimal Clusters**: Based on the elbow method, 4 clusters were chosen for the final analysis.

5. **Dimensionality Reduction**:
   - **PCA (Principal Component Analysis)** was used to reduce the feature space to 2 dimensions for visualization.

6. **Visualisation**:
   - **Elbow Method**: A plot of WCSS (Within-Cluster Sum of Squares) versus the number of clusters to identify the optimal cluster count.
   - **PCA Plot**: A scatter plot of the first two principal components colored by cluster membership.

## Results

1. **Elbow Method Plot**:
   - The elbow plot helps in determining the optimal number of clusters. The "elbow" point indicates the number of clusters where the addition of more clusters yields diminishing returns in WCSS.

   ![image](https://github.com/user-attachments/assets/8863fa49-af00-4d0e-b745-ee798d7f788f)


2. **PCA Clustering Plot**:
   - The PCA plot visualizes the clustering results in 2D space. Each point represents a protein sequence, colored by its assigned cluster.

![image](https://github.com/user-attachments/assets/e057b937-33cd-43ce-89e5-0c509fc386eb)



## Interpretation

- **Elbow Method**: The optimal number of clusters is identified by locating the "elbow" in the WCSS plot. This helps in balancing between model complexity and clustering quality.
  
- **PCA Plot**: The clustering results are visualized in two dimensions. Different clusters represent distinct groups of proteins based on their sequence features. This visualization helps in understanding how well-separated the clusters are and whether the features used are effective in distinguishing between the subcellular locations.


## Requirements

- `pandas`
- `scikit-learn`
- `numpy`
- `matplotlib`
- `biopython`


 
