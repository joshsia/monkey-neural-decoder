# monkey-neural-decoder

Author: Joshua Sia

## About

Designing a neural decoder to estimate the trajectory of a monkey's arm. Neural activity in the form of spike trains is recorded using 98 neural units from a monkey's brain as it repeatedly performs an arm movement task. The monkey repeats the movement 100 times along each of 8 reaching angles. For each trial, the neural spiking data and the arm position are recorded from 300 ms before movement onset until 100ms after movement ends.

The task is to predict the coordinates of the arm in the *x*, *y* and *z* planes given the neural spike train data.

A visualisation of the neural spike train data is shown below as a raster plot. Each blue bar represents a neural spiking activity. The arm trajectories are also shown for the 8 reaching angles.

|            |           |
:-------------------------:|:-------------------------:
![raster](https://github.com/joshsia/monkey-neural-decoder/blob/main/img/raster_plot.png)  |  ![arm-position](https://github.com/joshsia/monkey-neural-decoder/blob/main/img/reaching_trajectories.png)

Two models are trained: (i) A logistic regression model for classification into the reaching angle, (ii) A neural network to predict the arm coordinates. For the logistic regression model, the classification accuracy was used to measure model performance. After the model makes a prediction of the reaching angle, the mean arm trajectory in the predicted angle is then used as the logistic regression model's "final" prediction in order to calculate the RMSE. For the neural network, the RMSE between the predicted and actual arm trajectories was directly computed.

The logistic regression model was able to classify the neural spike trains into the correct reaching angle with an accuracy of 98.05%, and had an RMSE of 53.09. Interestingly, most of its incorrect predictions come from the same region of space.

On the other hand, the neural network resulted in an RMSE of 27.56. Strangely, the region where the logistic regression model has low accuracy is the region where the neural network performs well.

|       Logistic Regression     |     Neural Network      |
:-------------------------:|:-------------------------:
![lr-model](https://github.com/joshsia/monkey-neural-decoder/blob/main/img/lr_incorrect_preds.png)  |  ![nn](https://github.com/joshsia/monkey-neural-decoder/blob/main/img/nn_preds.png)

## Credits

The data used in this project was collected by the laboratory of Prof. Krishna Shenoy at Stanford University, and was distributed by Prof. Claudia Clopath at Imperial College London as part of the Brain Machine Interfaces module.
