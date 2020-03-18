# zindi_womnx

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
