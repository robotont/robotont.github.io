.. _demos_on_gazebo:

###############
Demos on Gazebo
###############

Before running the demos it is necessary to get acquainted with the setup section of the documentation.
Make sure you check: :ref:`setup_pc_only`

Launching the Simulation
------------------------
#. Clone the ``robotont_gazebo`` package into your workspace:

   .. code-block:: bash

      git clone https://github.com/robotont/robotont_gazebo.git

#. Build and source the newly added package:

   .. code-block:: bash

     colcon build --packages-select robotont_gazebo
     source install/setup.bash

#. Launch the simulator using the launch file:

   .. code-block:: bash
      
      ros2 launch robotont_gazebo gazebo.launch.py


Launch file arguments
---------------------

.. list-table::
   :header-rows: 1

   * - Name
     - Description
     - Options
   * - ``generation``
     - Specify the generation of robotont model that is to be loaded
     - 2.1, 3 (default)
   * - ``model``
     - Specify the model that is to be loaded into the world
     - robotont_gazebo_basic, robotont_gazebo_lidar, robotont_gazebo_nuc (default)
   * - ``world``
     - Specify world the robot is spawned in
     - bangbang.sdf, between.sdf, colors.sdf, mapping.sdf, maze.sdf, minimaze.sdf, minimaze_ar.sdf, empty_world.sdf (default)
   * - ``x``, ``y``, ``z``
     - Specify the robot's spawn pose
     - Number, 0 (default)

.. tip::

   For example, loading the generation 3 model in colors.sdf world at pose (-2, 1, 0):

   .. code-block:: bash

      ros2 launch robotont_gazebo gazebo.launch.py world:=colors.sdf x:=-2 y:=1

Worlds
------

.. list-table::
   :header-rows: 1

   * - World
     - Example
     - Launch Command
   * - minimaze.sdf
     - .. image:: /pictures/minimaze_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=minimaze.sdf``
   * - bangbang.sdf
     - .. image:: /pictures/bangbang_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=bangbang.sdf``
   * - between.sdf
     - .. image:: /pictures/between_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=between.sdf``
   * - colors.sdf
     - .. image:: /pictures/colors_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=colors.sdf``
   * - mapping.sdf
     - .. image:: /pictures/mapping_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=mapping.sdf``
   * - maze.sdf
     - .. image:: /pictures/maze_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=maze.sdf``
   * - minimaze_ar.sdf
     - .. image:: /pictures/minimaze_ar_world_example.png
          :width: 200px
     - ``ros2 launch robotont_gazebo gazebo.launch.py world:=minimaze_ar.sdf``


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

      #. Spawn LIDAR Robotont in a gazebo world

         .. code-block:: bash

            ros2 launch robotont_gazebo gazebo.launch.py model:=robotont_gazebo_lidar world:=<world_name>.sdf

      #. Launch the navigation stack and slam

         .. code-block:: bash

            ros2 launch 2d_slam nav2_lidar_slam.launch.py

      #. (Optional) Visualize costmaps and the robot's model in Rviz2

         .. code-block:: bash

            ros2 launch 2d_slam rviz2_visualize_costmaps.launch.py

   .. tab:: Robotont with Realsense D435i

      #. Spawn Robotont in a gazebo world

         .. code-block:: bash

            ros2 launch robotont_gazebo gazebo.launch.py world:=<world_name>.sdf

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
