# baxter_teleop
teleoperate baxter based on kinect
This document includs:
1. Instruction to install kinect openni driver and on ubuntu 14.04 with ROS indigo.
2. Demo of baxter teleoperation with kinect

=================================================================
Part I
=================================================================
Install openni driver and download openni-launch openni-tracker
OpenNI
components
sudo apt-get install git-core cmake freeglut3-dev pkg-config build-essential 
libxmu-dev libxi-dev libusb-1.0-0-dev doxygen graphviz mono-complete

download the OpenNI-Package 

mkdir ~/kinect

cd ~/kinect

git clone https://github.com/OpenNI/OpenNI.git

compiling the package: 

cd OpenNI/Platform/Linux/CreateRedist/

chmod +x RedistMaker

./RedistMaker

Installation of OpenNI: 

cd Final

tar -xjf OpenNI-Bin-Dev-Linux-x64-v1.5.7.10.tar.bz2

cd OpenNI-Bin-Dev-Linux-x64-v1.5.7.10

sudo ./install.sh

SesorKinect 

The way to get this part to work is similar to the OpenNI guide: 

Download Package: 

cd ~kinect/

git clone git://github.com/ph4m/SensorKinect.git

Compile Package with Redit: 

cd SensorKinect/Platform/Linux/CreateRedist/

chmod +x RedistMaker

./RedistMaker

And finally Installation: 

cd Final

tar -xjf Sensor-Bin-Linux-x64-v5.1.2.1.tar.bz2

cd Sensor-Bin-Linux-x64-v5.1.2.1

sudo ./install.sh

NITE 

You can download this Library for example from the link mentioned in the post above. Don't forget that only the Versions NITE v1.5.2.21 and NITE v1.5.2.23 will work for you. Paste the nite-folder into your kinect-folder to keep track of your data:

cd ~kinect/nite/

 tar -xjf NITE-Bin-Dev-Linux-x64-v1.5.2.23.tar.bz2

cd NITE-Bin-Dev-Linux-x64-v1.5.2.23

sudo ./install.sh

Now that everything around ROS is installed, we should reboot the system: sudo reboot

ROS-Components 

After we have installed all peripheral Libraries, we can install the required ros-core-components for OpenNI-usage. But we have to delete one library before that because of some issues that will appear otherwise: sudo apt-get remove libopenni-sensor-pointclouds0

Next Step is the Installation of the ROS-Kinect-driver: 

sudo apt-get install ros-indigo-openni-launch

sudo apt-get install ros-indigo-openni-camera

Finally we can install the openni_tracker to our usually workspace (for example the catkin_ws): cd ~catkin_ws/src

git clone https://github.com/ros-drivers/openni_tracker.git 

cd ..

Usage You need to start several terminals to work with the tracker.
Terminal_1: roslaunch openni_launch openni_launch

Terminal_2: rosrun openni_tracker openni_tracker

Terminal_3: rosrun rviz rviz

Now your system should be set up to be able to track a person under Indigo and to visualize the result. It would be very nice if someone could try to follow the instructions to verify this way.

========================================================
Part II
=======================================================
run baxter evironment variable setup script ./baxter.sh

roslaunch baxter_teleop baxter_teleop.launch

start to control you baxter with kinect.



