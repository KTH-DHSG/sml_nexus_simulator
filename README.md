# SML Nexus Simulator
ROS package of SML Nexus robot Gazebo simulation. Provides a Gazebo plugin to simulate holonomic drive.

## Usage
Run the simulation for one nexus robot by using the following command line:

`roslaunch sml_nexus_gazebo sml_nexus_world.launch`

To launch two nexus robots, use the following launch file:

`roslaunch sml_nexus_gazebo sml_nexus_multi.launch`

## Dependencies
* sml_nexus_description (part of the [sml_nexus repo](https://github.com/KTH-SML/sml_nexus)) for the robot URDF model
* Gazebo7 or Gazebo9

## Launch files
* **sml_nexus_world.launch:** Launches Gazebo and spawn one nexus robot.

     - **`use_sim_time`** Tells ROS nodes asking for time to get the Gazebo-published simulation time, published over the ROS topic /clock. Default: `true`.
     
     - **`gui`** Launch the user interface window of Gazebo. Default: `true`.
     
     - **`headless`** Enable gazebo state log recording. Default: `false`.

* **sml_nexus_multi.launch:** Launches Gazebo and spawn two nexus robots with their namespace. This launch file aims to provide an example for multi-robot simulation.

     - **`use_sim_time`** Tells ROS nodes asking for time to get the Gazebo-published simulation time, published over the ROS topic /clock. Default: `true`.
     
     - **`gui`** Launch the user interface window of Gazebo. Default: `true`.
     
     - **`headless`** Enable gazebo state log recording. Default: `false`.


* **spawn_one_nexus.launch:** To be included in a launch file to spawn a nexus robot.

     - **`robot_name`** Robot name used as namespace for the spawned robot. Default: `nexus0`.
     
     - **`pose_x`** x coordinate (in m) of the robot spawn pose. Default: `0`.
     
     - **`pose_y`** y coordinate (in m) of the robot spawn pose. Default: `0`.


## Gazebo plugin
* sml_nexus_ros_force_based_move:

  Outputs a force and a torque on the base link of a robot, using a velocity command as input and a proportional controller. Includes check for both Gazebo7 and Gazebo9 compatibility.

	* **Subscribed topic**
		* `/cmd_vel` (`geometry_msgs/Twist`)

		  Receives velocity command as a Twist message. The plugin will only process the linear velocity on the x and y-axis and the angular velocity on the z-axis

	* **Published Topics**
		 * `/odom` (`nav_msgs/Odometry`)
		
	  	  	Odometry from Gazebo model pose and velocity.
		  
		 *  `/front_sensor` (`sensor_msgs/Range`)
		
	  		Front ultrasonic range sensor distance
		
	 	*  `/left_sensor` (`sensor_msgs/Range`)
		
	  		Left ultrasonic range sensor distance
		
	 	*  `/rear_sensor` (`sensor_msgs/Range`)
		
	  		Rear ultrasonic range sensor distance
		
	 	*  `/right_sensor` (`sensor_msgs/Range`)
		
	  		Right ultrasonic range sensor distance
		
