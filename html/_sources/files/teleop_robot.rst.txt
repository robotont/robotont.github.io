#####################
Controlling the robot
#####################

   .. image:: /files/pictures/coord.png
      :width: 400

#. The robot driver subscribes to a specific type of messages called *velocity commands*. The standard name for this topic is :code:`/cmd_vel`. 

#. The message is of type :code:`geometry_msgs/Twist` and it's structure can be found from `ROS wiki <https://docs.ros.org/api/geometry_msgs/html/msg/Twist.html>`__.

#. To set and control the robot speed, the velocity commands need to be published continuously.


Controlling the robot using teleop twist keyboard
-------------------------------------------------
#. If teleop twist keyboard is not installed

   .. code-block:: bash
      
      sudo apt update
      sudo apt install ros-noetic-teleop-twist-keyboard

#. Open a new terminal window

#. Get the robot and PC into the same ROS environment as shown here: :ref:`same_env`.

#. **On ROBOTONT on-board computer** or on **on PC** run the following command:

   .. code-block:: bash
      
         rosrun teleop_twist_keyboard teleop_twist_keyboard.py

   or

   .. code-block:: bash
      
         roslaunch robotont_demos teleop_keyboard.launch

#. Use the following keys to move the robot:

   .. image:: /files/pictures/twist_keys.png
      :width: 400


   .. warning:: From this point beyond, you are able to drive the robot with a keyboard. Should you loose control over the robot, do one of the following
                 
       * PRESS "k" TO STOP THE ROBOT!
       * PRESS THE EMERGENCY SWITCH ON THE ROBOT.
   
   .. hint:: Notice that the teleop node receives keypresses only when the terminal window is active.
   
   .. tip:: Use :code:`CTRL + C` to stop the node.