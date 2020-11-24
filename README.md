# Simple Velocity Controller
This package contains `controller_node` which takes `input/cmd_vel` from `teleop_twist_keyboard` , filters it according to parameters specified, e.g. decreases speed near obstacles, and publishes filtered twist message to `/cmd_vel` for rto-1 robot and `pioneer/cmd_vel` for p3dx robot.
## Parameters
Specify parameters in `launch/controller.launch` file.
- `max_velocity` : Maximum velocity to be published
- `stop_distance` : Distance to stop near obstacles
- `slowdown_distance` : Starting distance to slow down
- `robot_namespace` : Specify `"p3dx"` for pioneer, `"rto-1"` for rto-1 robot.

## Launching
Simply type `roslaunch velocity_controller controller.launch`

## Comments
I've used simple linear deaccelaration model for robot. It did not work at first implementation, b/c there was a mistake about division. I've tried tanh, but decided linear is way to go. 
Speed linearly decreases as it gets closer to any object in its laser scanner field. Minimum distance in the scan field in considered for deacceleration.
Then it worked pretty well, both for p3dx and rto-1. 