# CHILIpReading

The goal of this project is to have a robot using real-time lip reading to increase the accuracy of audio speech recognition.

To do that, two computers are used. One will be qualified as laptop which represent the robot and will mainly manage the data collection and the other one, the computer,has a GPU and will do the audio visual speech recognition (AVSR).

# Laptop repos overview

## camera
It will take images and send them in the wanted format through a ros topic to the computer.

## microphone
It will take audio pulse and send them through a ros topic to the computer.

# computer repos overview

## state_machine
It decides when to record or when to process the datas. It also contains and load the config as rosparam for the rest of the system.

## AVSR
When the processing starts, it builds the video and process it using the PMaConformers repo.

# Lipreading - PMaConformers repo

This is a forked repositories comming from [Pingchuan Ma work](https://github.com/mpc001/Visual_Speech_Recognition_for_Multiple_Languages). It will be use for the AVSR part.
