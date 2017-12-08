# Robot-arm Usecase
This reopository contains the set of requirements written in an extended version of the Property Specification Patterns (PSPs) described in  [1][2][3] with their translation in Linear Temporal Logic (LTL) for NuSMV[4].

## Usecase 
The requirements specify the intended behaviour of a robotic arm placed on a surface, close to some objects and a bucket placed on the same plane.
The robotic arm, after initialization, searches for one of the objects placed on the surface, moves to the target position and grab the object. After grabbing, it shall move the object in a container placed in a fixed area of the surface and release it, without touching the container.
During normal operation, if the red alarm button is pressed, the robot shall stop as soon as possible. The robot shall stop even in the case of an unintended collision with other objects or with the robot itself (collisions can be detected using joints’ torque).

The full list of requirements describing the usecase is defined [here](requirements/robot-arm-usecase.req), while the [csv file](requirements.csv) contains the same lists of requirements enumerated and labeled with their pattern type (in the form of \<pattern name\>_\<scope type\>).

## Signals
In order to describe the usecase with PSPs, the following boolean and numeric signals are defined:

| Boolean Signals        |                        | Numerical Signals  |                    |
| ---------------------- | ---------------------- | ------------------ | ------------------ |
| state_init             | arm_moving             | joint1_angle       | joint3_acc         |
| state_scanning         | ef_idle                | joint2_angle       | joint4_acc         |
| state_moving_to_target | alarm_button_pressed   | joint3_angle       | joint1_torque      | 
| state_target_reached   | object_detected        | joint4_angle       | joint2_torque      |
| state_grabbing         |                        | joint1_speed       | joint3_torque      |
| state_moving_to_bucket |                        | joint2_speed       | joint4_torque      | 
| state_bucket_reached   |                        | joint3_speed       | ef_force           |
| state_releasing        |                        | joint4_speed       | ef_speed           |
| state_alarm            |                        | joint1_acc         | ef_acc             |
| arm_idle               |                        | joint2_acc         | proximity_sensor   |

There are 14 boolean signals and 20 numerical ones. 
PSPs don't allow to specify the unit of measurements for numerical signals, so the following units are used by default:
- joint angles are expressed in `deg`
- joint speed is expressed in `deg\s`
- joint accelleration is expressed in `deg\s^2`
- torque is expressed in `N·m`
- end effector (ef) size is expressed in `cm`
- ef force is expressed in `N`
- proximity sensor value is expressed in `cm`




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
