# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program

## Compilation

The code compiles and runs on my Mac. The Travis-CI build verifies that the code at least compiles with both g++ and clang:  
[![Build Status](https://travis-ci.org/stela/CarND-Path-Planning-Project.svg?branch=master)](https://travis-ci.org/stela/CarND-Path-Planning-Project)

## Valid Trajectories

The car appears to drive for any length without incidents, I never saw it fail sooner than the required 4.32 miles, the longest I had patience to view was 15 miles and 20 minutes driving without an incident. There is occasionally a problem when changing to a lane with a vehicle having a different speed than our car.

The car normally keeps the speed just under the 50 mph speed limit, it only goes slower when braking for a car nearby in front of it.

The acceleration indicated is usually not more than 2-3m/s^2, jerk also stays low. The values never reach 10.

The car manages to avoid collisions. Occasionally I have seen other car in the distance bump into each other, if something like that would happen near the car it might not be smart enough to escape such an unexpected situation.

The car manages to swiftly change lanes, it does so in less than 2 seconds I believe.

The car changes lanes when blocked ahead by a car in front of it, and at least one side is empty nearby the car, and it's safe to switch to. It does so smoothly thanks to the use of splines.


## Reflection
The paths are generated by combining a previously generated path's last two points, [see source code](src/main.cpp#L338-L349), with three more waypoints, 30, 60 and 90 meters ahead, [see source code](src/main.cpp#L352-L355). In case there are less than 2 previous path-points available, the car's current position and direction is used instead to generate the initial two points. The three last waypoints far ahead of the car are in the desired lane. The waypoints are fed to a [spline library](src/spline.h) to allow creating smoothly drivable path with points spaced out 20ms apart. 

The coordinate system is transformed so that the car is at its origin, see [main.cpp](src/main.cpp#L371-L372) before generating the spline, and after the 20ms-interval-points are generated, [transformed back](src/main.cpp#L404-L406). Frenet coordinates are [used to determine when to switch lanes based on the lane other nearby cars are in](src/main.cpp#L272-L316). 
