# kuka_gazebo
ROS package for running joint position simulation of the Kuka KR6 R900 sixx within Gazebo. 

## Credits
This package is inspired by work conducted by Sebastian Nagel, which in turn is based on work by Mark Culleton and Kevin Kelly.<br/>
https://github.com/SebNag/kuka_kr6r900sixx_moveit_gazebo_setup<br/>
https://github.com/ros-industrial/abb_experimental

## Install
The following is assuming a working ROS setup. Otherwise check out the article on ros.org on [installing and configuring your ROS environment](https://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment)

```sh
cd <path to catkin workspace>/src
git clone git@github.com:skrede/kuka_gazebo.git 
cd kuka_gazebo
catkin build
```

## Usage
Start the package by running 
```
roslaunch kuka_gazebo kr6_r900sixx_gazebo_joint_control.launch
```

The robot can be actuated within Gazebo by sending joint setpoints via the topics <br/>`/joint_a{n}_position_controller/command`

The KR 6 Agilus has six joints, and as such the topics are
```
/joint_a1_position_controller/command
/joint_a2_position_controller/command
/joint_a3_position_controller/command
/joint_a4_position_controller/command
/joint_a5_position_controller/command
/joint_a6_position_controller/command
```

## Test
Test the package by opening a terminal and publish a joint setpoint
```
rostopic pub -1 /joint_a1_position_controller/command std_msgs/Float64 "data: 1.57"

```
It should now move in Gazebo.
