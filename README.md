# OENMS: An Octomap Based Exploration and Navigation Multi-robot System

This system focuses on exploration of unexplored areas. Currently the system supports single robot exploration.

This robot system contains 4 major components

- [Exploration Module]
- [Planning Module] 
- [Control Module] 
- [Client Module] 

   [Exploration Module]: <https://github.com/KalanaRatnayake/exploration_module>
   [Planning Module]: <https://github.com/KalanaRatnayake/planning_module>
   [Control Module]: <https://github.com/KalanaRatnayake/control_module>
   [Client Module]: <https://github.com/KalanaRatnayake/client_module>

And server system contains a single component

- [Server Module] 

   [Server Module]: <https://github.com/KalanaRatnayake/server_module>

And uses a separate module for performance evaluation on both server and robot systems

- [Evaluator]

   [Evaluator]: <https://github.com/KalanaRatnayake/evaluator>

for performance evaluation

<br>

## Basic Environment Setup

Follow the instructions and Install Ubuntu 18.04 and ROS melodic as explained in the respective webpages. When installing Melodic, "ros-melodic-full-desktop" is prefered.

Setup Git as follows

```sh
sudo apt update
sudo apt install git
```

Setup catkin_tools as follows

```sh
sudo apt install python-catkin-tools python-catkin-pkg
```

<br>

## Dependencies

Run the following commands to setup dependencies

```sh
sudo apt install python3-pip
python3 -m pip install --upgrade setuptools grpcio-tools
```

```sh
sudo apt install ros-melodic-multimaster-fkie ros-melodic-cv-bridge ros-melodic-vision-opencv ros-melodic-rtabmap ros-melodic-rtabmap-ros libpcl-dev ros-melodic-tf2*
```

<br>

## System setup

Create a ros workspace 

```sh
mkdir -p xavier/src
cd xavier/src
```

and clone following repositories to 'src' folder.

```sh
git clone https://github.com/KalanaRatnayake/oenms.git
git clone https://github.com/KalanaRatnayake/server_module.git
git clone https://github.com/KalanaRatnayake/client_module.git
git clone https://github.com/KalanaRatnayake/control_module.git
git clone https://github.com/KalanaRatnayake/exploration_module.git
git clone https://github.com/KalanaRatnayake/planning_module.git
git clone https://github.com/KalanaRatnayake/custom_msgs.git
git clone https://github.com/KalanaRatnayake/evaluator.git
git clone https://github.com/KalanaRatnayake/rviz.git
git clone https://github.com/KalanaRatnayake/simulation.git

git clone https://github.com/yujinrobot/kobuki.git
git clone https://github.com/yujinrobot/kobuki_desktop.git
git clone https://github.com/yujinrobot/kobuki_msgs.git
git clone https://github.com/yujinrobot/yujin_ocs.git
git clone https://github.com/ros-drivers/rgbd_launch.git

git clone https://github.com/turtlebot/turtlebot.git
git clone https://github.com/turtlebot/turtlebot_apps.git
git clone https://github.com/turtlebot/turtlebot_simulator.git
git clone https://github.com/turtlebot/turtlebot_msgs.git
git clone https://github.com/turtlebot/turtlebot_interactions.git
```

Run the following from the root of the workspace to setup missing dependecies.

```
cd ..

rosdep install --from-paths src --ignore-src -r -y
```

Run the following from the root of the workspace to build the workspace

```sh
catkin build
```

<br>


## Simulation of single qbot system using qbot

First start the simulation,

```sh
source devel/setup.bash
roslaunch simulations single_qbot_large.launch
```

To start the qbot's control systems,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot.launch
```

To start the RVIZ and visualizing system,

```sh
source devel/setup.bash
roslaunch rviz visualizer_single_qbot.launch
```

<br>

## Simulation of 2 qbot system

First start the simulation,

```sh
source devel/setup.bash
roslaunch simulations two_qbot_large.launch
```

To start the qbot 1's system,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot_tworobot_1.launch
```

To start the qbot 2's system,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot_tworobot_2.launch
```

To start the corrdinator server

```sh
source devel/setup.bash
roslaunch oenms server.launch
```

To start the Rviz and visualizing system,

```sh
source devel/setup.bash
roslaunch rviz visualizer_two_qbot.launch
```

<br>

## Simulation of 3 qbot system

First start the simulation,

```sh
source devel/setup.bash
roslaunch simulations three_qbot_large.launch
```

To start the qbot 1's system,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot_1.launch
```

To start the qbot 2's system,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot_2.launch
```

To start the qbot 3's system,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot_3.launch
```

To start the corrdinator server

```sh
source devel/setup.bash
roslaunch oenms server.launch
```

To start the Rviz and visualizing system,

```sh
source devel/setup.bash
roslaunch rviz visualizer_three_qbot.launch
```

<br>

## Simulation of single qbot system with manual control

First start the simulation,

```sh
source devel/setup.bash
roslaunch simulations single_qbot_large.launch
```

To start the rosbot's control systems,

```sh
source devel/setup.bash
roslaunch oenms simu_qbot_manual.launch
```

To start the RVIZ and visualizing system,

```sh
source devel/setup.bash
roslaunch rviz visualizer_single_qbot.launch
```