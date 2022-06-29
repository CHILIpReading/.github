# CHILIpReading

The goal of this project is to achieve a distributed system for fast and accurate audio visual speech recognition (AVSR).

Two computers are used. A robot that will collect the data and a server that will do heavy processing step.

To connect the computers ros environments, you can follow [Husarnet tutorial](https://husarion.com/tutorials/ros-tutorials/5-running-ros-on-multiple-machines/)

![Distibuted Structure image](./../images/distributed_structure.png)

# Robot Overview

## Visual module
It will take images and send them in the wanted format through a ros topic to the computer.

## Audio module
It will take audio pulse and send them through a ros topic to the computer.

# Server Overview

## State Manager
It decides when to record or when to process the datas. It also contains and load the config as rosparam for the rest of the system.

## Video module
When the processing starts, it builds the video and process it using the PMaConformers repo.

# Visual speech recognition (VSR)
This is a forked repositories comming from [[1]](#1). It will be use for the VSR part.


## References
<a id="1">[1]</a> 
Ma, Pingchuan and Petridis, Stavros and Pantic, Maja (2021). 
[End-to-end audio-visual speech recognition with conformers](https://github.com/mpc001/Visual_Speech_Recognition_for_Multiple_Languages)
ICASSP 2021-2021 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP), 7613-7617.
