README: Market Regime Detection using Unsupervised Learning
===========================================================

🔍 Project Overview
-------------------
This project applies unsupervised learning techniques to identify hidden market regimes such as Trending, Mean-Reverting, Volatile, Stable, Liquid, and Illiquid behaviors. The analysis is based on both order book (depth20) data and trade volume data.

📁 Directory Structure
---------------------
trade_volume/       -> Folder containing trade volume .txt files  
depth20/            -> Folder with order book depth snapshots  
features/           -> Feature generation and rolling stats  
clustering/         -> Clustering logic (KMeans, GMM, HDBSCAN)  
visualizations/     -> Plotting regime evolution and insights  
report/             -> Final analysis and interpretations  

🧪 Step-by-Step Pipeline
------------------------

1. Data Merging and Preparation
- Read multiple trade volume `.txt` files and concatenated them into a single DataFrame.
- Parsed order book snapshots from `depth20/` directory.
- Merged both datasets based on timestamps.

2. Feature Engineering
- Midprice log returns  
- 30s rolling volatility  
- 10s rolling trade volume  
- Order Book Imbalance (OBI)  
- Bid-ask spread, microprice  
- Rolling skewness and kurtosis of returns  

3. Dimensionality Reduction
- Performed PCA to retain 95% of total variance.

4. Clustering Algorithms Applied
- KMeans (with sampled silhouette score)
- Gaussian Mixture Models (GMM)
- HDBSCAN ✅ (chosen as best method based on silhouette score)

5. Cluster Evaluation
- Computed silhouette scores
- Interpreted regimes based on mean feature profiles

6. Regime Labeling
- Manually interpreted cluster centers and assigned meaningful labels like:  
  Trending & Illiquid  
  Mean-Reverting & Liquid  
  Volatile & Stable  

7. Visualization & Insights
- Plotted regime evolution over time
- Overlaid regimes with price and volatility trends
- Created a regime transition matrix (Markov-style)

📊 Key Outputs
--------------
- Regime transition matrix
- Regime vs Time plot
- Feature-wise regime interpretations

📝 Final Report
---------------
See `report/Regime Detection Report` for detailed interpretation and visuals.

📌 Tools Used
-------------
- Python (Pandas, NumPy, Scikit-learn, HDBSCAN, Seaborn, Matplotlib)
- Jupyter Notebooks / Script-based pipeline

📚 Future Work
--------------
- Incorporate real-time regime detection
- Train models on intraday vs interday splits
- Extend features with market impact or sentiment scores

🧠 Author Notes
---------------
This project was developed as part of an ML internship task. The modular design allows for easy experimentation with clustering techniques and market interpretations.
