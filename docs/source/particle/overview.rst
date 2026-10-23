.. _particle_overview:

Overview
========

.. note:: This section is a **preview** of iDaVIE-p, the particle side of iDaVIE, which has not been released yet. The features described here may change before the release. These pages describe the ``alex/selection_tab`` branch (commit ``dfc5353``) of the iDaVIE-particle-work repository. This repository is currently only available to collaborators. See :ref:`particle_build`.

iDaVIE-p renders tables of points in virtual reality. Each row of a table is drawn as a particle. The columns of the table set the position of each particle, and can also set its colour, opacity, size and shape. This makes iDaVIE-p well suited to sparse, multiparameter data, such as galaxy catalogues, all-sky surveys and particle simulations.

iDaVIE-p uses the same VR environment as the volume side of iDaVIE. The way you move and scale the data with the controllers, and the VR windows, will be familiar to users of iDaVIE-v.

Workflow
--------

A typical session with iDaVIE-p looks like this:

#. **Load** a table in the LOAD tab of the desktop GUI: choose the columns for the X, Y and Z positions, then render it. See :ref:`particle_load_tab` and :ref:`particle_inputs_outputs`.
#. **Map** the columns of the table to the colour, opacity, size and shape of the particles, in the RENDERING tab or from VR. See :ref:`particle_rendering_tab` and :ref:`particle_mapping_files`.
#. **Explore** the data in VR: move, rotate and scale it, and look up the values of individual particles. See :ref:`particle_how_to_interact`.
#. **Filter** the particles to show only the ones that match a set of conditions. See :ref:`particle_filter`.
#. **Select** particles in VR or by condition, and look at the statistics of the selection. See :ref:`particle_selection_tab`.
#. **Export** the selected particles to a new table, or turn them into a new dataset to explore further. See :ref:`particle_inputs_outputs`.

Step-by-step examples are given in :ref:`particle_how_to_demos`.

.. _particle_multiple_datasets:

Multiple datasets
-----------------

Several tables can be loaded at the same time. To load another table, click :literal:`New Table...` in the :literal:`Loaded tables` tab of the desktop GUI, then load and render the table as usual.

* The first dataset that was rendered is the *primary* dataset. Datasets rendered later use the same scaling as the primary dataset, so that all datasets share the same frame. This means that the datasets line up correctly, as long as their coordinates are in the same units and the same coordinate system. Changing the :literal:`Initial Size (m)` of an axis of a later dataset takes it out of this shared frame.
* If the primary dataset is removed, the next dataset in the list becomes the primary dataset.
* One dataset at a time is the *active* dataset. The LOAD, RENDERING and SELECTION tabs act on the active dataset. Choose it in the :literal:`Loaded tables` tab, or in the VR Data List window.
* Each dataset has its own mapping, filter and selection. Each dataset can be hidden, and can be excluded from selections in VR by unchecking :literal:`Selectable`.

Examples
--------

.. figure:: /_static/2mrs_logo.gif
    :alt: iDaVIE-p used with 2MRS survey data
    :width: 60%

    Results of the Friends-of-Friends (FoF) algorithm applied to the 2MRS survey, showing the large-scale structure of the nearby universe. See `(Lambert et al. 2019) <http://ui.adsabs.harvard.edu/abs/2020MNRAS.497.2954L/abstract>`_ for more details.

.. figure:: /_static/cosmo_logo.gif
    :alt: iDaVIE-p used with a cosmological simulation
    :width: 60%

    A single snapshot of a cosmological simulation run with a smoothed particle hydrodynamics (SPH) code. See `(Huang et al. 2019) <https://academic.oup.com/mnras/article/484/2/2021/5288633>`_ for more background on the data used.

More examples are shown in :ref:`multidisciplinary`.

.. _particle_known_limitations:

Known limitations
-----------------

As a preview, iDaVIE-p has some limitations that will be addressed before the release:

* Controller bindings are only provided for Meta (Oculus) Touch controllers. Other controllers need bindings to be set up in SteamVR.
* Support for IPAC tables (:literal:`.tbl`) is incomplete. Please use FITS or CSV tables. See :ref:`particle_inputs_outputs`.
* Files with the extensions :literal:`.fit` and :literal:`.fts` cannot be loaded. Rename them to :literal:`.fits`.
* Drawing lines between two positions, and spherical coordinates, are not working yet.
* Screenshots cannot be taken in iDaVIE-p yet.
* Most settings in the desktop GUI last only for the current session.
