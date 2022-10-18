# CHILIpReading

The goal of this project is to achieve a distributed system for fast and accurate audio visual speech recognition (AVSR).

Two computers are used. A robot that will collect the data and a server that will do heavy processing step.

The two computers run on Ubuntu 20 using ros noetic and python3.

To connect the computers ros environments, you can follow [Husarnet tutorial](https://husarion.com/tutorials/ros-tutorials/5-running-ros-on-multiple-machines/).

![Distibuted Structure Graph](https://raw.githubusercontent.com/CHILIpReading/.github/main/images/distributed_structure.png)

For more information, see the report of the [project](https://github.com/CHILIpReading/.github/blob/main/report/David%20Roch%20Master%20thesis%20Distributed%20system%20for%20fast%20and%0Aaccurate%20visual%20speech%20recognition.pdf).


# Table of Contents  
[Robot Overview](#ro)  
[Server Overview](#so)  
[Visual speech recognition](#vsr)   
[Installation](#installation)   
[Launch](#launch)  
[Troubleshoot](#troubleshoot) 

<a name="ro"/> 

# Robot Overview

## Visual module
Responsible of taking images and to make sure that their transfer to the Video Module was correctly done.

## Audio module
Responsible of capturing sounds and to make sure that their transfer to the Video Module was correctly done.

## Evaluator
Feature added so that, instead of using the camera and microphone input, the system will use an mp4 video input. It will also take care of saving the processing time and results obtained.

<a name="so"/>

# Server Overview

## State Manager
Ensures that the actual state is well completed before deciding and setting the correct following state. It keeps the process timeline correct at all time and avoid being in non-predicted states.

## Video module
First responsible of receiving the images and sounds sent by the Visual and Audio modules to build a video out of them and then of using the video to get the prediction of the speech of it.

<a name="vsr"/>

# Visual speech recognition (VSR)
This is a forked repositories comming from [[1]](#1). It is used for the VSR part in the Video module.


<a name="installation"/>

# Installation
The following catkin workspace folder structure was adopted for this project on both computers:

```bash
├── build
├── devel
├── VSR
└── src
    ├── Audio_module
    ├── Evaluator
    ├── State_Manager
    ├── Video_module
    └── Visual_module
```

The VSR repo can be downloaded anywhere, but you have to setup the following environment path variable:
```cmd
export VSR_DIR=/path/to/vsr/folder/VSR
```

To install the python dependancies, you can clone the .github repo and execute
```cmd
pip install -r requirements.txt
```

<a name="launch"/> 

# Launch
To launch the full system, execute the following command (each command should be run on the computer wanted):
```cmd
roslaunch state_manager launchfile.launch
```
```cmd
cd VSR
rosrun video_module video.py 
```
```cmd
rosrun visual_module visual_module.py
```
```cmd
rosrun audio_module audio_module.py 
```

If you also want to run the Evaluator:
```cmd
rosrun evaluator evaluator.py 
```

<a name="troubleshoot"/> 

# Troubleshoot
## Deleting Husarnet
```cmd
sudo apt-get remove husarnet
sudo rm -r /var/lib/husarnet
```

# References
<a id="1">[1]</a> 
Ma, Pingchuan and Petridis, Stavros and Pantic, Maja (2021). 
[End-to-end audio-visual speech recognition with conformers](https://github.com/mpc001/Visual_Speech_Recognition_for_Multiple_Languages)
ICASSP 2021-2021 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), 7613-7617.
