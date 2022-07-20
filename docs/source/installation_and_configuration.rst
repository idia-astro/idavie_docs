.. _installation_configuration:

Installation and configuration
==============================
.. note:: The current version of the software is in beta testing so please be aware that issues might arise. We also appreciate your collaboration in identifying them and, if you do, please post them in the issue page on `Github <https://github.com/idia-astro/idavie_releases/issues>`_. All issues will be fixed for the first data release. 

Executable
-----------
Once the requirements described in :ref:`requirements`, are installed and working correctly, the user can download and unzip the provided :literal:`iDAVIE-v_v.0-beta.7.zip`, which contains the executable .exe (and other reference files). The zip file is available on Github at this `link <https://github.com/idia-astro/idavie_releases/releases/download/v1.0-beta.7/iDaVIE-v_v1.0-beta.7.zip>`_.

.. raw:: html

    <img src="_static/idavie-pkg-edit.png"
         style="width:100%;height:auto;">

To start the software, double-click on the executable iDaVIE-v file.
 

Source code
-----------
Currently not available. The source code will be made available after beta is completed.

Troubleshooting
---------------
In this section we share some useful tips where we found a solution to a known issue:

- Under some circumstances the voice commands stop to work. If this happens we found that the following sequence of actions solves the problem (**NOTE**: this solution has been tested only with Oculus Rift S and on machines where the RealTek Audio driver is installed, we cannot assure it will work for any set up)

  #. take the headset off 
  
  #. make sure the iDaVIE-v Desktop GUI is front and center and no other windows are in front of it
  
  #. use the Windows search function (lower left hand corner - says Type here to search), and type audio
  
  #. open the RealTek Audio Console that will apper after the search
  
  #. check that the Microphone is set to maxium;   toggle <mute> on and then off. Now the mic should be on and ready to receive commands.

  #. close the Audio Console

  #. put the headset back on and use the voice commands as normal.

- If errors are encountered that you can't solve, please:

  #. post and issue on the Github repository
  
  #. make contact with us and send us the log files along with your bug reports. The log files can be found in the directory :literal:`%appdata%/../LocalLow/IDIA/iDaVIE-v`. In order to find this directory using Windows please press :literal:`WIN + R` to open the run dialog, and paste the path directory in to open the folder). 
  
.. WARNING:: Unity only allows for a maximum of two log files to be stored. Therefore, if a problem is encountered with iDaVIE-v is best to copy the log file to a different folder **BEFORE** starting a new iDaVIE-v session otherwise the log file reporting the specific problem encountered will be lost.

Known issues
------------
The following are issues we already know about and that will be fixed as soon as possible:
 
#. In order to paint, a region must be selected and cropped to
#. Problem with virus protection systems. We will make a request to Norton to have our software "whitelisted". In the meantime the virus protection does not recognize the .exe and puts up the warning. See more details `here <https://www.symantec.com/connect/forums/how-avoid-wsreputation1-error>`_
#. A DLL deployment bug has been found in v1.0-beta.0 and has been fixed in v1.0-beta.1 and later versions. We refere the user to the latest version to solve this issue.
#. Issues loading frequency-based cubes have beeen fixed in v1.0-beta.2 and later versions.

