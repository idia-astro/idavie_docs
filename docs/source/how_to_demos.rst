.. _how_to_demos:

"How to" demos
==============

In this section we display example videos that should intuitively explain how to use iDaVIE. We made use of a sample data cube of the Fornax galaxy cluster, which is `available at this link <https://sites.google.com/inaf.it/meerkatfornaxsurvey/data#h.p_m3V9IHl56i6D>`_. The *Loni et al. (2021)* paper that gives more details about the data is `available here <https://ui.adsabs.harvard.edu/abs/2021A%26A...648A..31L/abstract>`_. We also use a mask that was created using the `HI Source Finding Application (SoFiA) <https://gitlab.com/SoFiA-Admin/SoFiA-2>`_.

Explore a cube
^^^^^^^^^^^^^^

Using the controls described in :ref:`how_to_interact`, the user can zoom in on the data and move the data where needed using the grip buttons. 

.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/yf-TmP5sesI?si=M8ZuKQktIgxgYJz6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Then with the A button (if the primary hand is the right) or the X button (if the primary hand is the left) the user can select a region around a point of interest.

.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/VFrSUYU6nF8?si=Ex_8Y4W9yK2l7-J6" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The user can then use the voice command "Crop selection" to crop the cube to the region selected.

.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/Ws8S2pUlLWo?si=twyI28LuEsJSO5cm" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

The 3D cursor will provide information about the current voxel under the cursor. If a mask is loaded, then the cursor info will also provide feedback on the identified sources, for example:

.. raw:: html

  <img src="_static/Cursor-feedback.png" style="width:560px; height:315px;">


The controller can also be used to adjust the minimum and maximum thresholds of the applied colour map of the cube. Using the "Edit min" or "Edit max" voice command, the user can move the primary controller up and down to adjust either threshold:


.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/VYKYdpFMMlA?si=ZgPHoCYGdqgxmYyM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  <div style="height: 20px;"></div>

Take snapshots
^^^^^^^^^^^^^^
iDaVIE allows the user to take a "screenshot" of their current view in the VR environment, saved to :literal:`Outputs\Camera\Screenshot_yyyyMMdd_Hmmss.png`, where :literal:`yyyyMMdd_Hmmss` is the current timestamp. To do so, the user can do any of the following:

#. Invoke the quick menu and laser on the camera icon and press the trigger (of the primary hand) while looking in the direction of the area of interest (i.e., if the user looks at the menu when pressing the trigger, then the picture will contain only the menu).

#. While looking at the area of interest, the user can say "take picture". If the image was taken sucessfully, the user will receive haptic feedback (vibration) on the primary hand controller.

Create/modify/save a mask
^^^^^^^^^^^^^^^^^^^^^^^^^
iDaVIE allows the user to create a mask or to modify an existing mask in VR. Both can be done using the "Paint menu" action that can be invoked from the "Quick menu" by lasering the brush icon. Using the functionality available in the "Paint menu", the user can add or delete mask voxels using the controllers. Once done, the user can save the created/updated mask by either overwriting an existing mask or creating a new one. As also explained in :ref:`inputs_outputs`:

* if a mask is loaded and modified in VR, then it can be saved by either overwriting the original mask **or**  as a copy. In the former case, the mask will be saved with the same name of the original mask and in the same directory, while in the latter case, the suffix :literal:`-copy.fits` will be added to the original mask name and the edited mask will be saved in the same directory as the original mask (i.e., the edited mask file name will then be :literal:`originalmaskname-copy.fits`).
* if no mask is provided in input, but one is created in iDaVIE, then the created mask is saved in the same directory of the data cube and a suffix :literal:`-mask.fits` will be added to the cube name to indicate the mask file (e.g. the created mask file name will then be :literal:`originalcubename-mask.fits`).

.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/78CIIWJQH1g?si=1Dwb0LTDZRXPhJuG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
  <div style="height: 20px;"></div>

Interact with catalogs in VR
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
iDaVIE allows the user to load catalogs from the Desktop GUI and overplot them on the visualised data cube.

.. raw:: html

        <iframe width="560" height="315" src="https://www.youtube.com/embed/GlRHiW6QV2U?si=gkU-252yYNvRgNLg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
        <div style="height: 20px;"></div>

Create statistics and save moment maps
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

iDaVIE allows the user to investigate the basic statistics of the cube and to create both moment 0 and moment 1 maps of a data cube. The user can create the moment maps for the entire cube or for a single selected region. In case a mask is available, the moment maps thresholds are set by the mask, but they can be changed manually. If no mask is available, then the thresholds should be set manually using the options available in the moment map windows. The moment maps can then be saved as a png or 2D fits image.

.. raw:: html

  <iframe width="560" height="315" src="https://www.youtube.com/embed/A1CE3WxVHs0?si=vHhrd6YxSUP1Z_SO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


.. raw:: html

    <img src="_static/MMap-slide.png"
         style="width:560px; height:315px;">
    <div style="height: 20px;"></div>

Create a movie using iDaVIE
^^^^^^^^^^^^^^^^^^^^^^^^^^^
iDaVIE provides an extensive video recording mode, with more detail available at :ref:`videoMaker`.

.. raw:: html

   <iframe width="560" height="315" src="https://www.youtube.com/embed/Jh-1LdrYnI8?si=gzbQ8rWtNmOOK0YW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Desktop Selection
^^^^^^^^^^^^^^^^^^^^^

Overview
--------

The desktop selection method introduces a way of masking sources without the use of a VR headset. This method allows you to move through your data slice by slice, circling regions of interest as you progress. Note: this method does not replace the VR selection methods but rather supplements it, the software needs an active headset to run.

How to use Desktop Selection
----------------------------

The desktop interface is integrated into the already existing desktop UI for iDaVIE-v. Once a file is loaded you simply can select the “Paint” tab to enter the desktop selection mode:

.. raw:: html

    <img src="_static/desktop_selection_tool/1_desktop_selection_tool.jpg" style="width:40%;height:auto;">

User Interface for Desktop Selection
------------------------------------

The desktop selection interface, as shown above, has two primary components. The first being the left half of the screen which represents a 2D slice of the data that you are currently viewing. This is where you can draw to make selections. Below are several buttons relating to actions that can be performed on this window. The right half of the screen displays several settings that can be toggled, described from top to bottom in the following table:

+-----------------------+---------------------------------------------------------------+
| Setting               | Description                                                   |
+=======================+===============================================================+
| Slice slider          | Allows you to move between slices. The left and right arrow   |
|                       | keys can also be used for this.                               |
+-----------------------+---------------------------------------------------------------+
| Axis                  | Allows you to change which axis the slices are moving through.|
+-----------------------+---------------------------------------------------------------+
| Source ID             | Allows you to set the source ID, or add new sources.          |
+-----------------------+---------------------------------------------------------------+
| Colour Map            | Allows you to change the colour map the data is rendered in.  |
+-----------------------+---------------------------------------------------------------+
| Selection Mode        | Similar to shape selection, allows you to toggle between      |
|                       | additive and subtractive selection.                           |
+-----------------------+---------------------------------------------------------------+
| Save Mask             | Options for saving a mask.                                    |
+-----------------------+---------------------------------------------------------------+
| VR View               | Gives a view of the data in 3D to represent which slice of the|
|                       | data is currently being displayed.                            |
+-----------------------+---------------------------------------------------------------+

Flow for Desktop Selection
--------------------------

Once the desktop selection is open, you would begin by moving to the slice of the source you wish to begin painting. Once there, you simply use your mouse with the left click to draw an enclosed region around the source:

.. raw:: html

    <img src="_static/desktop_selection_tool/2_desktop_selection_tool.jpg" style="width:40%;height:auto;">

Once you are happy, you can either press the Apply Mask button or Space Bar to confirm your selection. The outline will then turn yellow to indicate the selection has taken place:

.. raw:: html

    <img src="_static/desktop_selection_tool/3_desktop_selection_tool.jpg" style="width:40%;height:auto;">

Now, you may not be completely happy with the selection you made. You can either press undo to undo the drawing, or clear to clear all sources with the current source ID on that slice. Alternatively, you can swap to subtractive mode and draw to remove part of your selection:

.. raw:: html

    <img src="_static/desktop_selection_tool/4_desktop_selection_tool.jpg" style="width:40%;height:auto;">

.. raw:: html

    <img src="_static/desktop_selection_tool/5_desktop_selection_tool.jpg" style="width:40%;height:auto;">

Now, if you want to isolate a separate source you can add a new source ID by pressing the + button next to the source ID dropdown. You will notice that the new source you identified is now yellow and the previous source is orange. The yellow indicates the source matching the currently selected source ID.

.. raw:: html

    <img src="_static/desktop_selection_tool/6_desktop_selection_tool.jpg" style="width:40%;height:auto;">

For ease of use, when you traverse to the next slice and find that the sources are similar to the previous slice, you can simply press the Previous Mask button or P on your keyboard to copy the masks you drew in the previous slice over to the next:

.. raw:: html

    <img src="_static/desktop_selection_tool/7_desktop_selection_tool.jpg" style="width:40%;height:auto;">

Finally, once you are happy with your mask you can save it as a new mask or overwrite a previously uploaded mask file.