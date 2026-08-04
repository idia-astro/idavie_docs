.. _idvs_ref:

IDVS Scripting Language Reference
---------------------------------

**Version:** 1.0  
**Purpose:**  
The IDVS scripting language is used to control video recordings — defining camera positions, movements, and global recording settings.  
Each line in an IDVS script defines one instruction or configuration.

Table of Contents
^^^^^^^^^^^^^^^^^

1. `Basic Rules`_  
2. `Script Structure`_  
3. `Position Declarations`_  
4. `Commands`_  
    - `Start`_  
    - `Wait`_  
    - `Move`_  
    - `Rotate`_  
5. `Settings`_  
6. `Error Handling`_  
7. `Tips and Best Practices`_  
8. `Example Full Script`_  
9. `Summary of Commands`_

Basic Rules
^^^^^^^^^^^

* Each instruction must be written **on its own line**.  
* **Blank lines** are allowed (ignored).  
* **Comments** start with ``#`` and continue to the end of the line.  
* Commands are **case-sensitive**.  
* Indentation and extra spaces are ignored.
* Files exported from iDaVIE contain a number of comments explaining basic functionality.

**Example:**

.. code-block:: text

   # This is a comment
   Start at introPosition
   Wait 3 seconds

Script Structure
^^^^^^^^^^^^^^^^

An IDVS script generally contains three types of statements:

+---------------------------+--------------------------------------------------------------+
| **Type**                  | **Description**                                              |
+===========================+==============================================================+
|                           | Define named 3D positions and orientations used by movement  |
| **Position declarations** | and rotation commands. These positions are exported from the |
|                           | iDaVIE video location mode.                                  |
+---------------------------+--------------------------------------------------------------+
| **Commands**              | Control camera actions (start, move, wait, rotate, etc.).    |
+---------------------------+--------------------------------------------------------------+
| **Settings**              | Configure global video options (logo placement, quality).    |
+---------------------------+--------------------------------------------------------------+


Position Declarations
^^^^^^^^^^^^^^^^^^^^^

Define a named camera position and orientation. **Note**: these positions will almost always be exported from the iDaVIE video mode.

**Syntax:**

.. code-block:: text

   <alias> is {[X,Y,Z],[x,y,z]}

**Parameters:**

- ``<alias>`` — name used later in the script (letters/numbers/underscores only). These will be `p1`` to `pN` when exported from iDaVIE's video mode.
- ``[X,Y,Z]`` — camera position in 3D space  
- ``[x,y,z]`` — camera rotation (in degrees)

**Example:**

.. code-block:: text

   p1 is {[0,0,0],[0,0,0]}
   p2 is {[10,5,0],[0,180,0]}

**Notes:**

- Parentheses ``()`` can be used instead of square brackets ``[]``.  
- Redeclaring an alias overwrites the old one (warning issued).

Commands
^^^^^^^^

*Start*
_______

Sets the initial camera position.

**Syntax:**

.. code-block:: text

   Start at <positionAlias>

**Example:**

.. code-block:: text

   Start at p1

*Wait*
______

Pauses the camera movement for a given duration.

**Syntax:**

.. code-block:: text

   Wait <seconds> seconds

**Example:**

.. code-block:: text

   Wait 2 seconds

*Move*
______

Moves the camera from the current position to a defined destination.

**Syntax:**

.. code-block:: text

   Move in <method> to <positionAlias> over <N> seconds

**Parameters:**

- ``<method>`` — movement interpolation method (e.g., ``LINE``, ``ARC``.)  
- ``<positionAlias>`` — destination position (must be defined earlier)  
- ``<seconds>`` — time duration of the move  

**Example:**

.. code-block:: text

   Move in LINE to target over 5 seconds

**Error Conditions:**

- Unknown method → *“Invalid move method”*  
- Unknown position alias → *“Invalid position alias”*

*Rotate*
________

Rotates the camera around a defined position.  
Several variants are supported for specifying timing and rotation behavior.

+---------------------------------+--------------------------------------------------------------------------+
| **Variant**                     | **Syntax**                                                               |
+=================================+==========================================================================+
| **Basic**                       | ``Rotate around <alias> <n> times``                                      |
+---------------------------------+--------------------------------------------------------------------------+
| **Turn**                        | ``Rotate around <alias> <n> times turn <t> seconds``                     |
+---------------------------------+--------------------------------------------------------------------------+
| **Orbit**                       | ``Rotate around <alias> <n> times orbit <t> seconds``                    |
+---------------------------------+--------------------------------------------------------------------------+
| **Full (turn + orbit)**         | ``Rotate around <alias> <n> times turn <t1> seconds orbit <t2> seconds`` |
+---------------------------------+--------------------------------------------------------------------------+
| **Full (orbit + turn)**         | ``Rotate around <alias> <n> times orbit <t1> seconds turn <t2> seconds`` |
+---------------------------------+--------------------------------------------------------------------------+

**Examples:**

.. code-block:: text

   Rotate around p3 3 times
   Rotate around p2 2 times orbit 4 seconds
   Rotate around p5 2 times turn 1 seconds orbit 3 seconds

Settings
^^^^^^^^

Settings modify global video parameters.

**Syntax:**

.. code-block:: text

   <settingName>: <value>

**Examples:**

.. code-block:: text

   logopos: topRight
   framerate: 25

**Valid Settings:**

+---------------+-----------------------------+-------------------------------------------+
| **Setting**   | **Description**             | **Values**                                |
+===============+=============================+===========================================+
| ``logopos``   | Logo position in the video  | ``topLeft``, ``topRight``, ``bottomLeft``,|
|               |                             | or ``bottomRight``                        |
+---------------+-----------------------------+-------------------------------------------+
| ``Width``     | The width of the video.     | Integer value.                            |
+---------------+-----------------------------+-------------------------------------------+
| ``Height``    | The height of the video.    | Integer value.                            |
+---------------+-----------------------------+-------------------------------------------+
| ``Framerate`` | The framerate of the video. | Integer value.                            |
+---------------+-----------------------------+-------------------------------------------+

**Error Conditions:**

- Invalid setting name → *“Invalid setting name”*  
- Invalid logo position → *“Invalid logo position value”*  
- Invalid number → *“Format exception”*

Error Handling
^^^^^^^^^^^^^^

Errors encountered during parsing are reported in the iDaVIE log with the line number and a description.

**Example:**

.. code-block:: text

   Parse error in example.idvs:12: Invalid position alias `p999`.

Warnings (e.g., redefined aliases) do not stop execution.

Tips and Best Practices
^^^^^^^^^^^^^^^^^^^^^^^

* Define all positions **before** using them.  
* Use **descriptive aliases** like ``intro``, ``outro``, or ``focusPoint``. 

Example Full Script
^^^^^^^^^^^^^^^^^^^

.. code-block:: text

   # Video settings
   Height : 720
   Width : 1280
   FrameRate : 25
   LogoPos : BR

   # List of positions:
   # Takes the form:
   #    <alias> is {<location>, <direction>}
   # Alias can be any combination of characters, excluding whitespace.
   # Both location and direction are Vector3, printed in the form `(x, y, z)`,
   # and are relative to the datacube's normalised position and rotation.

   p1 is {(0.009, -0.075, -1.555), (9.131, 359.630, 357.958)}
   p2 is {(-0.008, -0.067, -0.695), (5.768, 359.589, 358.856)}
   p3 is {(0.849, 0.026, -0.030), (4.458, 268.075, 358.467)}
   p4 is {(0.221, -0.183, 0.055), (0.000, 0.000, 0.000)}

   # Script:
   # Accepted commands (see documentation for details):
   #    - Start at <alias>
   #    - Wait <n> seconds
   #    - Move in <METHOD> to <alias> over <n> seconds
   #        - Methods allowed: (LINE, ARC)
   #    - Rotate around <alias> <n> times

   Start at p1
   Wait 1 seconds
   Move in LINE to p2 over 2 seconds
   Move in ARC to p3 over 2 seconds
   Wait 1 seconds
   Rotate around p4 1 times
   Wait 1 seconds
   Move in ARC to p2 over 2 seconds
   Move in LINE to p1 over 2 seconds
   Wait 1 seconds

----

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