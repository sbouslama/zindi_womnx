# zindi_womnx

Third place solution of the challenge. In case you want to discover the other winner's solution, please take a look at this blog [post](https://zindi.africa/learn/meet-the-winners-of-the-womxn-in-big-data-south-africa-female-headed-households-in-south-africa-challenge)

## Motivation
The objective of this challenge is to build a predictive model that accurately estimates the % of households per ward that are female-headed and living below a particular income threshold by using data points that can be collected through other means without an intensive household survey like the census.

This solution can potentially reduce the cost and improve the accuracy of monitoring key population indicators such as female household headship and income level in between census years. The winning solutions will be made publicly available at the end of the competition.

## Data
you can download the data via the ZindiPlateform

Files available for download:

- Train.csv - is the dataset that you will use to train your model.
- Test.csv - is the dataset on which you will apply your model to. This dataset contains the same variables as the test data except there is no target. This is what you are predicting.
- SampleSubmission.csv - is an example of what your submission file should look like. The order of the rows does not matter, but the names of the wards must be correct.
- VariableDefinitions.csv - is the full list of variables and their explanations.
Starter_Notebook.ipynb - this is a notebook to start you on this challenge. Link to notebook on Google Colab.

Take note that the variables:

"lat" and "lon" are the locations of the CENTER POINTS of the wards.
"ADM4_PCODE" is the ward code used to find the ward polygon in the shapefile available here.
When you download this file you should have a new folder called `zaf_adm_2016SADB_OCHA_SHP` that we will
be using to extract new features 

##  Approach taken:

### Processing:

The data was clean and didn't need any pre-processing steps. Most of the features were highly skewed. I applied the Box-Cox Transformation so that we have more normal-distribution for most of the features, but this technique didn't improve the results.

### Feature Engineering:

I tried to engineer many features but only a few of them helped to get better results:
- Clusters: I created 10 clusters of the regions using K-means ( ++impact)
- Concatenate features that show the disposal of luxury items (++impact)
- Area of the top administrative levels (third and second levels) (+impact)
- Dimensionality reduction for dwelling and languages features (No impact so I dropped)
- Average distance of the center of regions to some POIs of different categories such as 'Facilities', 'Education Facility', Public Transport, etc. (tended to overfit on training dataset so I dropped)
- Target encoding features
### Models

I ran different gradient boosting problems but the Catboost model was the best.
For the individual model cross-validation, I used random CV row selections of data. The CV score tended to differ from the public leader-board score and this was due to the difference between the administrative levels between the train and test set.
### Hyperparameter Tuning:

Effective hyperparameter tuning proved to be a very large challenge in this project since the CV score and the leader-board was not correlated.
What were the things that made the difference for you that you think others can learn from?

### Seed Diversification: 
Trying different random seeds when training the model because of the non-correlation between the CV score and the leader-board.

