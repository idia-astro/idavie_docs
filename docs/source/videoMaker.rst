.. _videoMaker:

Recording videos in iDaVIE
==========================

With iDaVIE you can create smooth videos of your data using iDaVIE Video Scripts (IDVS).
This page details each step of this process: recording video positions in VR, to editing the IDVS generated from this, to loading this script in the desktop interface and creating the video.
Before this, the requirements for using the video feature are discussed.


Requirements
------------

To create videos, iDaVIE requires an `FFmpeg <https://github.com/FFmpeg/FFmpeg>`_ executable. 
You can download a pre-compiled FFmpeg executable from Windows `here <https://www.gyan.dev/ffmpeg/builds/ffmpeg-release-full.7z>`_.
Once you have downloaded the zipped files, extract them and store it in a location that you will remember, for example, your Documents folder.
iDaVIE will ask you to locate the FFmpeg executable later.


Recording video positions in VR
-------------------------------

iDaVIE provides functionality that allows the user to capture perspectives within the VR space. These perspectives can be exported to a file, which can then be used to generate a stable and smooth video.

.. raw:: html

   <iframe width="560" height="315" src="https://www.youtube.com/embed/Jh-1LdrYnI8?si=gzbQ8rWtNmOOK0YW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

See :ref:`videomakerui` for an explanation of the UI elements used for this functionality.

----

IDVS Scripting Language
-----------------------

The IDVS scripting language is used to control video recordings — defining camera positions, movements, and global recording settings.
Each line in an IDVS script defines one instruction or configuration. Exporting a list of perspectives from the VR generates an :literal:`.idvs` file with a list of positions defined and basic scaffolding for a complete IDVS script.

A full reference and documentation for the language can be found at :ref:`idvs_ref`. A summary of commands are presented below.

Summary of Commands
^^^^^^^^^^^^^^^^^^^

+-------------+-------------------------------------------------------------+-----------------------------------------------+
| **Command** | **Syntax**                                                  | **Purpose**                                   |
+=============+=============================================================+===============================================+
| **Position**| ``<alias> is {[X,Y,Z],[x,y,z]}``                            | Define a camera position and rotation         |
+-------------+-------------------------------------------------------------+-----------------------------------------------+
| **Start**   | ``Start at <alias>``                                        | Set initial camera position                   |
+-------------+-------------------------------------------------------------+-----------------------------------------------+
| **Wait**    | ``Wait <n> seconds``                                        | Pause for ``<n>`` seconds                     |
+-------------+-------------------------------------------------------------+-----------------------------------------------+
| **Move**    | ``Move in <method> to <alias> over <n> seconds``            | Move camera to ``<alias>``                    |
+-------------+-------------------------------------------------------------+-----------------------------------------------+
| **Rotate**  | ``Rotate around <alias> <n> times [turn <t>] [orbit <o>]``  | Rotate camera around a specific point         |
+-------------+-------------------------------------------------------------+-----------------------------------------------+
| **Setting** | ``<name>: <value>``                                         | Set a global configuration                    |
+-------------+-------------------------------------------------------------+-----------------------------------------------+

Previewing and Exporting videos
-------------------------------

The interface for previewing and exporting IDVS to videos can be found in the RENDER tab of the iDaVIE desktop GUI.

.. raw:: html

   <img src="_static/GUI/VideoMaker_RENDER_IDVS_annotated.png"
        style="width:100%;height:auto;">

1) The name of the IDVS currently loaded.
2) Button to find and load an IDVS, opens a file explorer.
3) Button to reload the current IDVS from disk. This is useful when making iterative changes to the current IDVS.
4) Button to play the video in "Preview" mode. The video will not be exported to a file, but performance is better than exporting. This button is only visible if an IDVS is loaded.
5) Button to "Export" the video to an mp4 file in :literal:`Output/Video`. A preview of the video is also show, however this preview may not be in real-time (depending on the frame-rate of the exported video) and performance will not be as good as Preview mode. This button is only visible if an IDVS is loaded.

If you press the Preview button, the video will be previewed in the GUI:

.. raw:: html

   <img src="_static/GUI/VideoMaker_RENDER_playing_annotated.png"
        style="width:100%;height:auto;">

1) View of the video being previewed. Replaces the usual VR View.
2) Text indicates "Preview" mode. If the Export button was pressed, this would display "Export Video".
3) Button to "Pause" the video preview. If pressed the video preview will be paused, and may be resumed by pressing the "Resume" button that replaces this.
4) Button to "Stop" the video preview.
5) The progress of the video. The text indicates if the video preview is "Playing" or if it is "Paused".
6) A slider to adjust the preview quality (resolution) of the video, provided in case of poor performance during preview. With the slider to the right, the video will be previewed at the full resolution as specified by the IDVS. With the slider towards the left, the video will preview at a lower resolution than this. The slider is only available during "Preview" mode and the slider position will not affect the output resolution of the video.

When you are satisfied with the video preview, you may wish to export the video.
To do this, press the Export button.
The first time you press the Export button a file dialogue will pop-up asking you to "Open the FFmpeg executable". This will also happen if the FFMPEG install is no longer valid.
Navigate to the file location where you stored the FFmpeg folder, select the :literal:`bin/ffmpeg.exe` file.

.. raw:: html

   <img src="_static/GUI/VideoMaker_RENDER_File_FFmpeg_blurred.png"
        style="width:100%;height:auto;">

The exported video can be found in :literal:`Output/Video`, and will have the same filename as the IDVS with an additional time-stamp at the end for when the video was made.

.. WARNING:: If the data cube is too zoomed in or out, this can affect the video and you may need to go into VR to change the level of zoom. If the nearest parts of the cube are cut-off when the camera enters it, then you are probably too zoomed out (the cube is too small). Conversely, if distant parts of the cube are cut-off, then you are probably too zoomed in (cube is too big).
