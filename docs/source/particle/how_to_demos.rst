.. _particle_how_to_demos:

"How to" demos
==============

.. note:: This page is part of the preview of iDaVIE-p, the particle side of iDaVIE. It describes features that have not been released yet and may change. See :ref:`particle_overview`.

The following demos use the sample table that comes with the iDaVIE-p source code, :literal:`Data/SampleData/test_catalog.fits` (see :ref:`particle_inputs_outputs`). Each row of this table links two galaxies of the 2MRS survey that belong to the same friends-of-friends group. The positions of the first galaxy are in the columns :literal:`X1`, :literal:`Y1` and :literal:`Z1`. The :literal:`Weight` column, with values from 0.1 to 1, gives the strength of the link.

Render a table
^^^^^^^^^^^^^^

#. Start iDaVIE-p. In the LOAD tab, click :literal:`Load Data Table` and choose :literal:`test_catalog.fits`.
#. The :literal:`X:`, :literal:`Y:` and :literal:`Z:` dropdowns show :literal:`X1`, :literal:`Y1` and :literal:`Z1`, the first three numeric columns. Keep them, and keep the :literal:`Initial Size (m)` of 5 m.
#. Click :literal:`Render Data`. When the progress bar turns green, the desktop GUI switches to the VR view.
#. Put on the headset. Grab the data with one grip to move it, and with both grips to scale and rotate it (see :ref:`particle_how_to_interact`).

.. image:: /_static/particle/demo_render.png
    :alt: The 2MRS sample table rendered in iDaVIE-p
    :width: 100%

Change the mapping on the desktop
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Open the RENDERING tab. In the :literal:`Color` block, uncheck :literal:`Uniform` and choose :literal:`Weight` as the source. The particles are now coloured by the strength of their links, with the :literal:`Plasma` colour map.
#. Choose another colour map in the dropdown under the histogram, e.g. :literal:`Viridis`.
#. In the :literal:`Opacity` block, uncheck :literal:`Uniform`, choose :literal:`Weight`, and drag the left handle of the range slider to the right. Weakly linked galaxies fade out.
#. Check :literal:`Invert` in the :literal:`Opacity` block to do the opposite, and make the weakly linked galaxies stand out.
#. Click :literal:`Save Mapping File` to keep this mapping. It can be loaded again with :literal:`Load Mapping File` in the LOAD tab (see :ref:`particle_mapping_files`).

Change the mapping in VR
^^^^^^^^^^^^^^^^^^^^^^^^

#. In VR, hold **Y** on the left controller to open the Quick Menu, and click :literal:`Render Parameter Tuning` to open the Render Mapping window.
#. Click :literal:`Color` at the top of the grid. The upper part of the window shows the histogram of the column mapped to the colour.
#. Click the histogram. Move your left hand sideways to change the minimum of the range, and your right hand to change the maximum. Press the right trigger when you are happy with the result.
#. To give all particles the same size, click the :literal:`Size` cell of the :literal:`Uniform` row. Then say :literal:`edit size`, and move your right hand up or down to change the size. Press the right trigger to finish.
#. To change the colour map, open :literal:`Colormaps` from the Quick Menu and click a colour map.

Show only part of the data with a filter
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. In the LOAD tab, open the :literal:`Filter` section.
#. Choose the column :literal:`Weight`, the operator :literal:`>=` and enter the value :literal:`0.9`. Click :literal:`Add Condition`.
#. Click :literal:`Apply Filter`. Only the galaxies with strong links are shown.
#. Check :literal:`Invert Filter` to show only the galaxies with weak links instead, or uncheck :literal:`Enable Filter` to show all galaxies again.

Select particles in VR and look at their statistics
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. In VR, move the tip of the right controller to a group of galaxies. Push the right thumbstick left or right to change the size of the green sphere.
#. Hold **A** and sweep the sphere through the group. The selected galaxies are highlighted.
#. Press **B** to switch to the red sphere, and hold **A** to remove galaxies from the selection. Press **B** again to go back to adding.
#. On the desktop, open the SELECTION tab. It shows the number of selected galaxies. Under :literal:`Statistics`, choose the :literal:`Z1` column to see the distribution of the selected galaxies along the Z axis, compared with all galaxies. In VR, the same information is shown in the Selection window, opened from the Quick Menu.

.. image:: /_static/particle/selection_stats.png
    :alt: Statistics of the selected particles in the SELECTION tab
    :width: 50%

Select particles by condition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. In the SELECTION tab, click :literal:`Clear Selection`.
#. In the :literal:`Select by condition` section, choose the column :literal:`Weight`, the operator :literal:`between` and enter :literal:`0.4, 0.6`. Click :literal:`Add Condition`.
#. Click :literal:`Add Matching`. The status line shows how many galaxies were added.
#. To refine the selection, add other conditions and click :literal:`Remove Matching`, or select more galaxies in VR.

Export a selection, or explore it as a new dataset
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Click :literal:`Export Selection` in the SELECTION tab, or say :literal:`export selection` in VR. The selected rows are written to a new FITS file in :literal:`Outputs/Tables`. The status line shows its path.
#. Click :literal:`New Dataset from Selection`. A new dataset, :literal:`test_catalog selection`, is created with only the selected galaxies, and the original dataset is hidden. The new dataset can be filtered, mapped and selected like any other dataset.
#. To return to the full table, remove the new dataset in the :literal:`Loaded tables` tab, or show the original dataset again with its eye button.

Look up a particle
^^^^^^^^^^^^^^^^^^

#. In VR, open the Quick Menu and click :literal:`Inquiry Window`.
#. Move the tip of the right controller next to a galaxy and click the right thumbstick, or say :literal:`look up`. A crosshair marks the nearest galaxy, and the Particle Inquiry window lists all its values.
#. Hold the right thumbstick click for 3 seconds, or say :literal:`reset lookup`, to clear it.
