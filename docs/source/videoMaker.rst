.. _videoMaker:

Recording videos in iDaVIE
==========================

Recording video positions in VR
-------------------------------

iDaVIE provides functionality that allows the user to capture perspectives within the VR space. These perspectives can be exported to a file, which can then be used to generate a stable and smooth video.

.. raw:: html

   <iframe width="560" height="315" src="" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

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
Lorem ipsum pretty annotated pictures.

Video Maker Backend
-------------------

Lorem ipsum, Mayhew, figure out what to copy from the discussion page to here, if any.