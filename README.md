# Sales Demand Forecasting for Shoe Distributor
Determining inventory levels are critical for any retail or online operation. 
If you are out of stock of a unit a customer wants, it is a missed opportunity that is most likely lost.
Therefore inventory levels are critical for any business. By using predictive analysis, 
it is possible to predict customers' future demand for product.

## Data
The raw data set for this project was retrieved from towardsdatascience.com and linked to an AWS S3 bucket. It is a collection of shoe sales over three years, representing 18 shops in 4 countries, including The United States, Canada, the United Kingdom, and Germany. The data set contains 14 features and 14,971 customer sales.

[Original Data](https://s3.us-west-2.amazonaws.com/public.gamelab.fun/dataset/Al-Bundy_raw-data.csv)

## Exploratory Data Analysis
When looking at the data, some of the relationships which can be determined are as follows:
Shoe size follows a normal distribution:

This means when ordering inventory, it should follow this ratio. In Men’s, for every three pairs of size 10(US) shoes, two pairs of size 9 and 11 should be ordered and 1 pair of size 12 and size 8. Subsequently in Women’s pairs the same ratio should exist with size 9 being the median. 

## Pre Processing

The first step in time series analysis is to do a series decomposition looking at trend, seasonality, and noise. Plotting the current sales data over time makes it difficult to tell at a glance any of these beyond a general trend.  


## Machine Learning Models

Several time-series analysis libraries, such as Arima, Sarimax, FBProphet, XGBoost, and TensorFlow, are appropriate for forecasting. 
We will apply multiple programs to the data, measure the accuracy of each, and determine the most appropriate one to use. 
We may even find that an ensemble method works the best.

I utilized the Python module statsmodel to decompose the plot and smooth out the data. 

After smoothing out the data we can definitely see a seasonal trend. 

This means that I would not utilize and Arima model, but instead start with a Sarimax model since it has a seasonal component to it. I started with a Sarimax model; however, it didn’t seem to capture an unexpected drop which occurred in the training set. 
I then went to an FBProphet model to see if it could handle the unexpected dip in sales better. The Prophet model seemed to anticipate the yearly trend much better than the Sarimax model. 

 
Upon cross validating the models, I found that the FBProphet model had a much lower Mean Absolute Percentage Error than the Sarimax model and that is the model I chose to utilize for the prediction. 

## Analysis

Utilizing the FBProphet model we could see that there is a general trend upwards over the coming two quarters. 
This would indicate that inventory levels should be slightly elevated from last years levels. 

## Future Improvements

* In the Future I would like to change this to a multivariate time series analysis by adding things like holidays into the model 
* Also since shoe model was part of the data set, I would like to see how sales coincide with the release of a new model.
