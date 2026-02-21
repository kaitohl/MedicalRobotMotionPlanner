Introduction
=============

Overview
--------

MedicalRobotMotionPlanner is a comprehensive workspace for planning and experimenting with motion planning 
workflows for medical robotics applications. It provides a collection of packages and tools that enable users to design, simulate, and execute motion.

Acknowledgements
---------------

Installation
-------------

Required software for installation includes:

- Ubuntu 22.04
- 3D Slicer 5.6.2
- ROS2 Humble
- SlicerROS2 
- MoveIt 2 Library
- KDL Library

To install SlicerROS2, follow this link: https://slicer-ros2.readthedocs.io/en/v1.0/index.html and follow the instructions for installation.

Please use this forked repository of SlicerROS2: https://github.com/kaitohl/slicer_ros2_module

MyCobot 280 M5 Example
-----------------------

The MyCobot 280 M5 is a 6-DOF robotic arm that can be used for various testing applications. We will use this robot as an example to demonstrate the capabilities of the MedicalRobotMotionPlanner workspace.

Please folow this link: https://github.com/elephantrobotics/mycobot_ros2 to clone the ROS2 package for MyCobot. Ensure you are on the correct branch for ROS2 Humble.

Note: To vizualize the robot in SlicerROS2, you will need to change the URDF file to include the correct path to the mesh files. Currently the mycobot 280 m5 URDF file points the mesh files to .dae files, but SlicerROS2 requires .stl files. The URDF and .dae files for the mycobot 280 m5 is located at ``mycobot_description/urdf/mycobot_280_m5``. You will need to change the URDF file to point to the .stl files located in the same directory. Once you have made the necessary changes to the URDF file, follow the commands below to build and launch necessary ROS2 nodes to visualize the robot in SlicerROS2. We will call our workspace ``ros2_cobot``.

.. code-block:: bash

   mkdir -p ~/ros2_cobot/src
   cd ~/ros2_cobot/src
   git clone https://github.com/elephantrobotics/mycobot_ros2.git -b humble
   cd ~/ros2_cobot
   source /opt/ros/humble/setup.bash
   colcon build
   source install/setup.bash

After succesfully building and sourcing the ROS2 package, you can launch the necessary nodes to visualize the robot in SlicerROS2. Use the following command to launch the nodes:

.. code-block:: bash

   ros2 launch mycobot_ros2_moveit2 demo.launch.py

This will launch the follwing:

- static_virtual_joint_tfs
- robot_state_publisher
- move_group
- moveit_rviz
- warehouse_db (optional)
- ros2_control_node + controller spawners
