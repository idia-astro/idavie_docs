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

