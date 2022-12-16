# Solidworks-URDF-Gazebo-ROS

## Sources
http://wiki.ros.org/sw_urdf_exporter/Tutorials/Export%20an%20Assembly

URDF from fusion 360: https://www.youtube.com/watch?v=ufYxkNnEFYw

URDF from solidworks: https://www.youtube.com/watch?v=PIxHKowQ-wc

https://www.youtube.com/watch?v=anMymsvJKJI&t

Writing and controlling a SDF car: https://www.theconstructsim.com/how-to-build-a-differential-drive-simulation/

Gazebo plugins: https://classic.gazebosim.org/tutorials?tut=ros_gzplugins#JointPoseTrajectory

Some stack solutions : https://answers.gazebosim.org//question/6540/my-wheeled-robot-model-sometimes-flies-up-into-the-air-while-driving-why/

## SDF Car
using https://www.theconstructsim.com/how-to-build-a-differential-drive-simulation/ , I built a package diff_drive_gazebo that has a SDF file of a 2 wheeled differential bot. I added a Differential plugin to the SDF file and launch files to launch the bot into gazebo and control it with keyboard. Make sure to copy the turtlebot3_teleop package into the same workspace as the SDF bot package.

Type the following commands in different terminals after entering the workspace and sourcing it

``` bash
roslaunch diff_drive_gazebo main.launch
```
![Screenshot (731)](https://user-images.githubusercontent.com/106007058/208167622-9aac7c00-e369-4806-9155-e1391541c268.png)


``` bash
roslaunch diff_drive_gazebo keyboard_teleop.launch
```
![Screenshot (733)](https://user-images.githubusercontent.com/106007058/208167728-d0dfa70e-5ed6-4ca0-a2b3-e1d168564f11.png)

## URDF IGVC Bot
You can find the assembly files in the repo
After creating a URDF package and trying to spawn the bots into gazebo and solving many errors in the way, we learnt 
1) xml file structure of a URDF file
2) all links and joint names should be different and at every joint parent and child links and the joint type should be defined properly or else it will create parse errors

So we launched the bot using the command:
``` bash
roslaunch Assem2 gazebo.launch
```
![Screenshot (728)](https://user-images.githubusercontent.com/106007058/208169126-54d348a3-0659-4a67-bf87-a6d8b061c3e7.png)

But the bot is not moving even after adding the differential plugin and publishing commands through the teleop node
![Screenshot (730)](https://user-images.githubusercontent.com/106007058/208169732-d5a04325-2191-465e-8f07-a265a7830369.png)

 Also, after about 1-2 minutes, the bot starts flying and rotating in the air even when we do not give it any velocity.
 ![Screenshot (729)](https://user-images.githubusercontent.com/106007058/208169918-94d2e5c6-220d-4ce8-83fd-4a0fd89a51ef.png)


## URDF IGVC Car
``` bash
roslaunch 4wheeledrobo gazebo.launch
```
I added a skid_ steer plugin. Even this bot is not moving when given velocity through teleop node. It just oscilltes about its intial position.
![Screenshot (727)](https://user-images.githubusercontent.com/106007058/208170035-9d5527ab-3e0d-4a81-945a-47b4d832d725.png)

