# EnergyForcasting

With this project, the intent is to find trends in the energy draw data from the dataset and use that to determine the energy draw in the future. There are several approaches to this and I list my approach below.

## Architecture of the predictive system designed

When modeling this relationship, the first thing that came to mind was using a model that has the ability to understand time series data. The specific model that I used is in pytorch forecasting: Here, I choose to go with an auto-regressive model implimented with LSTM. I do this because I want to model future time steps from the data that I am given and the analysis needs to be able to predict in a manner that mimics the patters in the data. Having an LSTM model helps keep track of long term relationships found in the data and here, the reccurent nature of the model and the data is key. 

## Preprocessing

I used data from kaggle for this, where I used hourly energy consumption data spanning 2001-2018. This data came with two columns, the datetime values and the values at each time period. The date time values were put together, so the first thing that I did was split these two then went ahead and segmented the timesteps into pieces that can be used for training.

## Ways to ensure that the data is being well-predicted.

Measuring the predictive power of a model is not a trivial task, that said there are a lot of tools at our disposal that can help with the process. I tracked the correlation and the standard deviation of the data to first see if the work to be done is on good data. From there, I trained a baseline model and found its absolute mean error to see what the data looks like at the beginning.

In the training process, I optimized the learning rate by running it trhhough a tuner to find the optimal value. After training, I plotted the predictions ontop of the validation dataset and observed the predicted behavoior and how close it was to mirroring what the data was expressing.

## Data (other than the building draw) that could be used to improve the system.

Other values that can be important is the weather, where we can find higher draw depending on the extremeness of the weather, and if possible average aage of appliances in a given area. The latter is more subtle, but the reasoning behind it is that older machines tend to have higher power draw and that could be reflective of the trends we might see that arent explained by the weather or other localities.
