.. _demos_on_gazebo:

###############
Demos on Gazebo
###############

Before running the demos it is necessary to get acquinted with the setup section of the documentation.
Make sure you check: :ref:`setup_pc_only`

Launching the Simulation
------------------------

#. To launch the simulator: 

   .. code-block:: bash
      
      roslaunch robotont_gazebo gazebo.launch


The launch file has three arguments:

* model - chooses between a model with NUC and realsense and a model without them

    * default: robotont_gazebo_nuc 

    * options: robotont_gazebo_nuc, robotont_gazebo_basic

* world - chooses which world to use

    * default: empty.world

    * options: empty.world, minimaze.world, bangbang.world, between.world, colors.world

* x_pos - chooses x coordinate of the world, controls where the robot will spawn, default: 0


For example, the following command will spawn the robot to a world called bangbang.world in position x=2 and 
the model that will be used is robotont_gazebo_nuc.

   
   .. code-block:: bash

      roslaunch robotont_gazebo gazebo.launch world:=$(rospack find robotont_gazebo)/worlds/bangbang.world model:=robotont_gazebo_nuc x_pos:=2


Worlds
-------

#. minimaze.world

   .. image:: pictures/maze.png
      :width: 400

   To run

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_minimaze.launch

#. bangbang.world

   .. image:: pictures/bangbang.png
      :width: 400

   To run 

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_bangbang.launch

#. between.world

   .. image:: pictures/between.png
      :width: 400

   To run

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_between.launch

#. colors.world

   .. image:: pictures/colors.png
      :width: 400

   To run

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_colors.launch


2D Mapping and Localization
----------------------------

Installation
~~~~~~~~~~~~
The following packages are needed to run the 2d mapping demo:

   .. code-block:: bash
      
      sudo apt update
      sudo apt install ros-noetic-depthimage-to-laserscan
      sudo apt install ros-noetic-move-base
      
To run the 2D mapping demo, you need to clone the base package:

   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_slam.git


and choose a mapping method from the following:

   1. Cartographer 
   2. Gmapping
   3. Hector SLAM

Gmapping and AMCL
~~~~~~~~~~~~~~~~~~

Installation
************

You can clone the package for the Gmapping method from `this repository. <https://github.com/robotont-demos/demo_slam_gmapping>`__

To clone the packages:

   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_slam_gmapping.git
      git clone https://github.com/robotont-demos/demo_teleop_keyboard.git


Running the demo
****************

#. Launch the simulator

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_minimaze.launch

#. Launch teleop keyboard

   .. code-block:: bash
      
      roslaunch robotont_demos teleop_keyboard.launch 

#. Launch 2d_slam.launch

   .. code-block:: bash
      
      roslaunch demo_slam_gmapping 2d_slam.launch

#. Display the map on RViz

   .. code-block:: bash
      
      roslaunch demo_slam 2d_slam_display.launch

Cartographer
~~~~~~~~~~~~

Installation
************

You can clone the package for the Cartographer method from `this repository. <https://github.com/robotont-demos/demo_slam_cartographer>`__

To clone the packages:

   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_slam_cartographer.git
      git clone https://github.com/robotont-demos/demo_teleop_keyboard.git

Running the demo
****************

#. Launch the simulator

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_minimaze.launch

#. Launch teleop keyboard

   .. code-block:: bash
      
      roslaunch demo_teleop teleop_keyboard.launch 

#. Launch 2d_slam.launch

   .. code-block:: bash
      
      roslaunch demo_slam_cartographer 2d_slam.launch

#. Display the map on RViz

   .. code-block:: bash
      
      roslaunch demo_slam 2d_slam_display.launch

Hector SLAM
~~~~~~~~~~~~

Installation
************

You can clone the package for the Hector SLAM method from `this repository. <https://github.com/robotont-demos/demo_slam_hector>`__

To clone the packages:

   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_slam_hector.git
      git clone https://github.com/robotont-demos/demo_teleop_keyboard.git

Running the demo
****************

#. Launch the simulator

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_minimaze.launch

#. Launch teleop keyboard

   .. code-block:: bash
      
      roslaunch demo_teleop teleop_keyboard.launch 

#. Launch 2d_slam.launch

   .. code-block:: bash
      
      roslaunch demo_slam_hector 2d_slam.launch

#. Display the map on RViz

   .. code-block:: bash
      
      roslaunch demo_slam 2d_slam_display.launch
 

Setting 2D navigation goals
****************************

#. Using ROS Navigation to make the robot move autonomously is pretty straightforward. There are two GUI buttons in RViz to tell the robot where it is located (if it fails to accurately localize at startup) and where it needs to go.

#. For setting initial pose, click on 2D Pose Estimate and drag the arrow where and how the robot actually is.
 
   .. image:: pictures/poseestimatearrow.png
    :width: 400


#.  To tell the robot where to go, click on 2D Nav Goal
    and drag the arrow to where you want the robot to go
    and which way does it have to face.

   .. image:: pictures/2dnavgoalarrow.png
    :width: 400

3D mapping
----------

Creates a 3D map of the robot's surroundings.

Installation
~~~~~~~~~~~~

#. For 3D mapping:

   .. code-block:: bash
      
      sudo apt install ros-noetic-rtabmap-ros

and clone the following packages: 
      
   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_mapping_3d.git
      git clone https://github.com/robotont-demos/demo_teleop_keyboard.git

Running the demo
~~~~~~~~~~~~~~~~

#. Launch the simulator

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_colors.launch

#. Launch mapping_3d.launch

   .. code-block:: bash
      
      roslaunch demo_mapping_3d mapping_3d.launch

#. Launch mapping_3d_display.launch to visualize the result

   .. code-block:: bash
      
      roslaunch demo_mapping_3d mapping_3d_display.launch

#. To move the robot open another terminal window and run teleop twist keyboard

   .. code-block:: bash
      
      rosrun demo_teleop teleop_keyboard.launch 

   .. hint:: Notice that the teleop node only receives keypresses when the terminal window is active.

  .. image:: pictures/3d_mapping_gazebo.png
    :width: 400

The robot identifies and tracks the pose of the provided AR tag and acts accordingly.

Follow the leader
~~~~~~~~~~~~~~~~~

The follow the leader demo showing the capabilities of the Robotont platform to detect and follow the AR Tag.

Installation
************

#. For AR tracking:

   .. code-block:: bash
      
      git clone https://github.com/machinekoder/ar_track_alvar.git -b noetic-devel
      git clone https://github.com/robotont-demos/demo_ar_follow_the_leader.git

Running the demo
****************

On the works

AR steering
-----------

The AR steering demo showing the capabilities of the Robotont platform to detect and follow the AR Tag.

Installation
************

#. For AR tracking:

   .. code-block:: bash
      
      git clone https://github.com/machinekoder/ar_track_alvar.git -b noetic-devel
      git clone https://github.com/robotont-demos/demo_ar_steering.git

Running the demo
****************

#. Launch ar_steering.launch (change tag_nr with your AR tag number)

   .. code-block:: bash
      
      roslaunch demo_ar_steering ar_steering.launch marker_id:=tag_nr

#. Launch the simulator

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_colors.launch

AR maze
-------

The gazebo AR maze demo showing the capabilities of the Robotont platform to detect and follow the AR Tag.

Installation
************

#. For AR tracking:

   .. code-block:: bash
      
      git clone https://github.com/machinekoder/ar_track_alvar.git -b noetic-devel
      git clone https://github.com/robotont-demos/demo_ar_maze.git

Running the demo
****************

#. Launch gazebo_ar_maze.launch

   .. code-block:: bash
      
      roslaunch demo_ar_maze gazebo_ar_maze.launch 

#. Launch the simulator

   .. code-block:: bash
      
      roslaunch robotont_gazebo world_minimaze_ar.launch
