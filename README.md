# Cyptocurrencies

## Overview 
Create a report that include what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

## Purpose
Use unsupervised learning to analyze crypto_data csv,  process the data to fit the machine learning models and group the cryptocurrencies with clustering algorithm. 

## Results

### Deliverable 1: Preprocessing the Data for PCA

- First we load and read in the crypto_data.csv and create Pandas DataFrame named crypto_df. Then, we  selected features that help us find patterns or groups considerating the knowledge we need to glean from running an unsupervised learning model. We kept all the cryptocurrencies that were traded and removed unnecesary data like; IsTrading column, CoinName column, rows with at least one null value and rows with coins that haven't been mined. 

- Use get_dummies() method to create variables for the two text features, Algorithm and ProofType, and store the resulting data in a new DataFrame named X and StandardScaler fit_transform() function to standardize the features from the X DataFrame

***crypto_df***

![Screenshot 2022-12-14 at 10 38 43 PM](https://user-images.githubusercontent.com/110786136/207773906-854af1ca-b01b-419c-8030-f77ef108ce77.png)

### Deliverable 2: Reducing Data Dimensions Using PCA

- Initialize PCA model with PCA method to reduce the dimensions to three principal components.

- Create a new DataFrame named pcs_df that contain the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.

***pcs_df***

![Screenshot 2022-12-14 at 10 36 55 PM](https://user-images.githubusercontent.com/110786136/207773665-ec307167-5dec-496a-8bcc-4f9102698dfc.png)

### Deliverable 3: Clustering Cryptocurrencies Using K-means

- Use pcs_df DataFrame and create a elbow curve with hvPlot to find the best value for K .
- K value for this elbow curve is 4.

***Elbow Curve***
![Elbow Curve](https://user-images.githubusercontent.com/110786136/207769652-b5eaea16-bc76-4645-9477-f374a6a59c86.png)

- With pcs_df DataFrame we run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies data

- Concatenating the crypto_df and pcs_df DataFrames on the same columns and named the new DataFrame clustered_df. We also add CoinName that hold the names of the cryptocurrencies and a new column named Class that holds the predictions of model.labels

### Deliverable 4: Visualizing Cryptocurrencies Results

- Scatter plots with Plotly Express and hvplot to visualize the distinct groups that correspond to the three principal components in pcs_df.

***3D Scatter Plot***
![3D Scatter plot](https://user-images.githubusercontent.com/110786136/207770563-a4e3f207-78e5-407f-88f6-ed8a30b5b5d3.png)

***Scatter Plot***

![Scatter plot](https://user-images.githubusercontent.com/110786136/207770579-b37a7a8d-8d8b-4d33-b778-10b1695ec352.png)
