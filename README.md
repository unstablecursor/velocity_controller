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