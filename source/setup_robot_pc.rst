.. _setup_robot_pc:
##############################
Using the robot with a user PC
##############################


This setup tutorial will guide you through setting up your PC to use it with Robotont.

Setting up the PC
======================

Make sure you check: :ref:`prerequisites`.

Cloning Robotont's packages
-----------------------------

All Robotont's packages can be accessed from `Robotont's GitHub <https://github.com/robotont>`__.

Packages necessary to run the demos from PC's Terminal are the following:

#. `robotont_description <https://github.com/robotont/robotont_description>`__

#. `robotont_nuc_description <https://github.com/robotont/robotont_nuc_description>`__

#. `robotont_navigation <https://github.com/robotont/robotont_navigation>`__

You can find the demos from the following repositories:

#. `AR Demo Follow-the-leader <https://github.com/robotont-demos/ar_follow_the_leader.git>`__
#. `AR Steering <https://github.com/robotont-demos/ar_steering.git>`__
#. `Slam 2D <https://github.com/robotont-demos/demo_slam>`__
#. `Mapping 3D <https://github.com/robotont-demos/demo_mapping_3d.git>`__

See the :ref:`demos_on_robot` for more information about the demos.

To clone the packages:

.. code-block:: bash
      
    git clone https://github.com/robotont/package_name.git

Building the colcon workspace
------------------------------

.. code-block:: bash
      
    cd colcon_ws
    colcon build

Sourcing the workspace
-----------------------

Make the workspace visible to ROS 2 (must be done for every new Terminal session)

.. code-block:: bash

      source ~/colcon_ws/install/setup.bash

For automatic sourcing:

.. code-block:: bash

      echo "source ~/colcon_ws/install/setup.bash" >> ~/.bashrc

.. _connecting_remotely:

Network Setup
=============
In order to work with Robotont one of the most convenient ways is to build a network connection between the robot and your PC. 

There are different ways in which you can connect to the robot remotely.

1. AP connection
2. Client connection


AP connection
-------------

Access Point (AP) connection involves connecting directly to the robotont's own network.

This method allows for direct communication with the robot without needing an external network infrastructure and is the easiest way to connect.

The topology of the network can be seen in the following image:

  .. image:: /pictures/apconfig.png
    :width: 100%

You can achieve this by connecting the user PC to Robotont's network.

  .. image:: /pictures/wifi_screen.png
    :align: center
    :width: 60%

Client connection
-----------------

This method involves connecting the robot and the user PC to the same network. The user PC can then connect to the robot using the robot's IP address or hostname.

  .. image:: /pictures/ssh_graph.png
    :width: 100%

This approach can be used to have multiple Robotonts and PCs within the same network. That is particularly helpful when setting up a classroom with multiple Robotonts.

  .. image:: /pictures/naming_router.png
    :width: 100%

.. _same_env:

Distributed ROS 2
-----------------

ROS 2 is designed for distributed systems out of the box. Unlike ROS, it does not use a central ROS Master. Instead, nodes discover each other using `DDS <https://en.wikipedia.org/wiki/Data_Distribution_Service>`__.

There are two options for setting up a distributed system, either using static IPs or defining hostnames on each of the devices.

.. note::
   For consistent networking, assign static IP addresses or use DHCP reservation for both the robot and your PC

.. tabs::

   .. tab:: Use static IPs

      **On Robotont (on-board computer):**

      .. code-block:: bash

         export ROS_DOMAIN_ID=10
         export ROS_IP=192.168.200.1

      **On PC:**

      .. code-block:: bash

         export ROS_DOMAIN_ID=10
         export ROS_IP=192.168.200.101

      .. important::
         Replace the IP addresses with the actual addresses of the devices

      To make these settings persistent, append them to the `.bashrc` file:

      .. code-block:: bash

         echo 'export ROS_DOMAIN_ID=10' >> ~/.bashrc
         echo 'export ROS_IP=192.168.200.101' >> ~/.bashrc
      
      .. note::
         The ``ROS_IP`` variable is helpful if you have multiple network interfaces or encounter issues with node discovery. In many typical setups, ROS 2 nodes will communicate without setting it

   .. tab:: Define hostnames

      On each device:

      1. **Edit the `/etc/hosts` file**:

         .. code-block:: bash

            sudo nano /etc/hosts

      2. **Add entries like this**:

         .. code-block:: text

            192.168.200.1   robotont-1
            192.168.200.101 laptop-1

         .. important::
            Replace the IP addresses with the actual addresses of the devices

      3. **Save and exit**. You can now use hostnames in your ROS 2 setup. Test with:

         .. code-block:: bash

            ping robotont-1

      If the ping succeeds, hostname resolution is working. ROS 2 nodes can communicate with no extra configuration beyond being on the same subnet.

      .. admonition:: Optional

         On both devices, set common DDS domain:

         .. code-block:: bash

            export ROS_DOMAIN_ID=10

         To make this persistent:

         .. code-block:: bash

            echo 'export ROS_DOMAIN_ID=10' >> ~/.bashrc

.. _verifying_communication:

Verifying Communication
------------------------

1. On the Robotont, start a ROS 2 publisher:

   .. code-block:: bash

      ros2 run demo_nodes_cpp talker

2. On the PC, start a ROS 2 subscriber:

   .. code-block:: bash

      ros2 run demo_nodes_cpp listener

If setup correctly, the PC should receive messages from the Robotont.

.. _ssh:

SSH
---
`SSH <https://en.wikipedia.org/wiki/Secure_Shell>`__ provides a safe and reliable way to remotely connect to the robot, allowing you to check its status and execute commands from your PC.

You can connect to the robot using either its IP address or hostname (if defined in the source machine's `/etc/hosts` file).

Follow these steps:

1. Open a new Terminal window on your PC

2. Connect your PC to Robotont’s network

3. Start the SSH connection using either the robot’s hostname or IP address:

.. tabs::

      .. tab:: Using the hostname

         .. code-block:: bash

            ssh <username>@<target_hostname>

         .. hint::
            Replace *<username>* with an user registered on the target machine and *<target_hostname>* with the robot's hostname, e.g

            .. code-block:: bash

               ssh peko@robotont-3

         .. image:: /pictures/ssh_nt.png
           :width: 100%

      .. tab:: Using the IP address

         .. code-block:: bash

            ssh <username>@<target_ip_address>

         .. hint::
            Replace *<username>* with an user registered on the target machine and *<target_ip_address>* with the robot's IP address, e.g

            .. code-block:: bash

               ssh peko@192.168.1.200

4. If prompted with a “yes/no” question about authenticity, type ``yes`` and press **Enter**.

5. **Enter the password** when prompted

6. Verify the login:

   When logged in, the terminal prompt will change to ``peko@robotont-X`` (or similar), indicating you are connected to the robot. This helps you identify which terminal is connected remotely.

   .. image:: /pictures/ssh_nt2.png
     :width: 100%

7. ROS environment setup:

   The robot should automatically source its ROS environment on login. To check which workspaces are being sourced, you can run:

   .. code-block:: bash

      tail ~/.bashrc

.. tip::

   If you have connection issues, double-check the robot’s network settings and ensure you are using the correct hostname or IP address

Troubleshooting Tips
--------------------

- Make sure both devices are on the same network/subnet.
- Check that firewalls allow multicast UDP traffic.
- Use the same ``ROS_DOMAIN_ID`` on all machines.
- If communication issues persist:

  - Try a different DDS implementation (e.g., Cyclone DDS or Fast DDS).
  - Explicitly set the middleware with:

    .. code-block:: bash

       export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp


