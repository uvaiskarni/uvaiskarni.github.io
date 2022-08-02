---
layout: page
title:  Air Quality Prediction Using Machine Learning
description: Developed an LSTM based model to forecast multivariant air pollutants  
img: assets/img/projects/Centralized_Federated.png
importance: 2
---

Air pollution is a major issue these days that is causing increasing concern among the general public. As a result, several air quality stations measure the pollutants in the air, and numerous prediction models have been developed to predict the amount of these pollutants within a given time frame (in the next hour, for example). First, a centralized model was developed to forecast the number of specific pollutants (for example, PM10 and NO2) within the next hour. Following the validation of the centralized model's accuracy (by comparing predictions to real values), the federated model was built, in which a server distributes a specific model to all clients participating in the federation for training. For this model, the Tensorflow library and Federated implementation were used to carry out the experiments required to test the federated learning approach.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Centralized_Federated.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
<div class="caption">
    Simple representation illustrating Centralized and Federated  
</div>

The project's purpose was to move away from centralized data - massive aggregations of data from various air quality monitoring sites. This is the standard method for training supervised machine learning models, but it necessitates the transmission and aggregation of massive amounts of raw data. Instead, the we looked at federated learning, which allows a machine learning model to be developed at each station and then combined through federated averaging.

Because such a setup does not yet exist, we modelled it using data from the Swedish Meteorological and Hydrological Institute (SMHI). Despite the fact that the dataset was centralized, we separated it by weather station (Stockholm E4/E20 Lilla Essingen, Stockholm Sveavägen 59, Stockholm Hornsgatan 108, and Stockholm Torkel Knutssonsgatan) and trained four independent models that were then combined using federated averaging.

A baseline for comparison is usually required when validating results. To validate against the federated models, a high performance centralized model was constructed in this situation. We used the same train/test/validation dataset, but we investigated it in different ways, with different features and machine learning model architectures. Testing such models in parallel and evaluating them based on their accuracy - specifically, Symmetric Mean Absolute Percentage Error (SMAPE) and Mean Absolute Error (MAE) - allowed the students to cover a wide range of parameters and converge to a high performing centralized model.

The centralized LSTM model that performs the best is the one that is used in the competition where it predicts the 4 gases values with approximately 0.5 SMAPE values for each one. Therefore, this model is suitable for a generalized one and can behave well enough for every gase for different datasets.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/LSTMModel.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     General architecture of our 24 hours prediction model
</div>


The LSTM model contains 3 layers: First layer is the LSTM-sequence Layer which takes the 24 hours sequence of the all features coming from the one hot encoding and outputs the 24 hours sequence of the future values. Secondly, the middle hidden layer also is an LSTM layer but it performs sequence to vector predictions where instead of sequence to sequence predictions. Since the outputs are future hourly values for only the next hour, the output shape is only 24 which come from the last LSTM cell as output. Lastly, it contains the dense layer getting the next 24 hours values as predictions for all 4 gases therefore, the number of output values are 24 x 4 = 96 values.

Sevral experiments were carried out, details of one of the them is provide. For the experiment elaborated bwelow four features: PM10, NO2, NOX, PM2.5 are used. The
previous 24 hours values are utilised to predict the next 24 hours of the PM10, NO2, NOX, PM2.5. Based on features availability across the different stations the following 4 stations were used for the experiments and they are #8779, #8780, #8781 and #18644. 2017 is used as Training data used, 2018 as validation and finally 2019 as Testing data. The data is normalized using Min Max Normalisation between range 0 and 1. All NaNs and negative values are replaced with zeros. Regarding the model structure it is sequential with two LSTM layers each with 24 LSTM units followed by a dropout layer with 0.2 dropout value. Along with adam as optimizer, Mean absolute error as loss, Early stopping with patience 10 is used to auto terminate training.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Centralized_Traning.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     Training vs Validation loss plot
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/NO2Actual_Vs_Predicted.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     NO2 Actual Vs Predicted values
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/NOXActual_Vs_Predicted.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     NOX Actual Vs Predicted values
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/PM2.5Actual_Vs_Predicted.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     PM 2.5 Actual Vs Predicted values
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/PM10Actual_Vs_Predicted.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     PM 10 Actual Vs Predicted values
</div>
