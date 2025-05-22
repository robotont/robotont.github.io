#######
Sensors
#######

The Robotont platform includes an Intel RealSense D435i 3D camera, capable of streaming both regular color images and depth data. These camera feeds are available automatically as soon as the robot is turned on.

Setup
-----

#. Clone the `depthimage_to_laserscan <https://github.com/ros-perception/depthimage_to_laserscan/>`__ package into your workspace and build:

   .. code-block:: bash

      cd ~/colcon_ws/src
      git clone https://github.com/ros-perception/depthimage_to_laserscan
      git checkout -b ros2 && git fetch
      colcon build

#. Setup distributed ROS 2 as shown here: :ref:`same_env`
#. Establish an SSH connection between the robot and the PC as shown here: :ref:`ssh`



Displaying the camera feed
--------------------------

#. **In Terminal**, on the PC, start Rviz2:


   .. code-block:: bash
      
      rviz2

#. Click on **Add** and select **Camera**. In the Camera **Image Topic** field, select */camera/color/image_raw*.

   .. image:: /pictures/camera_view.png
      :width: 60%

Getting distances from objects
------------------------------

The `depthimage_to_laserscan` node converts the RealSense camera's depth image into a 2D LaserScan message, which you can use to estimate distances to objects directly in front of the robot.

#. **Launch the depthimage_to_laserscan node** on the Robotont or your PC:

   .. code-block:: bash

      ros2 run depthimage_to_laserscan depthimage_to_laserscan_node

   .. hint::
      Make sure the parameters for the depth image topic and camera info match your camera's output, e.g.:

      .. code-block:: bash

         ros2 run depthimage_to_laserscan depthimage_to_laserscan_node \
            --ros-args \
            --remap depth:=/camera/depth/image_raw \
            --remap depth_camera_info:=/camera/color/camera_info

#. **Visualize and analyze the LaserScan data**:

   .. admonition:: Option 1: Rviz2

      * Click on **Add** and select **LaserScan**. In the LaserScan **Topic** field, select */scan*

      .. list-table::
         :widths: 50 50
         :header-rows: 0

         * - Gazebo simulation

             .. image:: /pictures/laserscan_gazebo.png
               :width: 100%
           - Rviz2 LaserScan visualization

             .. image:: /pictures/laserscan_rviz.png
               :width: 100%

   .. admonition:: Option 2: View raw data

      * **In Terminal**:

         .. code-block:: bash

            ros2 topic echo /scan

      * The messages are of type :code:`sensor_msgs/LaserScan` — see its structure on the `ROS 2 sensor_msgs/LaserScan documentation <https://docs.ros.org/en/jazzy/p/sensor_msgs/msg/LaserScan.html>`__
         .. image:: /pictures/laserscan_terminal.png
            :width: 60%