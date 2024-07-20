# CryptoClustering
Module 11
This data we looked at the was for crypto currenncy market, we provided a PCA and KMeans Algoritms to this data set.

PREPARE THE DATA
---------------------------------------------------------------------------------------------------------------------------
We imported the csv into the project under market_data_df and printed out the following dataframe:

![Alt text](image_clustering/intialdataframe.PNG)

After we describe() the data, then we started to transform the data. We used StandardScaler from Sklearn preprocessing 
library and hit market_data_df with .fit_transform() and created a scaled data frame of market_data_scaled. We then take
the index from the market_data_df, and bring that to the market_data_scaled and we will use this for our machine leanring 
models. 

![Alt text](scaleddataframe.PNG) 

FIND THE BEST VALUE FOR K USING THE ORIGNIAL SCALED DATAFRAME
---------------------------------------------------------------------------------------------------------------------------
The next section is find the best K for KMeans clustering, using a loop function. K is saved as a range of numbers for the
fof loop to call on. The range is set from 1, 11 meaning we should have ten numbers to try and see the best results. We 
then append the inertia_ values into a list. Then make a dictionary for keys being the range number used, and the inerita_
values to use in a data frame. After we visulaize the results. I might be wrong on this but we are using an elbow curve 
but I think we want convergence? Here is the plot. 

![Alt text](elbowcurve.PNG)

question: "What is the best value for `k`?"
answer: "4 where the elbow curves."

CLUSTER CRYPTOCURRNCIES WITH K-MEANS USING THE ORIGINAL SCALED DATA
---------------------------------------------------------------------------------------------------------------------------
This is were we will use the 4 value for our new KMeans model, the parameters for the function call is (n_clusters=4,
random_state=1). The model is then fit with our scaled data frame (market_scaled_df). After use the market_scaled_df for
a model.predict and saved under k_lower. We make a new data frame using copy from the market_scaled_df, and add a new column
['Predicted Clusters'] from k_lower and print the new data frame

![Alt text](scaleddataframe.PNG)

We also visualize the predicted column.

![Alt text](scaleddataframe.PNG)

OPTIMIZE CLUSTERS WITH PRINCIPAL COMPONENT ANALYSIS
---------------------------------------------------------------------------------------------------------------------------
This section we are going to use PCA, Principal Component Analysis. We intialize our function call with PCA(n_components=3)
after the data is fit_tranformed using our scaled market_scaled_df. We use the pca.explained_variance_ratio to show our 
variance values. I will include a picture of the variance values and question with answer.

![Alt text](varianceratio.PNG)

After we find the variance values the three PCA models and then turned into a dataframe using the fit_transform data, 
and using columns PCA1, PCA2 and PCA3 for our columns. and the index is set to the same index as the original df. Then we
visual the table.

![Alt text](pcadf.PNG)

FIND THE BEST VALUE FOR K USING THE PCA DATA.
---------------------------------------------------------------------------------------------------------------------------
Just like KMeans to find the best k value we will do the same thing for finding the best value of K for PCA. k_pca is created
into a list of range values 1-10. The a for loop will use the k_pca values and fidn the best PCA model to use. At the end of 
the for loop the inertia_ vlaues are saved to a list. A dictionary is also created to store the k_pca values with the inertia 
values. After we are done we create a new dataframe and look at the reults.

![Alt text](pcaelbow.PNG)

question: "What is the best value for `k` when using the PCA data?"
answer: 4
question: "Does it differ from the best k value found using the original data?"
answer: "No both models seem to like the 4 value for both models"

CLUSTER CYRPTOCURRENCIES WITH K-MEANS USING THE PCA DATA
---------------------------------------------------------------------------------------------------------------------------
For the final call of the PCA model we use a KMeans model and set the values, n_clusters=4 and random_state=1. We fit the 
data using our pca dataframe and use predict on the dataframe. and print the results. Then make a copy of the pca dataframe
and create a new column ['Predicted Clusters'] and print the results. 

![Alt text](pcapredict.PNG)

Visualize our predictions.

![Alt text](pcavis.PNG)

DETERMINE THE WIEGHTS OF EACH FEATURE ON EACH PRINCIPAL COMPONENT
---------------------------------------------------------------------------------------------------------------------------
We use pca.components_.T to show our array of values, and create a new dataframe using this array and after visualize our 
weights. 

![Alt text](pcaweights.PNG)

