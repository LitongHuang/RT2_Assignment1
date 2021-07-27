# First Assignment of the Research Track 2 course (Robotics Engineering / JEMARO, Unige)

Litong Huang (5058374)


## Architecture of the system:

### Node: 
- PositionServer
- GoToPoint
- StateMachine
- UserInterface

### Service:
- random position service
- start or stop the robot 
- drive the robot toward a point in the environment

### The launch file will open:
- The simulation environment
- The node PositionServer, which implements a random position service with random values for x, y, and theta, where x and y should be limited between some min and max values
- The node GoToPoint, which implements a service to drive a robot toward a point in space (x,y) with angle (theta) in the environment
- The node FSM, which implements a service to start or stop the robot, and calls the other two services to drive the robot. The robot can be stopped only when it reaches a target
- The UserInterface, which asks the user to start/stop the robot, and calls the service implemented in the FSM node

This package should contain two additional branches: **action** and **ros2**, which will be mentioned later. Other than that, a VREP scene which interacts with the simulation is also required.

## How to run the node:

The package contains the nodes and the simulation environment for controlling a mobile robot in the Gazebo simulation environment.

```
roslaunch rt2_assignment1 sim.launch
