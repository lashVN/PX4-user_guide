# PX4-Autopilot Main Release Notes

This contains changes to PX4 since the last major release (v1.14).

## Read Before Upgrading

TBD ...

## Major Changes

- TBD

## Upgrade Guide

## Other changes

### Hardware Support

- TBD

### Common

- TBD

### Control

- [offboard][ros2 offboard control](../flight_modes/offboard.md#ros-2-messages) allows for direct motors and servo control. Added in PX4 in [PX4-Autopilot#22222](https://github.com/PX4/PX4-Autopilot/pull/22222).

### Estimation

- TBD

### Sensors

- TBD

### Simulation

- [Gazebo](../sim_gazebo_gz/index.md): Support for [Advanced Plane](../sim_gazebo_gz/vehicles.md#advanced-plane), a simulated fixed-wing vehicle that provides better aerodynamic simulation than the regular plane. Added to PX4 in [PX4-Autopilot#22167](https://github.com/PX4/PX4-Autopilot/pull/22167) and [gz-sim#2185](https://github.com/gazebosim/gz-sim/pull/2185) (advanced lift drag plugin).
- [Gazebo](../sim_gazebo_gz/index.md): The environment variable `PX4_SIM_MODEL` can now be used to indicate the simulation model. This supersedes `PX4_GZ_MODEL`, which is now deprecated. Added to PX4 in [PX4-Autopilot#22400](https://github.com/PX4/PX4-Autopilot/pull/22400).
- [Gazebo](../sim_gazebo_gz/index.md): Separation of Gazebo and PX4 SITL. The two parts of the simulation are now separated. They can be independently launched in any order, and even run on different hosts across a network. Gazebo additional supports drag-and-drop via the resource spawner in Gazebo GUI. Added to PX4 in [PX4-Autopilot#22467](https://github.com/PX4/PX4-Autopilot/pull/22467).

### uXRCE-DDS / ROS2

- [uXRCE-DDS](../middleware/uxrce_dds.md): [DDS Topics YAML](../middleware/uxrce_dds.md#dds-topics-yaml) now allows the use of `subscription_multi` to specify that indicated ROS 2 topics are sent to a separate uORB topic instance reserved for ROS 2. This allows PX4 to differentiate between updates from ROS and those from PX4 uORB publishers. With this change ROS2 users can now decide if the messages that they are sending to PX4 will overlap with the existing uORB ones or be kept in separate instances. Added in PX4 in [PX4-Autopilot#22266](https://github.com/PX4/PX4-Autopilot/pull/22266).

### MAVLink

- TBD

### Multi-Rotor

- [Throw launch](../flight_modes_mc/throw_launch.md)<Badge text="Experimental" type="warning"/>: Start a multicopter by throwing it into the air. Added to PX4 in [PX4-Autopilot#21170](https://github.com/PX4/PX4-Autopilot/pull/21170).
- [Position Slow Mode](../flight_modes_mc/position_slow.md): A slower version of _Position mode_, where the maximum horizontal velocity, vertical velocity and yaw-rate axes can be configured to lower values (using parameters, RC controller knobs/switches, or MAVLink). Added to PX4 in [PX4-Autopilot#22102](https://github.com/PX4/PX4-Autopilot/pull/22102).

### VTOL

- TBD

### Fixed-wing

- [Simplified airspeed sensor configuration](../config_vtol/vtol_without_airspeed_sensor.md): Replacef parameter `CBRK_AIRSPD_CHK` with [SYS_HAS_NUM_ASPD](../advanced_config/parameter_reference.md#SYS_HAS_NUM_ASPD) and renamed parameter `FW_ARSP_MODE` to [FW_USE_AIRSPD](../advanced_config/parameter_reference.md#FW_USE_AIRSPD). To be able to arm without an airspeed sensor set `SYS_HAS_NUM_ASPD` to 0. To not use the airspeed sensor data in the controller, set `FW_USE_AIRSPD` to 0. Added to PX4 in [PX4-Autopilot#22510](https://github.com/PX4/PX4-Autopilot/pull/22510).

### Rover

- [Aion R1](../frames_rover/aion_r1.md)<Badge text="Experimental" type="warning"/>: ESC Driver for Roboclaw motor controller. This comes with build instructions and support for the Aion R1, a new differential drive rover, along with information about integrating the Roboclaw motor controller.

### ROS 2

- [PX4 ROS 2 Interface Library](../ros2/px4_ros2_interface_lib.md)<Badge text="Experimental" type="warning"/>: A new C++ library that simplifies controlling PX4 from ROS 2. Supports adding flight modes in ROS 2 that are peers of the PX4 modes running on the flight controller. Added to PX4 in [PX4-Autopilot#20707](https://github.com/PX4/PX4-Autopilot/pull/20707) (initial support). Goto Setpoint: https://github.com/PX4/PX4-Autopilot/pull/22375
