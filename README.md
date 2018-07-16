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

1. In main() I added 3 functions for predicting the behavior of neighboring vehicles, planning high-level behavior and generating a smooth trajectory of waypoints for the vehicle to traverse.
2. The prediction module uses sensor fusion data to track the nearest cars ahead and behind of the ego car in each lane. This information will be used by the behavior planner to determine if there is enough of a gap in neighboring lanes to perform a lane change.
3. The behavior planning module uses the output of the prediction module to determine the desired lane and speed for the ego vehicle. It makes this determination using logic-based rules. If there are no obstacles in the current lane the vehicle stays in the current vehicle, accelerating to the speed-limit if possible. On the other hand, if there are obstacles in the current lane, the ego vehicle seeks to make a lane change to a neighboring lane if it is feasible and desirable. A lane change is feasible if there is a gap big enough for the vehicle to move into the neighboring lane. A lane change is desirable if the target lane is moving faster or has more free space in front of the ego vehicle. If a lane change is not desirable or feasible, the ego vehicle stays in the current lane and reduces speed to match the vehicle in front of it. The behavior planner module outputs the desired lane and speed for the ego vehicle to the trajectory planner.
4. The trajectory planner module takes the the desired lane and speed and extends the previously planned trajectory as a smooth curve to incorporate the new target state. The construction of the trajectory planner follows the steps described in the project walkthrough video.


__*Results*__

The results of the Path Planning project demonstrating the car moving in autonomous mode around the Unity simulator track are shown below.

[![Path_Planning_Project](https://github.com/calvinhobbes119/Path-Planning-Project/blob/master/Untitled.png)](https://youtu.be/6ydnQEybQac)
