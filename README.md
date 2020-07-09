# SML Nexus Simulator
ROS package of SML Nexus robot Gazebo simulation. Provides a Gazebo plugin to simulate holonomic drive.

## Usage
Run one nexus robot by using the following command line:

`roslaunch sml_nexus_gazebo sml_nexus_world.launch`

### Dependencies
* sml_nexus_description (part of the [sml_nexus repo](https://github.com/KTH-SML/sml_nexus)) for the robot URDF model
* Gazebo7 or Gazebo9

### Gazebo plugin
* sml_nexus_ros_force_based_move:

  Outputs a force and a torque on the base link of a robot, using a velocity command as input and a proportional controller. Includes check for both Gazebo7 and Gazebo9 compatibility.

	* **Subscribed topic**
		* `/cmd_vel` (`geometry_msgs/Twist`)

		  Receives velocity command as a Twist message. The plugin will only process the linear velocity on the x and y-axis and the angular velocity on the z-axis

	* **Published Topics**
		* `/odom` (`nav_msgs/Odometry`)

		  Odometry from Gazebo model pose and velocity.

## Todo
* Implement range sensor
* Namespace and multi-robots
* Simulated inacurracy of odometry
