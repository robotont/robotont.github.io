.. _controlling_real_robot:
###########################
Teleoperating the real robot with user PC
###########################

You can control Robotont using your keyboard. This section explains how to send movement commands to the robot and interact using both methods.

   .. image:: /pictures/coord.png
      :width: 100%

* The robot driver subscribes to a specific type of messages called *velocity commands*. The standard name for this topic is :code:`/cmd_vel`.

* The message is of type :code:`geometry_msgs/Twist` — see its structure on the `ROS 2 geometry_msgs/Twist documentation <https://docs.ros.org/en/jazzy/p/geometry_msgs/msg/Twist.html>`__.

* To set and control the robot speed, the velocity commands need to be published continuously.


Setup
-------------------------------------------------

.. hint::

   Before installing any packages from apt, make sure existing packages are up-to-date:

   .. code-block:: bash

      sudo apt update && sudo apt upgrade -y

.. hint::

   ROS packages installed from apt are only available **in terminals where the ROS environment has been sourced**.
   To use these packages, you must first source the general ROS 2 environment:

   .. code-block:: bash

      source /opt/ros/jazzy/setup.bash

#. Install teleop twist keyboard from apt:

   .. code-block:: bash

      sudo apt install ros-jazzy-teleop-twist-keyboard

#. (Optional) Connect the robot and PC with the same subnet (see :ref:`same_env`).

Controlling the robot
-------------------------------------------------

#. **In Terminal** (on the robot's on-board computer or another PC, if distributed ROS is set up):

   .. code-block:: bash

      ros2 run teleop_twist_keyboard teleop_twist_keyboard

#. Use the following keys to move the robot:

   .. image:: /pictures/teleop_twist_terminal.png
      :width: 100%

   .. warning::

       From this point beyond, you are able to drive the robot with a keyboard. Should you lose control over the robot, do one of the following:
                 
       * Press "k" to stop the robot
       * Press the emergency stop button on the robot
   
   .. hint:: Note that teleop only receives keypresses when the terminal window is active (in focus).
   
   .. tip:: Use :code:`CTRL + C` to stop the node.

