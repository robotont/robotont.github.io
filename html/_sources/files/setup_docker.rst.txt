.. _setup_docker:

#############################################
Simulated robot on docker with X11 forwarding
#############################################

This setup tutorial will guide you through setting up your PC to run the simulated robot with the demos.
This assumes that you have a linux machine. Tested on ubuntu 20, but should work on any linux.

Installing Docker
-----------------

Quick version:

.. code-block:: bash

    sudo apt install curl
    echo "Installing docker"
    curl -fsSL https://get.docker.com | sudo sh

    groupadd docker
    usermod -aG docker $(whoami)

Restart user session.

Slow version is to follow the instructions `here <https://docs.docker.com/engine/install/ubuntu/>`__.

Cloning Robotont's packages
-----------------------------

All Robotont's packages can be accessed from `Robotont's GitHub <https://github.com/robotont>`__.

Packages necessary to run the Gazebo simulation with Robotont's demos are following:

#. `robotont_description <https://github.com/robotont/robotont_description>`__

#. `robotont_nuc_description <https://github.com/robotont/robotont_nuc_description>`__

#. `robotont_gazebo <https://github.com/robotont/robotont_gazebo>`__

#. `robotont_navigation <https://github.com/robotont/robotont_gazebo>`__

#. `robotont_demos <https://github.com/robotont/robotont_demos>`__

#. `robotont_msgs <https://github.com/robotont/robotont_msgs.git>`__

.. code-block:: bash

    mkdir -p robotont/src
    cd robotont/src

    git clone https://github.com/robotont/robotont_description.git
    git clone https://github.com/robotont/robotont_demos.git
    git clone https://github.com/robotont/robotont_gazebo.git
    git clone https://github.com/robotont/robotont_msgs.git
    git clone https://github.com/robotont/robotont_navigation.git
    git clone https://github.com/robotont/robotont_nuc_description.git

    cd ..
    echo "Path to robotont workspace: $(pwd)""


Instructions when using an nvidia GPU
-------------------------------------
Install nvidia-docker 2 `here <https://github.com/nvidia/nvidia-docker/wiki/Frequently-Asked-Questions#setting-up>`__.

Use docker-ros-box to setup ros

.. code-block:: bash

    git clone https://github.com/KingBoomie/docker-ros-box.git
    cd docker-ros-box
    ./init-ros-box.sh melodic <PATH_TO_ROBOTONT_WORKSPACE>

Instructions for everyone else
------------------------------
Use docker-ros-box to setup ros

.. code-block:: bash

    git clone https://github.com/pierrekilly/docker-ros-box
    cd docker-ros-box
    ./init-ros-box.sh melodic <PATH_TO_ROBOTONT_WORKSPACE>


Logging into your ros image
---------------------------
In the robotont folder

.. code-block:: bash

    ./go.sh
    cd /home/melodic-dev/catkin_ws


Installing missing dependancies
-------------------------------

.. code-block:: bash

    sudo apt install -y ros-melodic-depthimage-to-laserscan \
        ros-melodic-cartographer-ros \
        ros-melodic-move-base \
        ros-melodic-rtabmap-ros \
        ros-melodic-ar-track-alvar \
        ros-melodic-realsense2-description \
        ros-melodic-realsense2-camera \
        ros-melodic-joy \
        ros-melodic-teleop-twist-keyboard


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

Running the demos with Gazebo
-----------------------------

Tutorial for running the simulation with the demos can be found here: :ref:`demos_on_gazebo`.


    


