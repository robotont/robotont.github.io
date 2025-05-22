########################################
Controlling the simulated robot in RViz
########################################

Setup
------

#. Install teleop twist keyboard

   .. code-block:: bash
      
      sudo apt update
      sudo apt install ros2-jazzy-teleop-twist-keyboard

#. Start the driver

   .. code-block:: bash
      
      ros2 launch robotont_driver fake_driver.launch.py

#. Set the fixed frame to :code:`odom` in RViz

   .. image:: /pictures/frame_odom_img.png
       :width: 60%

Controlling the robot using teleop twist keyboard
-------------------------------------------------

#. Open a new Terminal window

#. Run the following command:

   .. code-block:: bash
      
         ros2 run teleop_twist_keyboard teleop_twist_keyboard.py

#. Use the following keys to move the robot:

   .. image:: /pictures/twist_keys.png
       :width: 60%

   .. hint:: Note that teleop only receives keypresses when the terminal window is active (in focus).

   .. tip:: Use :code:`CTRL + C` to stop the node.