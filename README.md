# Lane-Keeping-Assist-on-CARLA
## Introduction
<p align="center">
  <img  src="https://github.com/paulyehtw/Lane-Keeping-Assist-on-CARLA/blob/master/controller_output/CARLA.png">
</p>

This is a module assgnment from Motion Planning for Self-Driving Cars course of Self-Driving Cars Specialization on Coursera.org.

This assginment implements Lane Keeping Assist function by applying pure pursuit and Stanley methods for lateral control and PID controller for longitudinal control using Python as the programming language.

The waypoints and corresponding velocities for the track are pre-defined.

To realize this function, the open sourse simulator [CARLA](http://carla.org) is introduced.

## Prerequisites

First CARLA must be installed on your machine, the CARLA loader requires **Ubuntu 16.04 or later** to run

Please go through **CARLA-Setup-Guide-_Ubuntu_.pdf** and install CARLA and all other dependencies properly.

[CARLA Simulator can be downloaded here](https://d18ky98rnyall9.cloudfront.net/3dXfty7_EemFOA6Hm29iNA_de05a1c02eff11e9821ed19f5bd73b7b_CarlaUE4Ubuntu.tar.gz?Expires=1561680000&Signature=gfcHtRXSaqJsud-I3iOefXmlTSgiKse0nIb-QwQkMNOADAO2EFcggW4HtCYIjIi~5UsMLdcIrnlS3i9Qj7GhOkapph14Uw-C9j2xxhN0I7go5UrBWaEfv2pJkAfm41uywjH1QPmSj6YiRtUiMn67p7rcxvjLb3llMzLGvPdbzmM_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A) (This version of Carla is around 0.8.4 which is hugely different with the latest version 0.9.5. From Carla 0.9.0, there is no PythonClient folder.)

## Dependencies

Tested in python 3.5

- numpy==1.16.4
- pygame==1.9.6
- matplotlib==3.0.3

## How to run it

First clone this repository and put it under **PythonClient** directory.

### 1. Load the simulator

Open a terminal, move to `CarlaSimulator` folder.

Then run

`
./CarlaUE4.sh /Game/Maps/RaceTrack -windowed -carla-server -benchmark -quality-level=Low -fps=30
`
### 2. Run the LKA controller

Open another terminal and do `cd ~/opt/CarlaSimulator/PythonClient/lane-keep-carla-old`.

(optional) do `sudo apt-get install python3-tk` in case you do not have `Tkinter` module.

Run `python code/waypoint_follower.py` to execute the controller(default is MPC control method)

To select 3 different control methods:

MPC - `pythonn code/waypoint_follower.py --control-method MPC`

Stanley - `pythonn code/waypoint_follower.py --control-method Stanley`

Pure Pursuit - `pythonn code/waypoint_follower.py --control-method PurePursuit`

The vehicle should starting driving and following the track.

## Simulation results

The images shown below is the result of vehicle trajectory(MPC, Stanley and Pure Pursuit method).

The green line is the track(ground truth) and the orange line is the trajectory.

<p align="center"><b>MPC Method</b>
  <img  src="https://github.com/xpharry/lane-keep-carla-old/blob/master/controller_output/trajectory_MPC.png">
</p>

<p align="center"><b>Stanley Method</b>
  <img  src="https://github.com/xpharry/lane-keep-carla-old/blob/master/controller_output/trajectory_Stanley.png">
</p>

<p align="center"><b>Pure Pursuit Method</b>
  <img  src="https://github.com/xpharry/lane-keep-carla-old/blob/master/controller_output/trajectory_PurePursuit.png">
</p>
