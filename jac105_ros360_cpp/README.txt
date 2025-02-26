READ ME
-----------

The way to run my tiago bot controller for this assignment is to do the following:

STEP 0 : - Download ros360_moveit and put it the same directory as the jac105_ros360_cpp package if you dont have it already

STEP 1 : - Open a Ubuntu terminal 

STEP 2 : - type the following and hit enter: ros2 launch jac105_ros360_cpp tiago_blocks.launch.xml track:=scenario23

STEP 3 : - Wait for gazebo environment to fully load and for the robot arm to enter its tucked position 

STEP 4 : - Open another Ubuntu terminal

STEP 5 : - type the following and hit enter: ros2 run jac105_ros360_cpp tiagoController