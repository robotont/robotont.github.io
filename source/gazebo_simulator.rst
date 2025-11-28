.. _gazebo_simulator:

##############################
Gazebo simulator
##############################

This setup tutorial will guide you through setting up your PC to run the simulated robot with the demos.


Make sure you check: :ref:`prerequisites`.

Cloning Robotont's packages
-----------------------------

All Robotont's packages can be accessed from `Robotont's GitHub <https://github.com/robotont>`__.

Packages necessary to run the Gazebo simulation with Robotont's demos are following:

#. `robotont_description <https://github.com/robotont/robotont_description>`__

#. `robotont_nuc_description <https://github.com/robotont/robotont_nuc_description>`__

#. `robotont_gazebo <https://github.com/robotont/robotont_gazebo>`__

#. `robotont_navigation <https://github.com/robotont/robotont_navigation>`__

#. `robotont_msgs <https://github.com/robotont/robotont_msgs.git>`__

You can find the demos from the following repositories:

#. `AR Demo Follow-the-leader <https://github.com/robotont-demos/ar_follow_the_leader.git>`__
#. `AR Steering <https://github.com/robotont-demos/ar_steering.git>`__
#. `Slam 2D <https://github.com/robotont-demos/demo_slam>`__
#. `Mapping 3D <https://github.com/robotont-demos/demo_mapping_3d.git>`__

See the :ref:`demos_on_gazebo` for more information about the demos.

To clone the packages, for example, robotont_description:

.. code-block:: bash
      
    git clone https://github.com/robotont/robotont_description.git

Building the colcon workspace
------------------------------

.. code-block:: bash
      
    cd colcon_ws
    colcon build

Sourcing the workspace
-----------------------

Make the workspace visible to ROS 2 (must be done for every new terminal)

.. code-block:: bash

      source ~/colcon_ws/install/setup.bash

For automatic sourcing:

.. code-block:: bash

      echo "source ~/colcon_ws/install/setup.bash" >> ~/.bashrc


Running the Simulation
---------------------

After building and sourcing your workspace, you can spawn the robot in a gazebo world, for example:

.. code-block:: bash

   ros2 launch robotont_gazebo gazebo.launch.py world:=colors.sdf

.. image:: /pictures/colors_world_example.png
  :width: 100%

Refer to individual demo package READMEs for more details on launching specific demos.
