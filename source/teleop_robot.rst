#####################
Controlling the real robot
#####################

You can control Robotont using either your keyboard or a web-based interface. This section explains how to send movement commands to the robot and interact using both methods.

   .. image:: /pictures/coord.png
      :width: 60%

#. The robot driver subscribes to a specific type of messages called *velocity commands*. The standard name for this topic is :code:`/cmd_vel`. 

#. The message is of type :code:`geometry_msgs/Twist` — see its structure on the `ROS 2 geometry_msgs/Twist documentation <https://docs.ros.org/en/jazzy/p/geometry_msgs/msg/Twist.html>`__.

#. To set and control the robot speed, the velocity commands need to be published continuously.


Controlling the robot using teleop twist keyboard
-------------------------------------------------
#. If teleop twist keyboard is not installed

   .. code-block:: bash
      
      sudo apt update
      sudo apt install ros2-jazzy-teleop-twist-keyboard

#. Open a new terminal window

#. (Optional) Connect the robot and PC with the same subnet (see :ref:`same_env`).

#. **In Terminal** (on the robot's on-board computer or another PC, if distributed ROS is set up):

   .. tabs::

      .. tab:: Run the node directly

         .. code-block:: bash
      
            ros2 run teleop_twist_keyboard teleop_twist_keyboard.py

      .. tab:: Run necessary nodes with a launch file

         .. code-block:: bash

            ros2 launch demo_teleop teleop_keyboard.launch.py

#. Use the following keys to move the robot:

   .. image:: /pictures/twist_keys.png
      :width: 60%


   .. warning::

       From this point beyond, you are able to drive the robot with a keyboard. Should you lose control over the robot, do one of the following:
                 
       * Press "k" to stop the robot
       * Press the emergency stop button on the robot
   
   .. hint:: Note that teleop only receives keypresses when the terminal window is active (in focus).
   
   .. tip:: Use :code:`CTRL + C` to stop the node.


Controlling the robot using a web interface
-------------------------------------------

#. Make sure that the user's device and the robot are connected to the same subnet and are visible to one another (see :ref:`verifying_communication`).

#. Open the following URL in your web browser (replace `Robot-IP` with the actual IP address of your robot):

   .. code-block:: bash
      
     http://Robot-IP:3000/

You should see the following page:

   .. image:: /pictures/webapp_ok_step.png
       :width: 100%

#. Click OK to close the connection status dialog

#. You can now control the robot using the on-screen joystick and view both the camera feed and depth cloud in your browser.

   .. image:: /pictures/webapp3.png
       :width: 100%
