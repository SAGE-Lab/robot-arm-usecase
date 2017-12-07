# Robot-arm Usecase
This reopository contains the set of requirements written in an extended version of the Property Specification Patterns (PSPs) described in  [1][2][3] with their translation in Linear Temporal Logic (LTL) for NuSMV[4].

## Usecase 
The requirements specify the intended behaviour of a robotic arm placed on a surface, close to some objects and a bucket placed on the same plane.
The robotic arm, after initialization, searches for one of the objects placed on the surface, moves to the target position and grab the object. After grabbing, it shall move the object in a container placed in a fixed area of the surface and release it, without touching the container.
During normal operation, if the red alarm button is pressed, the robot shall stop as soon as possible. The robot shall stop even in the case of an unintended collision with other objects or with the robot itself (collisions can be detected using joints’ torque).

## Signals
In order to describe the usecase with PSPs, the following boolean and numeric signals are defined:

| Boolean Signals        | Numeric Signals  |
| ---------------------- | ---------------- |
| state_init             | joint1_angle     |
| state_scanning         | joint2_angle     |
| state_moving_to_target | joint3_angle     |
| state_target_reached   | joint4_angle     |
| state_grabbing         | joint1_speed     |
| state_moving_to_bucket | joint2_speed     |
| state_bucket_reached   | joint3_speed     |
| state_releasing        | joint4_speed     | 
| state_alarm            | joint1_acc       |
| arm_idle               | joint2_acc       |
| arm_moving             | joint3_acc       |
| ef_idle                | joint4_acc       |
| alarm_button_pressed   | joint1_torque    | 
| object_detected        | joint2_torque    |
|                        | joint3_torque    |
|                        | joint4_torque    | 
|                        | ef_force         |
|                        | ef_speed         |
|                        | ef_acc           |
|                        | proximity_sensor |


## References
  
   [1] Dwyer, M.B., Avrunin, G.S., Corbett, J.C.: Patterns in property
   specifications for finite-state verification. In: Software
   Engineering, 1999. Proceedings of the 1999 International Conference
   on, pp. 411–420. IEEE (1999)

   [2] http://patterns.projects.cs.ksu.edu/

   [3] Konrad, S., Cheng, B.H.: Real-time specification patterns. In:
   Software engineering, 2005. icse 2005.  proceedings. 27th
   international conference on, pp. 372–381. IEEE (2005)
   
   [4] http://nusmv.fbk.eu/
