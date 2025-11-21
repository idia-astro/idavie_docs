.. _installation_configuration:

Installation and configuration
==============================
.. note:: The software is in active development, and while we do our best to ensure that there are no issues present, there might be some. We welcome bug reports and feature requests on the GitHub `repository <https://github.com/idia-astro/iDaVIE/>`_. 

Executable
-----------
Once the requirements described in :ref:`requirements`, are installed and working correctly, the user can download and unzip the provided :literal:`iDaVIE.1.0.zip`, which contains the executable .exe (and other reference files). The zip file is available on Github at this `link <https://github.com/idia-astro/iDaVIE/releases/latest>`_.

.. raw:: html

    <img src="_static/idavie-pkg-edit.png"
         style="width:100%;height:auto;">

To start the software, double-click on the executable iDaVIE file.
 

Source code
-----------
Please see :ref:`build` for instructions on building iDaVIE from the source code. We also provide detailed :ref:`contribution` guidelines.

Configuration File
------------------
The first time iDaVIE is launched, a file named :literal:`config.json` will be generated in the main directory where the executable is located. This file contains the default configuration settings for the software. The user can modify this file to customize the software to their needs. The configuration file has the following settings that can be modified:

Config Options
~~~~~~~~~~~~~~

.. list-table::
   :widths: 15 85
   :header-rows: 1

   * - **Configuration Setting**
     - Description
   * - **$schema**
     - The URI of the JSON schema used for validation and code 
     
       completion with JSON editors. This should not be modified.
   * - **maxModeDownsampling**
     - Use maximum-mode downsampling when reducing cube size before 
     
       uploading to the GPU. This takes the maximum values of the 3D

       windows of voxels (depending on downsampling factors needed

       to reduce the cube size to be under **gpuMemoryLimitMb**) and

       sets individual voxels to those values in the downsampled version

       of the cube. Setting to :literal:`false` will use the slower average mode
       
       that sets the voxel values to the average of the 3D windows. The downsampling
       
       algorithm can be found `here in the iDaVIE source code. <https://github.com/idia-astro/iDaVIE/blob/6f644a5a3ef0b6339cddeaa52438c431023aad54/native_plugins_cmake/data_analysis_tool.cpp#L139>`_
       
       Default: ``true``.
   * - **foveatedRendering**
     - Use static foveated rendering to improve rendering performance at 
     
       the expense of image quality in the periphery of the headset display. 
     
       Default: ``true``.
   * - **bilinearFiltering**
     - Use bilinear filtering when sampling from the data texture on the 
     
       GPU. Smooths cube appearance at the expense of performance. It is 
     
       recommended to leave on ``false`` as this gives voxels in the cube a 
     
       more obvious definition. Default: ``false``.
   * - **gpuMemoryLimitMb**
     - Maximum size (in megabytes) of cubes uploaded to the GPU. Cubes 
     
       larger than this limit will be downsampled before GPU upload.
       
       Stronger GPUs can push this limit higher. Default: ``384``.
   * - **maxRaymarchingSteps**
     - Maximum number of raymarching steps to take when rendering the
     
       cube. A larger number of steps will improve cube appearance when
       
       large cubes are used, at the expense of performance. Default: ``384``.
   * - **angleCoordFormat**
     - Format for angle coordinates. 
     
       Options: ``Sexagesimal``, ``Decimal``. Default: ``Sexagesimal``.
   * - **velocityUnit**
     - Unit for velocity. Options: ``Km``, ``M``. Default: ``Km``.
   * - **defaultColorMap**
     - Default colour map to apply when loading a new cube.
     
       Options: Any of those on `this <https://matplotlib.org/2.2.4/gallery/color/colormap_reference.html>`_ list of matplotlib maps.
       
       Default: ``Inferno``.
   * - **defaultScalingType**
     - Default scaling type to use when applying the colour map to a cube. 
     
       Options: ``Linear``, ``Log``, ``Sqrt``, ``Square``, ``Power``, 
     
       ``Gamma``. Default: ``Linear``.
   * - **voiceCommandConfidenceLevel**
     - Confidence level threshold to use when recognizing voice commands. 
     
       Options: ``High``, ``Medium``, ``Low``, ``Rejected``.
       
       Default: ``Low``.
   * - **flags**
     - The different flag strings that can be applied to sources in a source 
     
       list, and exported with them. Other suggested flags can be letters or 
     
       quality (i.e. "Good", "Bad", etc.). Default: ``["-1", "0", "1"]``.
   * - **histogramIncrementSteps**
     - The number of steps that make up the full range of the min/max
     
       scaling for the histogram in the VR Plots window. Default: ``40``.
   * - **histogramStepsPerSecond**
     - The number of steps per second when incrementing the histogram
     
       min/max scales in the VR Plots window. Default: ``10``.
   * - **useQuickModeForPercentiles**
     - Use the quick, less precise percentile calculation for the scale
     
       min/max that uses the histogram instead of the full data set when
       
       selecting pre-defined histogram percentiles for the min/max scales
       
       in the desktop GUI. Default: ``true``.
   * - **restFrequenciesGHz**
     - Rest frequencies in GHz that can be chosen in the desktop or VR
     
       GUIs. These are used for frequency <-> velocity conversions. Add
       
       more to avoid typing in manually every session. Default: 
     
       ``{"HI": 1.420406, "12CO(1-0)": 115.271, "12CO(2-1)": 230.538, "12CO(3-2)": 345.796, "Halpha": 456806}``.
   * - **tunnellingVignetteOn**
     - Enable tunnelling vignette that adds black region in headset 
     
       peripheries. Default: ``true``.
   * - **tunnellingVignetteIntensity**
     - Intensity of the tunnelling vignette. Default: ``1.0``.
   * - **tunnellingVignetteEnd**
     - End value of the tunnelling vignette. This is how far the vignette 
     
       extends into the view. Default: ``0.40``.
   * - **displayCursorInfoOutsideCube**
     - Allow the controller to display information outside the volume cube. 
     
       Default: ``false``.
   * - **displayVoiceCommandStatus**
     - Display the voice command status in the cursor information.
     
       Default: ``true``.
   * - **usePushToTalk**
     - Enable the requirement that the secondary button on the primary
     
       controller must be held down to use voice commands. This is
       
       recommended for noisy environments. Default: ``false``.
   * - **useSimpleVoiceCommandStatus**
     - Use the simple voice command status indicator. This displays simple
       
       icons to indicate the status of voice commands. Setting this to
       
       false uses a more informative text version. Default: ``true``.
   * - **importedFeaturesStartVisible**
     - Imported sources start visible. Default: ``true``.
   * - **numberOfLogsToKeep**
     - The number of sessions' to keep the log files of. Default: ``5``.

Moment Maps Config Options
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :widths: 15 85
   :header-rows: 1

   * - **Moment Map Setting**
     - Description
   * - **momentMaps.defaultThresholdType**
     - Default threshold type to use when calculating moment maps.
     
       Options\: ``Mask``, ``Threshold``. Default\: ``Mask``.
   * - **momentMaps.defaultLimitType**
     - Default limit type to use when rendering moment maps.
     
       Options\: ``ZScale``, ``MinMax``. Default\: ``ZScale``.
   * - **momentMaps.defaultThreshold**
     - Default threshold value to use when calculating moment maps
     
       with a threshold type. Default: ``0``.
   * - **momentMaps.mom1MaskThreshold**
     - Mask threshold for M1 moment map. Default: ``0``.
   * - **momentMaps.m0.colorMap**
     - Colour map for M0 moment map. Options include any of the
 
       colourmaps found `here <https://matplotlib.org/2.2.4/gallery/color/colormap_reference.html>`_. 
     
       Default: ``Plasma``.
   * - **momentMaps.m0.scalingType**
     - Scaling type for M0 moment map. Options are the same as 
     
       defaultScalingType. Default: ``Sqrt``.
   * - **momentMaps.m1.colorMap**
     - Colour map for M1 moment map. Options include any of the
     
       colourmaps found `here <https://matplotlib.org/2.2.4/gallery/color/colormap_reference.html>`_. 
     
       Default: ``Plasma``.
   * - **momentMaps.m1.scalingType**
     - Scaling type for M1 moment map. Options are the same as 
     
       defaultScalingType. Default: ``Linear``.

Troubleshooting
---------------
In this section we share some useful tips where we found a solution to a known issue:

- Under some circumstances, the voice commands stop working. If this happens, we found that the following sequence of actions usually solves the problem (**NOTE**: this solution has been tested only with Oculus Rift S and on machines where the RealTek Audio driver is installed, we cannot assure it will work for all configurations)

  #. take the headset off 
  
  #. make sure the iDaVIE Desktop GUI is front and centre and no other windows are in front of it
  
  #. use the Windows search function (lower left hand corner - says Type here to search), and type audio
  
  #. open the RealTek Audio Console that will apper after the search
  
  #. check that the Microphone is set to maxium;   toggle <mute> on and then off. Now the mic should be on and ready to receive commands.

  #. close the Audio Console

  #. put the headset back on and use the voice commands as normal.

- If errors are encountered that you can't solve, please:

  #. Post an issue on the Github repository, or,
  
  #. Make contact with us and send us the log files along with your bug reports. The log files can be found in the directory :literal:`iDaVIE/Outputs/Logs`.

Known issues
------------
The following are issues we already know about and that will be fixed as soon as possible:

#. Problem with virus protection systems. We will make a request to Norton to have our software "whitelisted". In the meantime the virus protection does not recognize the .exe and puts up the warning.
