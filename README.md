# Cricket Player Performance Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/asim-ibn-aziz/cricket-player-segmentation/blob/main/Cricket_Model.ipynb)
[![nbviewer](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.org/github/asim-ibn-aziz/cricket-player-segmentation/blob/main/Cricket_Model.ipynb)

## Objective

The project aims to analyze cricket player performance data using clustering techniques to identify player segments based on their batting statistics.

## Data Preparation

The dataset includes batting statistics of various cricket players. Key attributes considered for analysis include Matches (Mat), Innings (Inns), Not Outs (NO), Runs (Runs), Batting Average (Ave), Balls Faced (BF), and Strike Rate (SR). Initially, the data is standardized using StandardScaler to ensure uniformity in scale across variables.

## Hopkins Statistic

To assess the clustering tendency of the dataset, the Hopkins statistic is computed. This statistic measures the spatial randomness of the data points, with values closer to 1 indicating a high tendency to cluster.

## K-Means Clustering

K-Means clustering is employed to partition the dataset into clusters based on player performance attributes. The number of clusters is arbitrarily set to 4. K-Means iteratively assigns data points to the nearest cluster centroid and updates the centroids until convergence.

## Cluster Quality

We compute the silhouette score on the standardized features to quantify separation and compactness of clusters. Higher is better (real-world tabular data commonly lands around 0.2–0.6 depending on structure).

## Interpretation

Once clustering is performed, the players are assigned cluster IDs based on their similarity in batting statistics. The clusters can be analyzed to understand different player segments and their respective performance characteristics.

## Visualization

A dendrogram is plotted using hierarchical clustering to visualize the distance between player clusters based on batting strike rate and average. This dendrogram helps identify natural groupings or clusters within the data.

## Outcome

By clustering cricket player performance data, the project aims to uncover distinct player segments based on their batting statistics. This analysis can provide valuable insights for team management, talent identification, and strategic decision-making in cricket.

## Outputs

- `player_clusters.csv`: Two-column export mapping each `Player` to their `Cluster_ID` (0–3). Useful for filtering, joining to full stats, and sharing with downstream tools.
- Notebook visuals: scatter `Ave` vs `SR` colored by cluster; dendrogram for an alternative similarity view.
- Metrics: Hopkins statistic (cluster tendency) and silhouette score (cluster quality).

## Highlights

- Clear clustering tendency (Hopkins ≈ 0.76)
- Four data-driven player segments via K-Means (k=4)
- Visual explanations: `Ave` vs `SR` scatter and dendrogram
- Exported `player_clusters.csv` for easy sharing and downstream use

## Results (previews)

![Ave vs SR scatter](../assets/scatter_ave_sr.png)

![Dendrogram](../assets/dendrogram.png)

## Findings (quick take)

- Cluster 0: Balanced averages with moderate strike rates; steady contributors.
- Cluster 1: Higher averages and experience; consistent top-order profiles.
- Cluster 2: High-volume run scorers; many matches/innings, seasoned performers.
- Cluster 3: More aggressive strike rates; impact players with faster scoring.

## Libraries Used (and why)

- numpy: Fast array math used under the hood for scaling and model input.
- pandas: Data ingestion (`Cricket.csv`), cleaning, feature selection, grouping, export to `player_clusters.csv`.
- matplotlib.pyplot: Base plotting utilities (figures, layout, rendering).
- seaborn: High-level plots; cluster scatter of `Ave` vs `SR` for easy visual separation.
- datetime: General-purpose datetime utilities (light usage in this analysis).
- scikit-learn (sklearn): `StandardScaler` for feature scaling; `KMeans` for clustering; `silhouette_score` for cluster quality.
- scipy.cluster.hierarchy: Linkage and dendrogram to visualize hierarchical relationships between players.

## How to Run (Cursor/Jupyter)

1. Open `Cricket_Model.ipynb` and select your Python kernel (the project `.venv`).
2. Run all cells. This will compute Hopkins, fit K-Means, create visuals, and write `player_clusters.csv` to the project folder.
3. Review cluster profiles (per-cluster means) and visuals to label/interpret each segment.

## Author

- Asim — data analysis and clustering, notebook and visuals, documentation.
