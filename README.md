Rice Identification
The identification of paddy rice is essential for understanding and estimating the status of food security at both regional and national levels.
This model has been developed to effectively identify the rice and non-rice areas within paddy fields in the Pangasinan region. It utilizes composite imagery with a spatial resolution of 10 meters derived from Sentinel-1 and Sentinel-2 satellite data.
The composite image and the ground point samples were processed in GEE and exported as an asset.
Hyperparameter Tuning
Hyperparameter tuning is the process of selecting the best hyperparameters for a machine-learning model to improve its performance. The goal is to find the optimal combination of hyperparameters.
Hyperparameter Tuning Process:
1-	Load the composite image that was exported as an asset
2-	 Create a function to Normalize Image Pixel Values it should be between 0 and 1, the formula is (x - xmin) / (xmax - xmin)
3-	Load the Gcps points that were exported as an asset
4-	Add a random column and split the Gcps into training (70%) and validation (30%) set
5-	Overlay the point on the image to get training data.
6-	Train a classifier (smileRandomForest)
Feature Importance
-	Run .explain() to see what the classifier looks like
-	Calculate relative importance using ee. Reducer.sum()
-	Create a FeatureCollection to be plotted as a chart 
Hyperparameter Tuning
-	Tune the number of trees parameter starting by 10 to 150 with an interval of 10 (10,150,10)
-	Tuning Multiple Parameters can be done together using nested map() functions ( numTrees and bagFraction)
-	Classifying a table instead of an image Classifiers work on both images and tables and export the result as CSV.
-	Alternatively, we can automatically pick the parameters that result in the highest accuracy
-	Use the optimal parameters in a model and perform final classification
-	Printing or displaying the image may time out as it requires extensive computation to find the optimal parameters, it is better to export the 'finalClassification' to Asset and import the result to view it.

