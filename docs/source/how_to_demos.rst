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

Create a movie (using external tools)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

We have found the best way to record sessions in iDaVIE is by activating the VR View window in the SteamVR Status menu:

.. raw:: html

    <img src="_static/SteamVR_view.png"
         style="width:50%;height:auto;">

An external screen recorder can then be used to capture the contents of the VR View window. For this, we recommend users download OBS Studio (https://obsproject.com/download). OBS Studio is a free and open-source software for video recording and live streaming. By setting the recording window to the VR View window, users can record their iDaVIE sessions.

Shape Selection
^^^^^^^^^^^^^^^^^^

Shape selection introduces a new method for using VR to select sub-regions of FITS files rendered by iDaVIE-v. This method of selection will allow you to choose from a selection of shapes to place into your data cube around regions of interest. One, or multiple shapes can be added to create complex selections. In addition to this, the shapes can both add to, and remove from a selection, an example of this is shown at the end of section 2.3. This method allows you to quickly select a region of interest without having to manually paint the entire region using the system’s paint functionality.

How to use Shape Selection

Getting to the shape selection menu

The shape selection is accessible from the paint mode menu. The paint mode menu is accessed by opening the quick menu with your controller, followed by pressing the paint brush icon on the menu:

.. raw:: html

    <img src="_static/shape_selection_tool/1_shape_selection.png"
         style="width:400px; height:auto;">

Once in the paint menu, you will notice a grey button with shapes on it. This is the button that takes you into the shape selection. However, it cannot be selected until you have chosen a source ID. This can be done by selecting a source already in the scene, or creating a new source with the + button. The shape button will then turn white and you can enter the menu:

.. raw:: html

    <img src="_static/shape_selection_tool/2_shape_selection_tool.png"
         style="width:400px; height:auto;">

User Interface for Shape Selection Menu

Upon entering the shape selection you will be presented with the following menu:

.. raw:: html

    <img src="_static/shape_selection_tool/3_shape_selection_tool.png"
         style="width:400px; height:auto;">

Copies all selected shapes. If used immediately after making a selection it will bring back the shapes used into the scene.
Swaps the mode of all selected shapes (additive shapes become subtractive and vice versa).
The following table gives a brief overview of each button from top left to bottom right, more detail about the flow of use of the method is described in section 2.3.

+-------------------+------------------------------------------------------------+
| Button            | Description                                                |
+===================+============================================================+
| Delete            | Deletes all selected shapes from the scene.                |
+-------------------+------------------------------------------------------------+
|                   | Copies all selected shapes. If used immediately after      |
| Copy              | making a selection, it will bring back the shapes used into|
|                   | the scene.                                                 |
+-------------------+------------------------------------------------------------+
| Change shape mode | Swaps the mode of all selected shapes (additive shapes     |
|                   | become subtractive and vice versa).                        |
+-------------------+------------------------------------------------------------+
| Add new shape     | Add a new shape to the scene.                              |
+-------------------+------------------------------------------------------------+
| Undo              | Undoes the previous action.                                |
+-------------------+------------------------------------------------------------+
| Open paint menu   | Open up the paint menu.                                    |
+-------------------+------------------------------------------------------------+
| Confirm Selection | Creates the mask of voxels from the shape(s) in the scene. |
+-------------------+------------------------------------------------------------+
| Exit              | Exits the shape selection.                                 |
+-------------------+------------------------------------------------------------+

Flow for Shape Selection

To begin you can add a new shape to the scene using the Add New Shape button. You will see a grey cube attached to your right controller in the scene:

.. raw:: html

    <img src="_static/shape_selection_tool/4_shape_selection_tool.png" style="width:400px; height:auto;">

You can then use up and down on the joystick with the same controller to cycle through all the shapes available. Once decided, the a button can be pressed to confirm the shape you want. The shape will then turn green:

.. raw:: html

    <img src="_static/shape_selection_tool/5_shape_selection_tool.jpg" style="width:400px; height:auto;">

The green colour indicates that the shape is in additive mode and will add to a selection once the confirm selection button on the shape menu is pressed. To change it to subtractive, either left or right on the joystick will change the mode. Alternatively the change mode button on the menu can be pressed. Once you are happy with the mode, you can move the controller and the shape will follow its position. You can then press the a button to place it into the scene:

.. raw:: html

    <img src="_static/shape_selection_tool/6_shape_selection_tool.jpg" style="width:400px; height:auto;">

The shape can be moved again by placing the controller into the shape and holding down the trigger on the controller. This will attach the shape to your controller as long as the trigger is held. A shape has two states: selected and deselected. When placed into the scene shapes are automatically in the selected state, indicated by their bright colour. To change the state of a shape point at it with the controller and press the trigger:

.. raw:: html

    <img src="_static/shape_selection_tool/7_shape_selection_tool.jpg" style="width:400px; height:auto;">

This then makes the colour of the shape less bright to indicate it is no longer selected. To increase or decrease the size of shapes in the scene you can use up and down on the joystick to increase and decrease the size respectively. This action will apply to all selected shapes in the scene. You can then add more shapes as you wish to isolate the desired region. An example of this is shown below:

.. raw:: html

    <img src="_static/shape_selection_tool/8_shape_selection_tool.jpg" style="width:400px; height:auto;">

The left image is before the mask is created and the right is after. As you can see the green region of the shape is added to the selection, whereas the red shapes remove from the selection. To save the mask, navigate back to the paint or quick menu and select the save option. Note: Large shapes can cause the system to lag or freeze momentarily.

Desktop Selection
^^^^^^^^^^^^^^^^^^^^^

Overview

The desktop selection method introduces a way of masking sources without the use of a VR headset. This method allows you to move through your data slice by slice, circling regions of interest as you progress. Note: this method does not replace the VR selection methods but rather supplements it, the software needs an active headset to run.

How to use Desktop Selection

Getting to the desktop selection interface

The desktop interface is integrated into the already existing desktop UI for iDaVIE-v. Once a file is loaded you simply can select the “Paint” tab to enter the desktop selection mode:

.. raw:: html

    <img src="_static/desktop_selection_tool/1_desktop_selection_tool.jpg" style="width:400px; height:auto;">

User Interface for Desktop Selection

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

Once the desktop selection is open, you would begin by moving to the slice of the source you wish to begin painting. Once there, you simply use your mouse with the left click to draw an enclosed region around the source:

.. raw:: html

    <img src="_static/desktop_selection_tool/2_desktop_selection_tool.jpg" style="width:400px; height:auto;">

Once you are happy, you can either press the Apply Mask button or Space Bar to confirm your selection. The outline will then turn yellow to indicate the selection has taken place:

.. raw:: html

    <img src="_static/desktop_selection_tool/3_desktop_selection_tool.jpg" style="width:400px; height:auto;">

Now, you may not be completely happy with the selection you made. You can either press undo to undo the drawing, or clear to clear all sources with the current source ID on that slice. Alternatively, you can swap to subtractive mode and draw to remove part of your selection:

.. raw:: html

    <img src="_static/desktop_selection_tool/4_desktop_selection_tool.jpg" style="width:400px; height:auto;">

.. raw:: html

    <img src="_static/desktop_selection_tool/5_desktop_selection_tool.jpg" style="width:400px; height:auto;">

Now, if you want to isolate a separate source you can add a new source ID by pressing the + button next to the source ID dropdown. You will notice that the new source you identified is now yellow and the previous source is orange. The yellow indicates the source matching the currently selected source ID.

.. raw:: html

    <img src="_static/desktop_selection_tool/6_desktop_selection_tool.jpg" style="width:400px; height:auto;">

For ease of use, when you traverse to the next slice and find that the sources are similar to the previous slice, you can simply press the Previous Mask button or P on your keyboard to copy the masks you drew in the previous slice over to the next:

.. raw:: html

    <img src="_static/desktop_selection_tool/7_desktop_selection_tool.jpg" style="width:400px; height:auto;">

Finally, once you are happy with your mask you can save it as a new mask or overwrite a previously uploaded mask file.