
Controlling the robot using an Android device app
----------------------------------------------

#. Turn on robotont

#. From your Android device, go to Google Play Store and install the `ROS Control app <https://play.google.com/store/apps/details?id=com.robotca.ControlApp&hl=en>`__.

#. Connect yout Android device to Roboton's network or make sure that your Android device and Robotont’s on-board computer are connected to the same wifi router

#. Open the ROS Control app on your phone. 

#. Insert the ROBOTONT's IP address into Master URI field by entering the following:

   .. code-block:: bash
      
         http://robotont_IP_address:11311

#. Click on "Show advanced options" in the prompted window and fill in "Joystick" and "Odometry" topic names with "cmd_vel" and "odom", respectively

#. Click OK to add the robot

#. Now you can select the robot from the list and teleoperate it using the touch joystick button

