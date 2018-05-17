# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program

## Compilation

The code compiles and runs on my Mac. The Travis-CI build verifies that the code at least compiles with both g++ and clang:  
[![Build Status](https://travis-ci.org/stela/CarND-Path-Planning-Project.svg?branch=master)](https://travis-ci.org/stela/CarND-Path-Planning-Project)

## Valid Trajectories

The car appears to drive for any length without incidents, after 15 miles and 20 minutes it was still driving without incident. With a shorter length of lanes left and right scanned than currently, there was occasionally a problem when changing to a lane with a vehicle having a different speed than our car.

The car normally keeps the speed just under the 50 mph speed limit, it only goes slower when braking for a car nearby in front of it.

The acceleration indicated is usually not more than 2-3m/s^2, jerk also stays low. The values never reach 10.

The car manages to avoid collisions. Occasionally I have seen other car in the distance bump into each other, if something like that would happen near the car it might not be smart enough to escape such an unexpected situation.

The car manages to swiftly change lanes, it does so in less than 2 seconds I believe.

The car changes lanes when blocked ahead by a car in front of it, and at least one side is empty nearby the car, and it's safe to switch to. It does so smoothly thanks to the use of splines.


## Reflection

