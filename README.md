# First Assignment of the Research Track 2 course (Robotics Engineering / JEMARO, Unige)

Litong Huang (5058374)

This README.md file is related to the first branch **action**, which it implements a ros action in order to control the robot movement in the environment. 


## Architecture of the system:

### Node: 
- PositionServer
- GoToPoint
- StateMachine (FSM)
- UserInterface

### Service:
- random position service
- start or stop the robot 
- drive the robot toward a point in the environment

### The launch file will open:
- The simulation environment
- The node PositionServer, which implements a random position service with random values for x, y, and theta, where x and y should be limited between some min and max values.
- The node GoToPoint, which implements a service to drive a robot toward a point in space (x,y) with angle (theta) in the environment. In this case, the node GoToPoint is modelled as a ROS action server. From the "go_to_point_action", it has an action to comunicate to gazebo with a subscriber and a publisher so that the position of the robot can be known, and decides whether a robot should run or stop. 
- The node FSM, which implements a service to start or stop the robot, and calls the other two services to drive the robot. In addition, it can also be implemented to cancel the goal when the related user command is received. The robot can be stopped only when it reaches a target.
- The UserInterface, which asks the user to start/stop the robot and communicates to the server in "state_machine". It calls the service implemented in the FSM node. The "state_machine" server also communicates to the server in "position_service" when a new random goal exists. In addition, it also communicate to the "go_to_point_action" action in order to create a new goal or delete the current goal.

## How to run the node:
Things to keep in mind: This branch should contain the same package in ROS, just like the workspace we created in class for ROS, and it needs to be inside the src folder. In the workspace, execute "catkin_make" for the directory to build code. Also, remember to source ROS in the bash file. 


The package contains the nodes and the simulation environment for controlling a mobile robot in the Gazebo simulation environment.

```
roslaunch rt2_ass1 sim.launch
```


