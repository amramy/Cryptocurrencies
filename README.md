# Cryptocurrencies


## Overview: 

Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked for a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

The data needs to be processed to fit the machine learning models. Since there is no known output unsupervised learning will be used. The data will need to be preprocessing for PCA (Principal Component Analysis), reduce the data dimensions using PCA, clustering the Cryptocurrencies using K-means then visualizing the cryptocurrencies results. 

### Preprocessing the Data for PCA

* load the data
* Set the index to the "Unnamed" column
* Keep all cryptocurrencies that are being traded
* Remove the "IsTrading" column 
* Drop all null values. TotalCoinsMined column had 459 null values to drop.
* Keep rows were coins are mined. "TotalCoinsMined" column is more than zero
* Create DataFrame holding cryptocurrencies names
* Drop "CoinName" column from main dataset
* Use pd.get_dummies() to create variables for text features
* Standardize (aka: scale) the data with StandardScaler() with an array output


### Reducing Data Dimension Using PCA

* Use PCA to reduce dimension to three principle components
* fit_transform() pca compnents
* Create DataFrame with the three priciple compnents
<img width="496" alt="principle component df" src="https://user-images.githubusercontent.com/111904266/220728915-0fd0db9d-0168-4ff0-8fc7-8cbe09e16566.png">

### Cluster Cryptocurrencies Using K-Means

* Find the best value for K by calculating the inertia for the range of K values with a for loop
* Create an Elbow Curve to find the best value for K 
<img width="638" alt="Elbow curve" src="https://user-images.githubusercontent.com/111904266/220729295-d15f22ab-3bdd-4e3c-a1d2-1b9ac7c47027.png">    

* Initialize the K-Means model
* Fit the K-Means model
* Predict the K-Means model as an array
* Create a new DataFrame that includes predicted clusters and cryptocurrencies features
  * Include the "CoinName" column
  * Include the "Class" column
  

### Visualize Cryptocurrencies Results

* Create a 3D-Scatter with the merged PCA and clusters data

<img width="659" alt="3D scatter " src="https://user-images.githubusercontent.com/111904266/220730501-f9d4ff9d-4894-40cc-a5d0-6b4ecefc7085.png">

* Create a table with tradable cryptocurrencies
* There are 532 tradable cryptocurrencies
* Scale and fit the tradable cryptocurrencies with MinMaxScaler().fit_transform()
* Create a new DataFrame with tradable cryptocurrencies and index from original dataset
  * Include the "CoinName" column
  * Include the "Class" column
* Create a hvplot.scatter using x="TotalCoinsMined" and y="TotalCoinSupply" from the newst DataFrame

<img width="644" alt="hvplot scatter" src="https://user-images.githubusercontent.com/111904266/220731881-edec7450-31af-464f-9838-374df8f92d06.png">


**** 
### Resources: 
**Data:**
crypto_data.csv retrieved from crytocompare.com   
  https://min-api.cryptocompare.com/data/all/coinlist
  
**Technologies used:**
* Jupyter Notebooks
* Python
* Pandas
* hvplot
* plotly
* sklearn
  * StandardScaler
  * MinMaxScaler
  * PCA
  * KMeans


