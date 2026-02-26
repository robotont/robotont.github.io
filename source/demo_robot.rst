.. _demos_on_robotont:

##################
Demos on Robotont
##################

Before running the demos it is necessary to get acquainted with the setup section of the documentation.
Make sure you check:

* :ref:`setup_robot_pc`
* :ref:`connecting_remotely`

2D Mapping and Localization
----------------------------

Setup
~~~~~~~~~~~~~

.. hint::

   Before installing any packages from apt, make sure existing packages are up-to-date:

   .. code-block:: bash

      sudo apt update && sudo apt upgrade -y

.. hint::

   ROS packages installed from apt are only available **in terminals where the ROS environment has been sourced**.
   To use these packages, you must first source the general ROS 2 environment:

   .. code-block:: bash

      source /opt/ros/jazzy/setup.bash

#. Install Nav2 from apt:

   .. code-block:: bash

      sudo apt install ros-jazzy-navigation2

#. Navigate to your colcon workspace

   .. code-block:: bash

      cd ~/<your_colcon_workspace>/src

#. Clone the ``depthimage_to_laserscan`` package

   .. code-block:: bash

      git clone https://github.com/ros-perception/depthimage_to_laserscan.git --branch ros2

#. Build the package:

   .. code-block:: bash

      colcon build --packages-select depthimage_to_laserscan

The demo for 2D slam based navigation is available from `this repository <https://github.com/robotont-demos/2d_slam>`__.

#. Navigate to your colcon workspace

   .. code-block:: bash

      cd ~/<your_colcon_workspace>/src

#. Clone the ``2d_slam`` package

   .. code-block:: bash

      git clone https://github.com/robotont-demos/2d_slam.git

#. Build the package:

   .. code-block:: bash

      colcon build --packages-select 2d_slam

Running the demo
~~~~~~~~~~~~~~~~~

The demo can be run on a Robotont featuring either a LIDAR or the standard Realsense D435i camera

.. tabs::

   .. tab:: Robotont with LIDAR

      #. Launch the navigation stack and slam

         .. code-block:: bash

            ros2 launch 2d_slam nav2_lidar_slam.launch.py

      #. (Optional) Visualize costmaps and the robot's model in Rviz2

         .. code-block:: bash

            ros2 launch 2d_slam rviz2_visualize_costmaps.launch.py

   .. tab:: Robotont with Realsense D435i

      #. Launch the navigation stack and slam

         .. code-block:: bash

            ros2 launch 2d_slam nav2_realsense_slam.launch.py

      #. (Optional) Visualize costmaps and the robot's model in Rviz2

         .. code-block:: bash

            ros2 launch 2d_slam rviz2_visualize_costmaps.launch.py

Setting 2D navigation goals
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Using ROS Navigation to make the robot move autonomously is straightforward. In RViz, you have two main GUI buttons: one to set the robot’s current location (if it doesn’t localize itself accurately at startup), and one to set its navigation goal.

#. **To set the initial pose**:

   Click on **“2D Pose Estimate”** in the RViz toolbar, then click and drag the arrow to indicate where the robot is located and which way it is facing.

   .. image:: /pictures/pose_estimate.gif
    :width: 100%


#. **To set a navigation goal**:

   Click on **“2D Goal Pose”** in the RViz toolbar, then click and drag the arrow to the desired destination and orientation for the robot.

   .. image:: /pictures/nav_goal.gif
    :width: 100%

3D mapping
----------
.. dropdown::

   Creates a 3D map of the robot's surroundings.

   .. image:: /pictures/wip.gif
    :width: 200


Follow the leader
-----------------

.. dropdown::

   The follow the leader demo shows the capabilities of the Robotont platform to detect and follow the AR Tag.

   .. image:: /pictures/wip.gif
    :width: 200

AR steering
-----------

.. dropdown::

   The AR steering demo shows the capabilities of the Robotont platform to detect and follow the AR Tag.

   .. image:: /pictures/wip.gif
    :width: 200

AR maze
-------

.. dropdown::

   The AR maze demo shows the capabilities of the Robotont platform to detect and follow the AR Tag.

   .. image:: /pictures/wip.gif
    :width: 200
