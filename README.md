# Neural Network Charity Analysis
## Overview
The purpose of creating this neural network was to create a machine learning binary classifier capable of predicted if an applicant would be successful if they were funded by Alphabet Soup. We were given a dataset containing over 34,000 past organizations who had recieved funding previously.

## Results
### Data Preproccessing
We start off by asking a few questions about our data to help shape it in preperation for our model:
* Which column(s) are considered the target(s) for our model?
* What column(s) are considered to be the features for your model?
* What column(s) are neither targets nor features, and should be removed from the input data?

Here is a list of all of our columns, and brief descriptions:
* EIN and NAME—Identification columns
* APPLICATION_TYPE—Alphabet Soup application type
* AFFILIATION—Affiliated sector of industry
* CLASSIFICATION—Government organization classification
* USE_CASE—Use case for funding
* ORGANIZATION—Organization type
* STATUS—Active status
* INCOME_AMT—Income classification
* SPECIAL_CONSIDERATIONS—Special consideration for application
* ASK_AMT—Funding amount requested
* IS_SUCCESSFUL—Was the money used effectively

Looking at our dataset, we find the corrisponding answers:
* IS_SUCCESSFUL would be considered our target, as this column displays whether an organization was successful
* AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT will serve as our features, and they bring a variety of important datapoints
* EIN and NAME just serve as identification, which our model wont need as it is not supposed to predict an applicants success based on name

### Compiling, Training, and Evaluating the Model
We had to start with a base model, and then use trial and error to optimize it in order to bring up our models accuracy. For our base model, we started with these specifications:
* Two hidden layers, each with 80 and 30 neurons respectively
* Used the ReLu activation function for initialization as well as the second layer
* Used the Sigmoid activation function for our final layer
* An accuracy of 53.12% was achieved

#### Layers and Neurons
We had chosen to start with 80 neurons as our dataset was quite large, so there was quite a bit of proccessing our model needed to do. So much so, that we included a secondary layer with much less neurons, 30, to attempt to fine-tune our initial attempt.

#### Activation Functions
Starting with ReLu sets up a base, as it scales from 0 to infinity. We had a large disbalance between T3 application types compared to others, so ReLu was chosen to handle it. For our models end point, Sigmoid is the perfect binary classification activation function, as the purpose of the model is to predict whether the applicant would be successful or not, a binary decision.

#### Initial Model Results
With an achieved accuracy of 53.12% and loss metric measured at 86.86%, this is not an effective model at all. Our threshold for success is set at 75% accuracy, with as minimal loss as possible.
Target Model Performance was not achieved.

### Optimizing our Model
In order to attempt to reach our Target Model Performance of 75% accuracy, we took a number of steps:
* Increased neurons within the hidden layers
* Added an additional hidden layer
* Changed our initial activation function
* Re-preproccessed our data

#### Increasing Neurons (optimized1)
By bumping the amount of neurons from 30 to 40 within the second layer, we saw a drastic jump in accuracy, to 64.42%. This seemed to be the sweet spot, as increasing it more lowered our accuracy. This is almost good news. The reason it is almost good news but not completely is that another metric increased: loss. Our loss value jumped from 86.86% to 108.68%. Increasing neurons did increase our accuracy, but due to the loss increase as well, perhaps the neurons should be increased elsewhere, bringing us to our next optimization.

#### Additional Hidden Layer (optimized2)
By adding an additional hidden layer to our previous change, containing 20 neurons, we saw a decrease in accuracy, to 63.67%. However, our loss metric dropped significantly, from the high 108.68% down to 65.32%, A step in the right direction. From this, we see that more layers and neurons won't do us much good, so we take a different approach: changing our activation functions.

#### Using Sigmoid (optimized3)
Sigmoid is amazing for binary classification, perfect for what we need in theory. Replacing all activation functions with Sigmoid, we find that this is not the optimization leap we were hoping for. The models accuracy drops to 52.92%, worse than our initial model! At this point, perhaps it is not the model we should be adjusting and tuning, but our input data to assist with any outliers the model might be confused with.

#### Expanded Bucketing (optimized4)
We had used bucketing in our preproccessing preparations in order to set up a cut-off point for what we could call "rare" occurances, as to not confuse our model with so many features. Looking back at our dataset, perhaps there were still too many features that it was getting confused on and assigning too much importance to, so we expanded our definition of what we considered "rare" occurances. Using our second optimized model with this new set of data, we managed to achieve 63.85% accuracy, an improvement from the second optimization, but still nowhere near our set 75% accuracy threshhold.

## Summary
Overall, our Deep Learning Model failed. It could not reach our threshhold regardless of our adjustments to layers, functions or the input data. An alternative model that would perhaps perform better than our own might be the LogisticRegression Model, as that model excels in binary classification with given targets, as our dataset contained.
