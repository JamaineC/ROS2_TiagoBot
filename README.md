# Tiago Bot ROS2 State Machine – Maze Navigation & Object Handling  
## Project Overview  
This project is a **Robotic Applications** assignment from **Aberystwyth University**, focusing on **ROS2-based robotic control**. It involves developing a **C++ ROS2 state machine** to control a **Tiago Bot** in a simulated **Gazebo environment**. The project features **maze navigation using laser scanning**, **object detection and pickup**, **delivery to a target bin**, and a **finite state machine (FSM) architecture** to coordinate these tasks efficiently.  

## Prerequisites  
Ubuntu 22.04 LTS or compatible Linux distribution, ROS2 Humble or later, Gazebo & MoveIt!, Tiago Bot Simulation Package.  

## Installation & Setup  
Clone Required Packages: `cd ~/ros2_ws/src && git clone https://github.com/your-repo/jac105_ros360_cpp.git && git clone https://github.com/your-repo/ros360_moveit.git && cd ~/ros2_ws && colcon build --symlink-install && source install/setup.bash`  

Launch the Simulation: `ros2 launch jac105_ros360_cpp tiago_blocks.launch.xml track:=scenario23`  

Wait for the **Gazebo environment** to fully load and for the robot arm to enter its **tucked position**, then start the Tiago Bot Controller: `ros2 run jac105_ros360_cpp tiagoController`  

## State Machine Workflow  
The robot begins **maze navigation**, using **laser scan data** to detect turns and adjusting speed dynamically. Once the maze is completed, it enters **object alignment**, detecting **blue cubes** via ROS2 vision processing, adjusting head tilt and movement. It then moves to **arm control**, extending the robot arm for object pickup and gripping the cube. After picking up the object, it enters **backup mode**, reversing while keeping the object aligned, before transitioning to **object placement**, where it delivers the cube into a **green bin**. The state machine ensures structured and modular execution throughout the process.  

## Troubleshooting  
If the **simulation fails to launch**, ensure dependencies are installed and sourced correctly. If the **Tiago Bot does not move**, check if ROS2 topics are being published using `ros2 topic echo /servoing_cmd_vel`. If **object detection is not working**, verify the `/colour_detection/` topic outputs correct coordinates.  

## Future Improvements  
Enhancements could include **gripper functionality for varied object sizes**, **depth camera integration for more accurate object handling**, and **adaptive navigation using SLAM** for improved real-world application.  

## License  
This project is released for **educational and research purposes**. Contributions and improvements are welcome!  
