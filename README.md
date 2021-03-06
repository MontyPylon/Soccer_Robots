# Soccer Robots
This repository contains all top-level ROS packages for my autonomous soccer robots project. The size and shape of these robots are cube shaped with dimensions approximately 11.5x11.5x9 cm^3. All the robot parts are 3D printed, with the only exceptions for the wheels and tracks which were purchased from Pololu. The robots positions are tracked using OpenCV color recognition, and commands are sent to the robots via UDP packets. Below are some sample images of the robots.

<p align="center">
  <img src="http://i.imgur.com/n0Dbfh6.jpg" width="400"/>
  <img src="http://i.imgur.com/T1JxGsI.jpg" width="400"/>
  <img src="http://i.imgur.com/2LMFLc8.jpg" width="400"/>
  <img src="http://i.imgur.com/ACQWQDa.jpg" width="400"/>
</p>

## Installation

### ROS

This project is built for ROS Kinetic on Ubuntu 16.04, which you can [install here](http://wiki.ros.org/kinetic/Installation/Ubuntu).

Then, make sure the ROS_DISTRO environment variable is set correctly:

```
echo $ROS_DISTRO
```

It may already be.  If not, issue this shell command:

```
$ export ROS_DISTRO=kinetic
```

Next, create a workspace and clone the source repositories:
```
$ source /opt/ros/$ROS_DISTRO/setup.bash
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ git clone https://github.com/MontyPylon/soccer_robots.git
```

Install all dependencies:
```
$ rosdep install --from-paths src --ignore-src --rosdistro $ROS_DISTRO -y
```

Then, build everything:
```
$ cd ~/catkin_ws
$ catkin_make
$ source devel/setup.bash
```
If everthing was installed correctly, the project should build with no errors, and is ready to launch!

### Arduino IDE

In order to upload the sketches to the robots, the Arduino IDE must be installed, which can be [downloaded here](https://www.arduino.cc/en/Main/Software).

Once the software is downloaded, navigate into the folder it was downloaded in and run the following command in a shell.
```
$ cd <path to arduino>
$ ./install.sh
```

After it is installed, the ESP-8266 libraries must be installed. First, open the Arduino IDE, click on File --> Preferences, then add the following link to the Additional Boards Manager URL's: http://arduino.esp8266.com/stable/package_esp8266com_index.json

Finally, go to Tools --> Board --> Boards Manager, search for "esp8266", and install the library.

### Additional Drivers

Before we can access the camera, we need to install it's drivers. Run this command to install the necessary drivers:
```
$ sudo apt-get install v4l-utils
```

