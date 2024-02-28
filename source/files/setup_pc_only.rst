.. _setup_pc_only:

##############################
Using only the simulated robot
##############################

This setup tutorial will guide you through setting up your PC to run the simulated robot with the demos.


Installing Ubuntu
-----------------

Download and install Ubuntu Linux on your PC from the following link: `Ubuntu 20.04.6 LTS (Focal Fossa) <https://releases.ubuntu.com/focal/>`__.

The guide to install Ubuntu on your PC can be found `here <https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview>`__.

Installing ROS
--------------

Install ROS Noetic by following the guide: `ROS Noetic <http://wiki.ros.org/noetic/Installation/Ubuntu>`__.

Creating a catkin workspace
----------------------------

Create a workspace for catkin as shown `here <http://wiki.ros.org/catkin/Tutorials/create_a_workspace>`__.

Cloning Robotont's packages
-----------------------------

All Robotont's packages can be accessed from `Robotont's GitHub <https://github.com/robotont>`__.

Packages necessary to run the Gazebo simulation with Robotont's demos are following:

#. `robotont_description <https://github.com/robotont/robotont_description>`__

#. `robotont_nuc_description <https://github.com/robotont/robotont_nuc_description>`__

#. `robotont_gazebo <https://github.com/robotont/robotont_gazebo>`__

#. `robotont_navigation <https://github.com/robotont/robotont_gazebo>`__

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

Building the catkin workspace
------------------------------

.. code-block:: bash
      
    cd catkin_ws
    catkin build

Sourcing the workspace
-----------------------

Make the workspace visible to ROS (must be done for every new terminal)

.. code-block:: bash

      source ~/catkin_ws/devel/setup.bash

For automatic sourcing:

.. code-block:: bash

      echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc



