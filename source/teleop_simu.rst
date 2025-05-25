########################################
Controlling the simulated robot in RViz2
########################################

Setup
------

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

#. Navigate to your colcon workspace:

   .. code-block:: bash

      cd ~/<your_colcon_workspace>/src

#. Clone the ``robotont_driver`` package:

   .. code-block:: bash

      git clone https://github.com/robotont/robotont_driver.git

#. Build the package:

   .. code-block:: bash

      colcon build --packages-select robotont_driver

#. Start the driver:

   .. code-block:: bash
      
      ros2 launch robotont_driver fake_driver_launch.py

Controlling the robot using teleop twist keyboard
-------------------------------------------------

#. Start the ``teleop_twist_keyboard`` node:

   .. code-block:: bash
      
         ros2 run teleop_twist_keyboard teleop_twist_keyboard

#. Use the following keys to move the robot:

   .. image:: /pictures/teleop_twist_terminal.png
       :width: 100%

   .. hint:: Note that teleop only receives keypresses when the terminal window is active (in focus).

   .. tip:: Use :code:`CTRL + C` to stop the node.