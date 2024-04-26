.. _demos_on_robot:

#################
Demos on Robotont
#################

Before running the demos it is necessary to get acquinted with the setup section of the documentation.

Before running the demos on the robot read the following instructions: 

* :ref:`setting_up_pc`
* :ref:`connecting_remotely`

Note that some of the commands will run on Robotont on-board computer and some on user PC.

2D Mapping and Localization
----------------------------

The following are needed to run the 2D mapping demo:

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
      git clone https://github.com/robotont-demos/demo_teleop.git


Running the demo
****************

#. **On Robotont on-board computer or on PC** launch 2d_slam.launch

   .. code-block:: bash
      
      roslaunch demo_slam_gmapping 2d_slam.launch

#. **On PC** launch 2d_slam_display.launch to visualize the result

   .. code-block:: bash
      
      roslaunch demo_slam 2d_slam_display.launch

#. To move the robot open another terminal window **on robotont on-board computer or on the PC** and run teleop twist keyboard (TBA)

   .. code-block:: bash
      
      roslaunch demo_teleop teleop_keyboard.launch 

   .. hint:: Notice that the teleop node only receives keypresses when the terminal window is active.

Cartographer
~~~~~~~~~~~~

Installation
************

You can clone the package for the Cartographer method from `this repository. <https://github.com/robotont-demos/demo_slam_cartographer>`__

To clone the packages:

   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_slam_cartographer.git
      git clone https://github.com/robotont-demos/demo_teleop.git

Running the demo
****************

#. **On Robotont on-board computer or on PC** launch 2d_slam.launch

   .. code-block:: bash
      
      roslaunch demo_slam_cartographer 2d_slam.launch

#. **On PC** launch 2d_slam_display.launch to visualize the result
   
      .. code-block:: bash
         
         roslaunch demo_slam 2d_slam_display.launch

#. To move the robot open another terminal window **on robotont on-board computer or on the PC** and run teleop twist keyboard (TBA)

   .. code-block:: bash
      
      roslaunch demo_teleop teleop_keyboard.launch 

   .. hint:: Notice that the teleop node only receives keypresses when the terminal window is active.

Hector SLAM
~~~~~~~~~~~~

Installation
************

You can clone the package for the Hector SLAM method from `this repository. <https://github.com/robotont-demos/demo_slam_hector>`__

To clone the packages:

   .. code-block:: bash
      
      git clone https://github.com/robotont-demos/demo_slam_hector.git
      git clone https://github.com/robotont-demos/demo_teleop.git

Running the demo
****************

#. **On Robotont on-board computer or on PC** launch 2d_slam.launch

   .. code-block:: bash
      
      roslaunch demo_slam_hector 2d_slam.launch

#. **On PC** launch 2d_slam_display.launch to visualize the result

   .. code-block:: bash
      
      roslaunch demo_slam 2d_slam_display.launch

#. To move the robot open another terminal window **on robotont on-board computer or on the PC** and run teleop twist keyboard.

   .. code-block:: bash
      
      roslaunch demo_teleop teleop_keyboard.launch 

   .. hint:: Notice that the teleop node only receives keypresses when the terminal window is active.

Setting 2D navigation goals
~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
      git clone https://github.com/robotont-demos/demo_teleop.git

Running the demo
~~~~~~~~~~~~~~~~

#. **On Robotont on-board computer or on PC** launch mapping_3d.launch

   .. code-block:: bash
      
      roslaunch demo_mapping_3d mapping_3d.launch

#. **On PC** launch mapping_3d_display.launch to visualize the result

   .. code-block:: bash
      
      roslaunch demo_mapping_3d mapping_3d_display.launch

#. To move the robot open another terminal window **on robotont on-board computer or on user PC** and run teleop twist keyboard
 
   .. code-block:: bash
      
      rosrun demo_teleop teleop_keyboard.launch 

   .. hint:: Notice that the teleop node only receives keypresses when the terminal window is active.

  .. image:: pictures/3dmap.png
    :width: 400

AR tracking
-----------

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

#. **On Robotont on-board computer or on PC** launch ar_follow_the_leader.launch (change tag_nr with your AR tag number)

   .. code-block:: bash
      
      roslaunch demo_ar_follow_the_leader ar_follow_the_leader.launch marker_id:=tag_nr

#. **On PC** launch ar_marker_display.launch to visualize the result

   .. code-block:: bash
      
      roslaunch demo_ar_follow_the_leader ar_marker_display.launch

AR steering
~~~~~~~~~~~

The AR steering demo showing the capabilities of the Robotont platform to detect and follow the AR Tag.

Installation
************

#. For AR tracking:

   .. code-block:: bash
      
      git clone https://github.com/machinekoder/ar_track_alvar.git -b noetic-devel
      git clone https://github.com/robotont-demos/demo_ar_steering.git

Running the demo
****************

#. **On Robotont on-board computer or on PC** launch ar_steering.launch (change tag_nr with your AR tag number)

   .. code-block:: bash
      
      roslaunch demo_ar_steering ar_steering.launch marker_id:=tag_nr

#. **On PC** launch ar_marker_display.launch to visualize the result
   
      .. code-block:: bash
         
         roslaunch demo_ar_steering ar_marker_display.launch


AR Maze 
~~~~~~~

The AR maze demo showing the capabilities of the Robotont platform to detect and follow the AR Tag and navigate through the maze.

Installation
************

#. For AR tracking:

   .. code-block:: bash
      
      git clone https://github.com/machinekoder/ar_track_alvar.git -b noetic-devel
      git clone https://github.com/robotont-demos/demo_ar_maze.git

Running the demo
****************

#. **On Robotont on-board computer or on PC** launch ar_maze.launch

   .. code-block:: bash
      
      roslaunch demo_ar_maze ar_maze.launch

   .. hint:: Make sure to modify the list with ar tags for maze navigation in 8th line of ar_maze.launch:  
         roslaunch demo_ar_maze ar_maze.launch marker_ids:="4,10,5"
