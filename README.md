# Neural_Network_Charity_Analysis
## Purpose of Analysis
AlphabetSoup is attempting to use Neural Network Deep Learning to vet contributions to certain organizations.  In the past, some have proven to be untrustworthy and either not used their contributions ethically or at all.  The Deep Learning model should predict which organizations will be trustworthy and which will be high-risk.  Target model performance is set at 75%

## Results
- **Target:**  The final column of the dataframe "IS_SUCCESSFUL" is the target.  This is the metric that determines if the contribution money was used effectively.  This column was set as the target while also being dropped from the features.

![01](https://user-images.githubusercontent.com/106561880/196081770-69d52a7d-9313-432f-bf72-b83bada54318.png)

- **Features:** The following columns were considered the features:  APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, ASK_AMT

- **Neither:**  The following columns were not useful to the data training set:  EIN, NAME, and SPECIAL_CONSIDERATIONS.  SPECIAL_CONSIDERATIONS were mostly inconsequential since the vast majority were listed as N.

![02](https://user-images.githubusercontent.com/106561880/196081812-92fde7fa-93aa-44c7-8e80-e5f590559b6a.png)


- **Binning:** To help improve performance, the following columns had outlying amounts binned into "Other" categories within their own columns: APPLICATION_TYPE, CLASSIFICATION, AFFILIATION, USE_CASE, and ORGANIZATION.  INCOME_AMT was also binned where all income amounts over 1M were bundled into one category.

- **Original Compilation, Training, and Evaluation:**  For the first attempt, the neural network model was built with 2 hidden layers, with 8 neurons in the first layer and 5 neurons in the second layer.  Relu activation functions were used since they generally perform well.  The output layer uses a sigmoid activation function.

![03](https://user-images.githubusercontent.com/106561880/196081828-f1253d90-5ac0-4bb0-b90b-0bb1ad3eb60c.png)

- **Original Results:**  Using 100 epochs, we did not meet our 75% goal.  Accuracy is at 72.7%.

![04](https://user-images.githubusercontent.com/106561880/196081843-24641aea-0563-459d-b319-eb09e6507753.png)

- **Additional Training Attempts:**  Some additional steps were mentioned above:
1. Additional binning and modifications to these columns: AFFILIATION, USE_CASE, ORGANIZATION, INCOME_AMT, SPECIAL_CONSIDERATIONS.
2. Neurons added to existing layers.  1st hidden layer increase to 16.  2nd hidden layer increase to 12
3. 3rd Hidden Layer was also added.
4. Activation functions were changed on 1st and 2nd hidden layers: to "elu" and "selu", respectively.

![05](https://user-images.githubusercontent.com/106561880/196081881-86032046-b731-4613-aaa9-cfc5178626de.png)

- **Additional Training Results:**  
There was minimal improvement.  Accuracy is at 72.8%.  The number of epochs was not updated.  Looking through the model training, there was minimal accuracy improvement even after the 5th epoch.

![06](https://user-images.githubusercontent.com/106561880/196081897-9a40e73e-d4c3-4c8f-a891-24537761fe36.png)

## Summary
Using the current Neural Network model.  We can accurately predict if a organization will effectively use contributions nearly 73% of the time.  However, is not up to the minimum goal of 75%.

While it was recommended to use a Deep Learning Model, it may be advantageous to use a Random Forest model.  It behaves similarly to a Neural Network and can more easily handle outliers.  Fewer modifications to the data may be necessary.  It is worth a shot to see if it improves on performance.

