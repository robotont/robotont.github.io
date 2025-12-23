.. _gazebo_simulator:

##############################
Gazebo Simulator
##############################

This setup tutorial will guide you through setting up your PC to run the simulated robot on gazebo and some basics commands.


Dependencies
=======================

Make sure you check: :ref:`prerequisites` and you have cloned and tested robotont_description and robotont_nuc_description packages, you can find complete instructions on :ref:`visualize`.

All Robotont's packages can be accessed from `Robotont's GitHub <https://github.com/robotont>`__.

Packages necessary to run the Gazebo simulation with Robotont's demos are following:

#. `robotont_description <https://github.com/robotont/robotont_description>`__  

#. `robotont_nuc_description <https://github.com/robotont/robotont_nuc_description>`__  

#. `robotont_gazebo <https://github.com/robotont/robotont_gazebo>`__ 

#. `gz_planar_move <https://github.com/sygism/gz_planar_move>`__ 


Install Gazebo Harmonic and the ROS ↔ Gazebo integration packages (required for simulation time `/clock`, physics stepping, and Gazebo transport bridges), plus common Robotont description tools:

.. code-block:: bash

    sudo apt update
    sudo apt install -y \
        gz-harmonic \
        ros-jazzy-ros-gz \
        ros-jazzy-ros-gz-sim \
        ros-jazzy-ros-gz-bridge \
        ros-jazzy-xacro \
        ros-jazzy-robot-state-publisher

After cloning the Robotont and `gz_planar_move` repositories into your workspace `src/`, install remaining dependencies with rosdep:

.. code-block:: bash

    cd ~colcon_ws
    rosdep update
    rosdep install --from-paths src --ignore-src -r -y


Building and sourcing the colcon workspace
=======================
.. code-block:: bash
      
    cd colcon_ws
    colcon build


Make the workspace visible to ROS 2 (must be done for every new terminal)

.. code-block:: bash

      source ~/colcon_ws/install/setup.bash

For automatic sourcing:

.. code-block:: bash

      echo "source ~/colcon_ws/install/setup.bash" >> ~/.bashrc


Running the Simulation
=======================

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


After building and sourcing your workspace, you can spawn the robot in a gazebo world, for example:

.. code-block:: bash

   ros2 launch robotont_gazebo gazebo.launch.py world:=colors.sdf

.. image:: /pictures/colors_world_example.png
  :width: 100%

Open a second terminal and use ``teleop_twist_keyboard`` to control the robot:

.. code-block:: bash

   ros2 run teleop_twist_keyboard teleop_twist_keyboard

If everything worked correctly, you should see the following in your terminal:

   .. image:: /pictures/teleop_screenshot.png
    :width: 100%

By pressing different keys in this terminal, you’ll see the robot move
Refer to individual demo package READMEs for more details on launching specific demos.
See the :ref:`demos_on_gazebo` for more information about the demos.