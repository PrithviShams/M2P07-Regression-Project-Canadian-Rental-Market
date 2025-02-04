# M2P07-Regression-Project-Canadian-Rental-Market<br>
<br>

### Data Preparation<br>
Several regression models were trained on a dataset of rental listings obtained from rentfaster.ca . The dataset contained around 25000 data points, providing ample data for train-test splits. Data was cleaned up to standardize categorical and numerical values in preparation for feature encoding. Missing values were imputed using SimpleImputer; dropping of missing values was avoided as much as possible to preserve data integrity. Numerical values were imputed with median values and categorical values were imputed with mode values. Irrelevant metadata like rentfaster_id, posting url etc. were removed; I also excluded address data since latitude and longitude accounts for location; I excluded availablity date because it does not really impact rental prices, knowing that rental prices are influenced by financing costs of the asset and construction costs.
<br>
<br>
Visualization of the correlation of the cleaned up numerical features with the target value of rental price showed a strong correlation with sq foootage and number of baths. This aligns with our experience. Square footage itself has a strong correlation with number of beds and baths. To keep things simple, I treated all these 3 as separate features instead of devising interaction terms to account for their mutual interaction. 

### Model training<br>

