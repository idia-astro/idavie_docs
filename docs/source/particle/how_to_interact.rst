.. _particle_how_to_interact:

How to interact with the particles in VR
========================================

.. note:: This page is part of the preview of iDaVIE-p, the particle side of iDaVIE. It describes features that have not been released yet and may change. See :ref:`particle_overview`.

If you are new to VR, please first read the tips on how to get comfortable in :ref:`how_to_interact`. They apply to iDaVIE-p as well.

How to use the controllers
--------------------------

iDaVIE-p currently provides controller bindings for Meta (Oculus) Touch controllers. The right controller is the primary controller, which is used to point at windows and to select particles. The left controller opens the Quick Menu and shows the compass.

.. note:: The :literal:`Primary Controller Hand` setting in the SETTINGS tab of the desktop GUI can be set to :literal:`Left`, but left-handed use is not fully supported in this preview. We recommend keeping the right hand as the primary hand.

.. image:: /_static/Oculus.png
    :alt: The buttons of a Meta (Oculus) Touch controller
    :width: 80%

.. list-table::
   :widths: 30 70
   :header-rows: 1

   * - **Control**
     - Action
   * - **Grip** (either hand)
     - Hold to grab the data, and move it around with your hand. All datasets move together.
   * - **Grip** (both hands)
     - Hold both grips to scale and rotate the data. Move your hands apart or together to scale. Move one hand forward and the other back to rotate around the vertical axis, or one hand up and the other down to roll. The first rotation you make, of more than 5°, locks the rotation to that axis until you release the grips.
   * - **Trigger** (right)
     - Point the laser at a window and press the trigger to click buttons and drag windows. Also confirms a range or uniform edit (see below).
   * - **A** (right)
     - Hold to select particles with the selection sphere (see below).
   * - **B** (right)
     - Press to switch the selection sphere between adding (green) and removing (red) particles. Hold for 3 seconds to clear the selection of the active dataset.
   * - **Thumbstick** (right)
     - Push left or right to shrink or grow the selection sphere. Push up or down to scroll a list under the laser, or to push or pull a window while you drag it.
   * - **Thumbstick click** (right)
     - Click to look up the particle nearest to the tip of the controller (see below). Hold for 3 seconds to clear the look-up.
   * - **X** (left)
     - Hold to show the compass.
   * - **Y** (left)
     - Hold to show the Quick Menu next to the left controller. See :ref:`particle_gui`.
   * - **Menu** button
     - Not used. This is a Meta function that is unrelated to iDaVIE.

.. note:: The left thumbstick is not used in this preview. Avoid clicking it, as this may change the rendering of the active dataset.

Selecting particles
-------------------

A translucent sphere is always shown at the tip of the right controller. It is green when it adds particles to the selection, and red when it removes them.

#. Hold **A** and move the controller through the data. The particles that the sphere touches are added to the selection, or removed from it.
#. Press **B** to switch between adding and removing.
#. Push the right thumbstick left or right to make the sphere smaller or larger.
#. To start again, hold **B** for 3 seconds, or say :literal:`reset selection`.

Selected particles are highlighted, by default with a colour that stands out against the colour map. The sphere selects particles in all datasets that are marked :literal:`Selectable`, not only in the active dataset. Particles hidden by the filter are skipped by default. These options, and the hold time of the **B** button, can be changed in the SELECTION tab of the desktop GUI (see :ref:`particle_selection_tab`).

The selection of the active dataset, with its statistics, is shown in the SELECTION tab of the desktop GUI and in the VR Selection window. From there, the selection can be exported or turned into a new dataset.

Looking up a particle
---------------------

Click the right thumbstick, or say :literal:`look up`, to find the particle of the active dataset that is nearest to the tip of the right controller. A crosshair marks the particle, and moves with the data.

The values of all columns of the particle are listed in the Particle Inquiry window, which is opened from the Quick Menu. To clear the look-up, hold the right thumbstick click for 3 seconds, say :literal:`reset lookup`, or click the reset button of the Particle Inquiry window.

Compass and cursor position
---------------------------

Hold **X** on the left controller to show a compass. Its three axes show the directions of the X, Y and Z axes of the active dataset, and are labelled with the names of the columns mapped to them.

The position of the tip of the right controller, in the coordinates of the active dataset, is shown next to the right controller.

.. _particle_vr_editing:

Editing the mapping in VR
-------------------------

The mapping of the colour, opacity, size and shape of the particles can be changed without taking off the headset, using the Render Mapping window (see :ref:`particle_gui`) or a voice command:

* **Range edit**: when a property is mapped to a column, say :literal:`edit color`, :literal:`edit opacity`, :literal:`edit size` or :literal:`edit shape`, or click the histogram in the Render Mapping window. Then move your hands sideways: the left controller moves the minimum of the range, and the right controller moves the maximum. The rendering updates as you move.
* **Uniform edit**: when a property is uniform, say the same voice command. Then move the right controller up or down to change the value. One metre of movement covers the full range of values.

Press the right trigger to finish the edit and keep the new values.

Voice commands
--------------

Voice commands can be used as an alternative to the controllers. They are always listening while iDaVIE-p is running. When a command is recognised, the right controller vibrates briefly. All commands are also listed in the Voice Commands window, opened from the Quick Menu, where they can be run by clicking them.

.. list-table::
   :widths: 25 65
   :header-rows: 1

   * - Command
     - Description
   * - **Navigation**
     -
   * - "reset position"
     - Move, rotate and scale all datasets back to where they started.
   * - **Looking up particles**
     -
   * - "look up"
     - Look up the particle nearest to the tip of the right controller.
   * - "reset lookup"
     - Clear the look-up.
   * - **Selection**
     -
   * - "reset selection"
     - Clear the selection of the active dataset.
   * - "export selection"
     - Export the selection of the active dataset to a file. See :ref:`particle_inputs_outputs`.
   * - **Editing the mapping**
     -
   * - "edit color" or "edit colour"
     - Edit the colour mapping. See :ref:`particle_vr_editing`.
   * - "edit opacity"
     - Edit the opacity mapping.
   * - "edit size"
     - Edit the size mapping.
   * - "edit shape"
     - Edit the shape mapping.

.. note:: The :literal:`usePushToTalk` setting of the configuration file has no effect in iDaVIE-p yet.
