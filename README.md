# M2P07-Regression-Project-Canadian-Rental-Market<br>
<br>

### Data Preparation<br>
Several regression models were trained on a dataset of rental listings obtained from rentfaster.ca . The dataset contained around 25000 data points, providing ample data for train-test splits. Data was cleaned up to standardize categorical and numerical values in preparation for feature encoding. Missing values were imputed using SimpleImputer; dropping of missing values was avoided as much as possible to preserve data integrity. Numerical values were imputed with median values and categorical values were imputed with mode values. Irrelevant metadata like rentfaster_id, posting url etc. were removed; I also excluded address data since latitude and longitude accounts for location; I excluded availablity date because it does not really impact rental prices, knowing that rental prices are influenced by financing costs of the asset and construction costs.
<br>
<br>
Visualization of the correlation of the cleaned up numerical features with the target value of rental price showed a strong correlation with sq foootage and number of baths. This aligns with our experience. Square footage itself has a strong correlation with number of beds and baths. To keep things simple, I treated all these 3 as separate features instead of devising interaction terms to account for their mutual interaction. 

### Model training<br>
A simple MLR model and several cross-validated models were trained to compare performance. All the models showed almost similar performance, which was surprising since models like LassoCV and ElasticNetCV penalize overfitting when the feature set is as large as this. <br>
<br>
To test if something went wrong with the polynomial conversion of latitude and longitude, I trained the models again after excluding these features. <br>
<br>
The residual plot improved when we excluded the polynomial features, but the metrics got worse. In both cases, the residual plot showed the models performed well at rents upto $4000 but got worse at higher rents. <br>
<br>
### Performance on unseen data<br>
I sampled 9 unseen data points from rentfaster.ca .  I did this sampling manually, so it was not possible to achieve the same level of diversity in the values as the training dataset. I considered a residual of < $500 as acceptable; 3 out of 9 datapoints passed this test. Prediction accuracy of 33% where all of the predicted values exceeded the unseen target variable by a few thousand dollars indicates overfitting may have taken place. I suppose 9 data points is not enough to assess the reliability of the model. The feature engineering of this dataset must be revisited to find the root cause of overfitting.

