# ID2223 - Lab 1
by Annysia Dupaya and Lennart Roth

The aim for our lab is to create an air quality forecast dashboard for the town of Eimsbüttel, Germany. 

## Base Lab
For the base portion of the lab, we used the historical air quality and weather data of the town. The information for this is split into two feature groups "air quality" and "weather". We then get the latest (today's) information and insert it into the feature groups. 

We then use the features from the feature groups to create a feature view, which is used to train the model. After splitting the data into train and test sets, we use XGB Regressor as our basis and have our training data fit into the model.

Finally, after the model is trained, we create our predictions (notebook 4). With our batch data and the model we have created. We use /modelname/.predict() to generate the predictions for the next ten days.

### Running Daily
After making sure the lab runs well locally, we use Github Actions to schedule notebooks 2 and 4 to run daily. The results of the daily runs can be found in the Github Pages for this project [here](https://chinadupaya.github.io/mlfs-book/air-quality/).

## Comparison over time
For the base lab, which we will now call Version 1, we were successful into creating an air quality forecasting tool for the selected town. Our model performance modeling tool shows that while the predictions follow the trend of how the air quality moves, it is not completely accurate. We can improve it by introducing a "rolling days" feature in the next section.

## Rolling Days Feature
The rolling days feature uses the latest information from the last three days to create a "trend" feature that the model can use to give more accurate forecasts.

We insert a rolling mean in our air quality feature group. For the historical data, this means disregarding the oldest three days but having the rest of the data contain a "pm25_lagging" feature. Since the historical data is from 2019, we still have more than enough historical data to use from.

When it comes to forecasting (notebook 4), we first get the rolling mean using historical data for the first prediction. For its succeeding data, we get the new rolling mean, then predict for the next day. We do this iteratively until we reach our forecasted 10 days.

With a trend feature introduced, the accuracy of the forecasts is far closer to the actual quality in a given day. The bottom-most iamge of the [Github Page](https://chinadupaya.github.io/mlfs-book/) compares both Versions 1 and 3, showing the results for three are far closer to that of Version 1.

---

# mlfs-book
O'Reilly book - Building Machine Learning Systems with a feature store: batch, real-time, and LLMs


## ML System Examples


[Dashboards for Example ML Systems](https://featurestorebook.github.io/mlfs-book/)

## Course Comparison

| Course                         | MLOps | LLLMs             | Feature/Training/Inference | Working AI Systems | Focus |
|--------------------------------|-------|----------------------------|--------------------|------------------|
| Building AI Systems (O'Reilly) | Yes   | Fine-Tuning & RAG | Yes                        | High               | Project-based, Software Engineering, Fundamentals    |
| [Made With ML](https://madewithml.com/)                   | No          | Yes   | No                         | No                 | Software Engineering, Model Training   |
| [7 Steps MLOps](https://www.pauliusztin.me/courses/the-full-stack-7-steps-mlops-framework)            | Yes   | Separate Course    | Yes                        | Low                | Learning Tools and Project    |
