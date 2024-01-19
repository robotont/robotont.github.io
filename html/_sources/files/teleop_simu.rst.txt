########################################
Controlling the simulated robot on RViz
########################################

Setup
------

#. Install teleop twist keyboard

   .. code-block:: bash
      
      sudo apt update
      sudo apt install ros-noetic-teleop-twist-keyboard

#. Start the driver

   .. code-block:: bash
      
      roslaunch robotont_driver fake_driver.launch

#. Set the fixed frame to :code:`odom` in RViz

   .. image:: /files/pictures/frame_odom_img.png
       :width: 400

Controlling the robot using teleop twist keyboard
-------------------------------------------------

#. Open a new terminal window

#. Run the following command:

   .. code-block:: bash
      
         rosrun teleop_twist_keyboard teleop_twist_keyboard.py

#. Use the following keys to move the robot:

   .. image:: /files/pictures/twist_keys.png
       :width: 400

   .. hint:: Notice that the teleop node receives keypresses only when the terminal window is active.

   .. tip:: Use :code:`CTRL + C` to stop the node.


Controlling the robot using an Android device
---------------------------------------------

#. Make sure that the user PC and Android device are connected to the same wifi router

#. Open the ROS Control app on your phone

#. Insert your computer's IP address into Master URI field by entering the following:

   .. code-block:: bash
      
         http://IP_address:11311

#. Click on "Show advanced options" in the prompted window and fill in "Joystick" and "Odometry" topic names with "cmd_vel" and "odom", respectively

#. Click OK to add the robot

#. Now you can select the robot from the list and teleoperate it using the touch joystick button