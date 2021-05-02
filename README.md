# Cryptocurrencies
# Project Overview
You and Martha have done your research. You understand what unsupervised learning is used for, how to process data, how to cluster, how to reduce your dimensions, and how to reduce the principal components using PCA. It’s time to put all these skills to use by creating an analysis for your clients who are preparing to get into the cryptocurrency market.

Martha is a senior manager for the Advisory Services Team at Accountability Accounting, one of your most important clients. Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked you to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

The data Martha will be working with is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what Martha is looking for, she has decided to use unsupervised learning. To group the cryptocurrencies, Martha decided on a clustering algorithm. She’ll use data visualizations to share her findings with the board. This project consists of four technical analysis deliverables;

* Deliverable 1: Preprocessing the Data for PCA
* Deliverable 2: Reducing Data Dimensions Using PCA
* Deliverable 3: Clustering Cryptocurrencies Using K-means
* Deliverable 4: Visualizing Cryptocurrencies Results
# Resources
* Data Source: `crypto_data.csv`
* Data Tools/Software: Python 3.8.5, Jupyter Notebook 6.1.4, Pandas

# Deliverable 1: Preprocessing the Data for PCA
>Using your knowledge of Pandas, you’ll preprocess the dataset in order to perform PCA in Deliverable 2.

### Requirements
1. The following five preprocessing steps have been performed on the `crypto_df` DataFrame:
    * All cryptocurrencies that are not being traded are removed 
     ![1](https://user-images.githubusercontent.com/76136277/116799776-73083c00-aac9-11eb-9f40-85acaca8ebcd.PNG)

    * The `IsTrading` column is dropped 
    ![2](https://user-images.githubusercontent.com/76136277/116799779-7ac7e080-aac9-11eb-94af-6b36e4228613.PNG)

    * All the rows that have at least one null value are removed 
    ![3](https://user-images.githubusercontent.com/76136277/116799793-82878500-aac9-11eb-8807-e708286f4efd.PNG)

    * All the rows that do not have coins being mined are removed 
    ![4](https://user-images.githubusercontent.com/76136277/116799798-8adfc000-aac9-11eb-9a10-dd11105ec09d.PNG)

    * The CoinName column is dropped 
    ![5](https://user-images.githubusercontent.com/76136277/116799804-903d0a80-aac9-11eb-9d31-9ae0da04614f.PNG)

2. A new DataFrame is created that stores all cryptocurrency names from the `CoinName` column and retains the index from the `crypto_df` DataFrame 
![6](https://user-images.githubusercontent.com/76136277/116799813-b5317d80-aac9-11eb-8a1b-9773fd80bf11.PNG)

3. The `get_dummies()` method is used to create variables for the text features, which are then stored in a new DataFrame, `X` 
![7](https://user-images.githubusercontent.com/76136277/116799816-bbbff500-aac9-11eb-92e7-b3a04058bfa0.PNG)

4. The features from the `X` DataFrame have been standardized using the StandardScaler `fit_transform()` function 
![8](https://user-images.githubusercontent.com/76136277/116799834-dd20e100-aac9-11eb-99c3-f727495dffd1.PNG)

# Deliverable 2: Reducing Data Dimensions Using PCA
>Using your knowledge of how to apply the Principal Component Analysis (PCA) algorithm, you’ll reduce the dimensions of the `X` DataFrame to three principal components and place these dimensions in a new DataFrame.

### Requirements
1. The PCA algorithm reduces the dimensions of the `X` DataFrame down to three principal components.
![9](https://user-images.githubusercontent.com/76136277/116799924-87006d80-aaca-11eb-9092-6b1d6134167a.PNG)

2. The `pcs_df` DataFrame is created and has the following three columns, `PC 1`, `PC 2`, and `PC 3`, and has the index from the `crypto_df` DataFrame
![10](https://user-images.githubusercontent.com/76136277/116799929-8c5db800-aaca-11eb-9732-50da0ca5f8bc.PNG)

# Deliverable 3: Clustering Cryptocurrencies Using K-means
> Using your knowledge of the K-means algorithm, you’ll create an elbow curve using `hvPlot` to find the best value for K from the `pcs_df` DataFrame created in Deliverable 2. Then, you’ll run the K-means algorithm to predict the K clusters for the cryptocurrencies’ data.

### Requirements
* The K-means algorithm is used to cluster the cryptocurrencies using the PCA data, where the following steps have been completed:
  * An elbow curve is created using `hvPlot` to find the best value for K 
  ![a](https://user-images.githubusercontent.com/76136277/116800127-3a1d9680-aacc-11eb-98cd-129e885e5f60.PNG)

  * Predictions are made on the K clusters of the cryptocurrencies’ data 
  ![b](https://user-images.githubusercontent.com/76136277/116800135-4570c200-aacc-11eb-96e6-f9785d30f2e2.PNG)

  * A new DataFrame is created with the same index as the `crypto_df` DataFrame and has the following columns: `Algorithm`, `ProofType`, `TotalCoinsMined`, `TotalCoinSupply`, `PC 1`, `PC 2`, `PC 3`, `CoinName`, and `Class` 
![c](https://user-images.githubusercontent.com/76136277/116800139-528db100-aacc-11eb-9ed4-e1105f4be2b8.PNG)


# Deliverable 4: Visualizing Cryptocurrencies Results
>Using your knowledge of creating scatter plots with Plotly Express and `hvplot`, you’ll visualize the distinct groups that correspond to the three principal components you created in Deliverable 2, then you’ll create a table with all the currently tradable cryptocurrencies using the `hvplot.table()` function.

### Requirements
1. The clusters are plotted using a 3D scatter plot, and each data point shows the CoinName and Algorithm on hover 
![d](https://user-images.githubusercontent.com/76136277/116800238-54a43f80-aacd-11eb-890f-f27ca9355c86.PNG)
![newplot](https://user-images.githubusercontent.com/76136277/116800241-61c12e80-aacd-11eb-8e70-21f3fa3e6444.png)

2. A table with tradable cryptocurrencies is created using the `hvplot.table()` function 
![e](https://user-images.githubusercontent.com/76136277/116800277-afd63200-aacd-11eb-9b88-26ef8b023866.PNG)

3. The total number of tradable cryptocurrencies is printed 
![f](https://user-images.githubusercontent.com/76136277/116800291-cf6d5a80-aacd-11eb-9805-3f0b4ba077b4.PNG)

4. A DataFrame is created that contains the `clustered_df` DataFrame index, the scaled data, and the `CoinName` and `Class` columns
![g](https://user-images.githubusercontent.com/76136277/116800318-06dc0700-aace-11eb-8458-bcb492b77fd5.PNG)

5. A `hvplot` scatter plot is created where the X-axis is "TotalCoinsMined", the Y-axis is "TotalCoinSupply", the data is ordered by "Class", and it shows the CoinName when you hover over the data point.
![h](https://user-images.githubusercontent.com/76136277/116800323-0fccd880-aace-11eb-83cc-8696c0dcebb0.PNG)
![bokeh_plot (1)](https://user-images.githubusercontent.com/76136277/116800327-16f3e680-aace-11eb-9546-34115bf121d0.png)

