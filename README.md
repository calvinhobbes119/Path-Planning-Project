# Model-Predictive-Control
Udacity Self-Driving NanoDegree Term 3 Project on Path Planning

## Project: Model-Predictive-Control [![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---
This project implements Path Planning for Udacity's Self Driving Car Nanodegree. It comprises of (A) prediction module to predict the behavior of neighboring vehicles to our ego car, (B) behavior planner to describe the desired high-level behavior such as lane and speed for the ego vehicle and (C) trajectory planning module which translates the high-level behavior into a smooth trajectory.

Code changes
---
For this project I made the following changes to the starter code.

__*main.cpp*__

1. I transformed the telemetry data by converting the speed _v_ into m/s from mph.
2. I converted the waypoints from map-coordinates to vehicle coordinates by applying a matrix transformation, and fit a 3rd order polynomial function to the waypoints. The coefficients of this polynomial _f_ will be provided to the MPC solver to predict the optimal control trajectory for minimizing a cost function.
3. To determine the state parameters _CTE_ and _psi_, we use _f(0)_ and _f'(0)_.
4. The state vector and best-fit polynomial coeffs are fed to the MPC solve routing.
5. The MPC solve routine returns the actuator settings for the next time step, as well as the predicted optimal trajectory which minimizes the cost function over _N_ timesteps.
6. The steering actuator value is normalized by _deg2rad(25)_ to convert the steering value to be between _[-1,1]_.
7. The MPC predicted trajectory is returned to the Unity simulator as a json message for visualization purposes.


__*Results*__

The results of the MPC project demonstrating the car moving in autonomous mode around the Unity simulator track are shown below.

[![MPC Project](https://github.com/calvinhobbes119/Model-Predictive-Control/blob/master/Untitled.png)](https://youtu.be/6ydnQEybQac)
