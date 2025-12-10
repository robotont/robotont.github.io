.. _visualize:
#############
Visualize
#############

Introduction
============

The robotont_description packages provide the complete robot models used across the Robotont software ecosystem. 
THey define the robot’s physical structure, kinematics, visual appearance, and collision properties using a combination 
of URDF (Unified Robot Description Format), Xacro macros, and associated meshes and configuration files.

These packages serve as the foundation for simulation, visualization, and downstream control components. 
Whether you are running Robotont in Gazebo, RViz, or a custom application, robotont_description packages ensure that 
all tools share a consistent and accurate representation of the platform.

Packages description
============
.. tabs::

    .. tab:: robotont_description
        This package provides the canonical robot model used throughout tutorials, simulations, and general development. It includes the core chassis, wheels, default sensor frames, and all geometry required for visualization and simulation. Use this model when targeting the standard Robotont configuration without hardware-specific extensions.

    .. tab:: robotont_nuc_description
        This variant extends the base robot description to reflect the hardware layout of Robotont units that integrate an Intel NUC as the main compute module together with an Intel RealSense D435i depth camera. The package adds the corresponding mechanical structures, sensor mounts, and TF frames, ensuring accurate geometry, mass properties, and sensor placement for simulation and real-robot integration.

    .. tab:: robotont_lite_description
        This package provides the robot model for the Robotont Lite variant. It includes the LiDAR sensor and its associated frames and mounts instead of the depth camera used in the NUC configuration. Use this description whenever you are working with a Robotont Lite robot or simulating the Lite platform with LiDAR-based perception.

Cloning and Building
============

Make sure you have followed the instruction presented in :ref:`prerequisites`.

Navigate to the src folder of your workspace 

.. code-block:: bash

    cd ~/your_ws/src

And clone the required repository:

.. tabs::

    .. tab:: robotont_description

        .. code-block:: bash

            git clone https://github.com/robotont/robotont_description.git

    .. tab:: robotont_nuc_description

        .. code-block:: bash

            git clone https://github.com/robotont/robotont_nuc_description.git

    .. tab:: robotont_lite_description

        .. code-block:: bash

            git clone https://github.com/robotont/robotont_lite_description.git

After cloning, return to the root of your workspace and build:

.. code-block:: bash

    cd ~/your_ws
    colcon build

Once the build completes, source your setup file:

.. code-block:: bash

    source install/setup.bash

Your Robotont description packages are now ready to use in visualization, simulation, or downstream development.

Visualization
============

After building and sourcing your workspace, you can open RViz with the Robotont model preloaded by running:

.. tabs::

    .. tab:: robotont_description

        .. code-block:: bash

            ros2 launch robotont_description display_simulated_robot.launch.py
            
    .. tab:: robotont_nuc_description

        .. code-block:: bash

            ros2 launch robotont_nuc_description display_simulated_robot.launch.py

    .. tab:: robotont_lite_description

        .. code-block:: bash

            ros2 launch robotont_lite_description display_robot_model.launch.py