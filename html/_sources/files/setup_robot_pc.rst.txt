##############################
Using the robot with a user PC
##############################


This setup tutorial will guide you through setting up your PC to use it with Robotont.

.. _setting_up_pc:

Setting up the PC
======================

Installing Ubuntu
-----------------

Download and install Ubuntu Linux on your PC from the following link: `Ubuntu 20.04.6 LTS (Focal Fossa) <https://releases.ubuntu.com/focal/>`__.

The guide to install Ubuntu on your PC can be found `here <https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview>`__.

Installing ROS
--------------

Install ROS Noetic by following the guide: `ROS Noetic <http://wiki.ros.org/noetic/Installation/Ubuntu>`__.


Creating a catkin workspace
----------------------------

Create a workspace for catkin as shown `here <http://wiki.ros.org/catkin/Tutorials/create_a_workspace>`__.

Cloning Robotont's packages
-----------------------------

All Robotont's packages can be accessed from `Robotont's GitHub <https://github.com/robotont>`__.

Packages necessary to run the demos from PC's terminal are following:

#. `robotont_description <https://github.com/robotont/robotont_description>`__

#. `robotont_nuc_description <https://github.com/robotont/robotont_nuc_description>`__

#. `robotont_navigation <https://github.com/robotont/robotont_gazebo>`__

You can find the demos from the following repositories:

#. `AR Demo Follow-the-leader <https://github.com/robotont-demos/ar_follow_the_leader.git>`__
#. `AR Steering <https://github.com/robotont-demos/ar_steering.git>`__
#. `Slam 2D <https://github.com/robotont-demos/demo_slam>`__
#. `Mapping 3D <https://github.com/robotont-demos/demo_mapping_3d.git>`__

See the :ref:`demos_on_robot` for more information about the demos.

To clone the packages:

.. code-block:: bash
      
    git clone https://github.com/robotont/package_name.git

Building the catkin workspace
------------------------------

.. code-block:: bash
      
    cd catkin_ws
    catkin build

Sourcing the workspace
-----------------------

Make the workspace visible to ROS (must be done for every new terminal)

.. code-block:: bash

      source ~/catkin_ws/devel/setup.bash

For automatic sourcing:

.. code-block:: bash

      echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc

.. _connecting_remotely:

Network Setup
=============

There are different ways in which you can connect to the robot remotely.

#. AP connection

Access Point (AP) connection involves connecting directly to the robotont's own network.

This method allows for direct communication with the robot without needing an external network infrastructure and is the easiest way to connect to the robot.


#. Client connection

This method involves connecting the robot and the user PC to the same network. The user PC can then connect to the robot using the robot's IP address or hostname.

Hostname vs. IP-address based setup
------------------------------------

In order to run ROS nodes on the robot from a PC, the PC needs to be in the same ROS environment as the robot.
There are two ways to achieve this:

#. Hostname based setup
#. IP-address based setup

In the following examples, we assume the Robotont and the PC having the following configuration:

.. csv-table::
  :header: "Machine", "Hostname", "IP-address","Netmask"
  :widths: 40, 40, 40,40 

  "Robotont", "robotont-1", "192.168.200.1", "255.255.255.0"
  "PC", "laptop-1", "192.168.1.101","255.255.255.0"

Hostname based setup
*********************

In this configuration, the robot and PC query each other via hostnames. It means that both hosts need to have each other's names associated with IP addresses. These hostname <--> IP pairs are defined in the `/etc/hosts` file. Use your favorite text editor and make sure the following entries exist.

**/etc/hosts on Robotont on-board computer:**

.. code-block:: bash

  127.0.1.1 robotont-1
  192.168.200.101 laptop-1


**/etc/hosts on PC:**

.. code-block:: bash

  127.0.1.1 laptop-1
  192.168.200.1 robotont-1


IP-address based setup
**********************

If you want to configure IP based communication there is no need to edit the hosts file. Instead, a `ROS_IP` environmental variable has to be set on both sides:

SSH 
---

SSH is a secure way to connect to the robot and run commands on it. It is a good way to check the status of the robot and to run commands on it.

It can be done using the IP address of the robot or the hostname.

SSH IP
^^^^^^

SSH Hostname
^^^^^^^^^^^^^^

1. Open a new terminal window

2. Connect the user PC to Robotont's network.

  .. image:: /files/pictures/wifi_screen.png
    :width: 400

3. Establish an ssh connection (change the X with the ID written on the robot)

   .. code-block:: bash
      
      ssh peko@robotont-X

  or 

  .. code-block:: bash
      
      ssh peko@ip_of_the_robot

  .. image:: /files/pictures/ssh_nt.png
    :width: 400

4. If a yes/no question is asked, enter yes

5. Enter the password


6. When logged in successfully, you can see that the terminal prompt has changed to peko@robotont-X. This will be an important reference when trying to figure out which terminal is connected to where.

  .. image:: /files/pictures/ssh_nt2.png
    :width: 400

7. After logging into the robot, the ROS environment should be automatically sourced for you. You can quickly display the last lines of the file with tail ~/.bashrc command to examine which workspaces are sourced.

.. _same_env:
Distributed ROS
----------------

The ROS environment can be distributed across multiple machines. This means that the ROS Master can be running on one machine, while the nodes are running on another. This is useful when the robot has limited computational resources and the user wants to run the nodes on a more powerful machine.

ROS_IP
^^^^^^
If you want to configure IP based communication there is no need to edit the hosts file. Instead, a `ROS_IP` environmental variable has to be set on both sides:

**on Robotont on-board computer:**

.. code-block:: bash

  export ROS_IP=192.168.200.101


**on PC:**

.. code-block:: bash

  export ROS_MASTER_URI=http://192.168.200.1:11311
  export ROS_IP=192.168.200.101


Similarly to the hostname based setup, append the commands to `.bashrc` to set the variables automatically.


You can use your own router to connect the robot and the PC to get them on the same network.

You can set up the environment by following the naming conventions for the IP-address assignment to every device that connects to the router.

  .. image:: /files/pictures/naming_router.png
    :width: 400


ROS_MASTER_URI
^^^^^^^^^^^^^^
We need to tell the PC to look for a ROS Master on Robotont. We do that by modifying a special environment variable named `ROS_MASTER_URI`, which by default points to localhost.

**on PC**, open a terminal and enter:

.. code-block:: bash

  export ROS_MASTER_URI=http://robotont-1:11311

Now all ROS nodes you run in this terminal will connect to the Master on the Robotont. Test it with e.g. `rosnode list`.
Note that the environment variable has to be set for each terminal window! To make it automatic, you can add the line to the end of the `.bashrc` file in the home directory of the PC:

.. code-block:: bash

  echo 'export ROS_MASTER_URI=http://robotont-1:11311' >> ~/.bashrc
