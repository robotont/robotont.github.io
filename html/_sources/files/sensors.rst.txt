#######
Sensors
#######

Robotont uses a Realsense D435i 3D camera, which provides a regular camera feed and a depth sensor. 

The camera feed is launched automatically when the robot is turned on.

Displaying the camera feed
--------------------------

#. Establish an ssh connection between the robot and the PC as shown here: :ref:`setting_up_pc`


#. **On the PC** display the feed on RViz


   .. code-block:: bash
      
      roslaunch rviz rviz 

Click on Add and select Camera. In the Camera topic field, select /camera/color/image_raw. 

   .. image:: /files/pictures/camera_view.png
      :width: 400

Getting distances from objects
------------------------------

Laserscan_to_distance node provides distances from the closest object from the left, the right and the middle.

#. To run laserscan_to_distance node **on Robotont on-board computer**

   .. code-block:: bash
      
      roslaunch robotont_laserscan_to_distance distance_from_depth_image.launch

#. To display the distances either **on PC** or **on Robotont on-board computer**

   .. code-block:: bash
      
      rostopic echo /scan_to_distance

   .. image:: /files/pictures/terminal.png
      :width: 400