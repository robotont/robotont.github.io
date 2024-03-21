
#############
Overview
#############

ROBOTONT is an mobile ground robot with omnidirectional wheels to enable rapid movement in any direction at a desired heading. 
The sensor system includes a depth camera which allows it to see like humans and map the entire environment in 3D. 
The powerful on-board computer facilitates running high performance algorithms and libraries. 
The software stack is open-source and based on ROS (Robot Operating System). 
Its literally transparent design, modular hardware, and open-source software offer endeless custiomization and extendibility options.

ROBOTONT currently includes the following out-of-the-box demos:

    
   * Android device, gamepad and keyboard based teleoperation,
   * 2D mapping and SLAM,
   * 3D mapping,
   * AR marker tracking, and
   * gesture-based human-robot interaction.

   .. image:: /files/pictures/robotont_gen_2_3_multi_view.png
      :width: 800

Specification
-------------

`On-board computer - Intel NUC7i5BNK <https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc7i5bnk.html>`__

.. csv-table::
   :widths: 20, 20

   "Processor", "Intel Core i5 (7th Gen) 7260U (2 cores, up to 3.4 GHz)"
   "RAM", "DDR4 2133 MHz 4 GB"
   "GPU", "Intel Iris Plus Graphics 640"
   "Peripherals", "1x HDMI, 4 x USB 3.0 Type A, 1 x Thunderbolt 3/DisplayPort/USB-C 3.1 Gen2"
   "Storage", "Transcend MTS420 M2.0 SSD 120 GB"
   "Network", "Intel I219-V Gigabit Ethernet – RJ45 <br> Intel Dual Band Wireless-AC 8265, IEEE 802.11a/b/g/n/ac"

`Development board for external devices and motors- ARM NUCLEO-L476RG <https://os.mbed.com/platforms/ST-Nucleo-L476RG/>`__

.. csv-table::
   :widths: 20, 20

   "CPU", "ARM®32-bit Cortex®-M4, 80 MHz"
   "Debugging and programming interface","ST-LINK/V2-1"
   "Connectivity", "mini-USB"
   "GPIO", "51"

`Motors – DC motors with encoders <https://www.pololu.com/product/1442/specs/>`__

.. csv-table::
   :widths: 20, 20

   "Voltage", "12 V"
   "Stall current", "5000 mA"
   "Max rpm", "500"
   "Max torque", "0.59 Nm"
   "Gear Ratio", "19:1"
   "Encoder resolution (motor)", "64 counts per revolution"
   "Encoder resolution (gearbox)", "1200 counts per revolution"

`3D depth camera – Intel Realsense D435 <https://www.intelrealsense.com/depth-camera-d435/>`__

.. csv-table::
   :widths: 20, 20

   "Depth Stream Output Resolution", "1280 x 720"
   "Depth Field of View horizontal", "85.2 deg"
   "Depth Field of Vies vertical", "58 deg"
   "RGB Sensor Resolution and Frame Rate", "1920 x 1080 at 30 fps"
   "Minimum depth", "110 mm"
   "Max range", "Approx.10 meters; Varies depending on calibration, scene, and lighting condition"
   "Connection type", "USB 3 Type-C"




























