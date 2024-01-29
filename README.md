# deep-learning-challenge
GWU Module Challenge 21

## Background
The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With your knowledge of machine learning and neural networks, you’ll use the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.

From Alphabet Soup’s business team, you have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

*   `EIN and NAME` — Identification columns
*   `APPLICATION_TYPE` — Alphabet Soup application type
*   `AFFILIATION` — Affiliated sector of industry
*   `CLASSIFICATION` — Government organization classification
*   `USE_CASE` — Use case for funding
*   `ORGANIZATION` — Organization type
*   `STATUS` — Active status
*   `INCOME_AMT` — Income classification
*   `SPECIAL_CONSIDERATIONS` — Special considerations for application
*   `ASK_AMT` — Funding amount requested
*   `IS_SUCCESSFUL` — Was the money used effectively

## Overview
For this challenge, in addition to the original preprocessed data and model, the following 3 optimizations were completed to compare which is a better fitted model with less loss and high accuracy.

*   <b>For OPT1:</b> Removal of a feature(s), add additional target, and/or adding one additional hidden layer. 
*   <b>For OPT2:</b> APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT
    *   With more restricted binning and 2 additional layers with first having 15 neurons and second having 10 neurons using same activation as original model. Also increase the number of epochs to 50 from 100.
*   <b>For OPT3:</b> Same number of features from original model and use the top model suggested by Keras Tuner

In general the outcome of the original preprocessed data and model yielded similar accuracy and loss when compared against the 3 optimized models. The original model yielded a `Loss` of about 56% with an `Accuracy` of about 72.70%. The Losses and Acurracies obtained from the 3 optimization were:
*   `Opt1` => `Loss` - 55.57%, `Accuracy` - 72.83%
*   `Opt2` => `Loss` - 56.82%, `Accuracy` - 72.86%
*   `Opt3` => `Loss` - 55.10%, `Accuracy` - 72.87%

All in all, by removing features we would see a higher percentage in `Loss` with a lower `Accuracy` but we can supplement to reverse that by increasing the number of hidden layers and neurons. However, that would come at a higher cost of efficiency. As a result, it is recommended that we keep the preprocessing process the same as the original model and can simply add one or two additioanl layers with around the same amount of neurons in each.

-   The original Neural Network model can be located under the `Outputs` folder under the name `AlphabetSoupCharity.h5`.
-   The original working file is `AlphabetSoupCharity.ipynb` and the optimized models/additional trial models are located under `AlphabetSoupCharity_Optimization.ipynb`.
-   The `Starter_code` folder contains the original working template for the project.

## Results
-   Data Preprocessing
    *   The target(s) variable used for this project was: `IS_SUCCESSFUL`
        *   Note that `STATUS` was also tried and added into `Opt1` as well but ended with a high `Loss` and much lower `Accuracy` (not shown in the `AlphabetSoupCharity_Optimization.ipynb`). Due to the poor result, it was reverted back to single default target `IS_SUCCESSFUL`.
    *   The feature(s) used for this project were: `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, and `ASK_AMT`

-   Compiling, Training, and Evaluating the Model
    *   The neurons, layers, and activation functions were kept closely similar to what the original model was set up as. However, in the last optimization - `Opt3` - it was decided to used the number of layers, neurons, and different type of activation functions suggested by `Kerastuner`.
    *   Unfortunately, neither any of the four models reached the target performance of 75%. The one with best yield of `Accuracy` and `Loss` was from the `Opt3` which was based on the suggestion made from the `Kerastuner`.

## Summary
In closing, rather than trying to come up with a working model manually, it would be best to take advantage of `Kerastuner` and try for the top recommended model. But before doing so, it would be best to revisit the original dataset and have a better understanding of the date being presented. A few quesitons or actions could be done before proceeding with feeding the data to the model:

1)  Understand the business model and the data being presented more by discussing further with the data owner.
2)  Adding any additional features or observations that may be useful, this would mean having a better correlation between features and observations.
3)  Once having a better understanding of the data, a better ETL model is needed to improve the prediction.

It is true that we can help the model improve simply by increasing the number of hidden layers as well as neurons. However, by doing so we are losing efficiency and increase in costs that may result in only a small increment of accuracy overall.