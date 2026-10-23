.. _multidisciplinary:

The multidisciplinary uses of iDaVIE
====================================

iDaVIE, as a data visualisation tool for 3D volumetric data, provides profound insight for a multitude of scientific disciplines. While our focus has been on astronomical data and the included analysis tools are tailored to that domain, the visualisation on its own provides substantial benefit to other disciplines. This includes 3D models of neurological systems constructed from MRI images, 3D models of ice cores constructed from CT scans, and models of a mouse brain assembled from microscope images.

Preparing data for iDaVIE
-------------------------

Volumetric data
^^^^^^^^^^^^^^^

For volumetric data, iDaVIE natively supports the :literal:`.fits` image data format. Although we plan to expand to other formats in the future, the current best way to prepare data for iDaVIE is to convert it to :literal:`.fits` format. This can easily be done using the `Astropy <https://www.astropy.org/>`_ library in Python.

The following code snippet demonstrates how to convert a random 3D numpy array to a :literal:`.fits` file:

.. code-block:: python

    import numpy as np
    from astropy.io import fits

    # Create a random 3D numpy array.
    data = np.random.rand(100, 100, 100)

    # Write the array to a .fits file
    hdu = fits.PrimaryHDU(data)
    hdul = fits.HDUList([hdu])
    hdul.writeto('data.fits')

Particle data
^^^^^^^^^^^^^

For particle data, iDaVIE supports :literal:`.fits` binary tables, :literal:`.csv` files and IPAC :literal:`.tbl` tables. The best way to prepare particle data for iDaVIE is to convert it to a :literal:`.fits` table. This can also be done using the `Astropy <https://www.astropy.org/>`_ library in Python.

The following code snippet demonstrates how to write a sparse 3D particle table to a :literal:`.fits` file:

.. code-block:: python

    import numpy as np
    from astropy.table import Table

    # Create a table of 10000 random particles with a position and a mass.
    n = 10000
    particle_table = Table({
        'x': np.random.rand(n),
        'y': np.random.rand(n),
        'z': np.random.rand(n),
        'mass': np.random.rand(n),
    })

    # Write the table to a .fits file
    particle_table.write('particle_data.fits', format='fits')

See :ref:`particle_inputs_outputs` for more details on the supported formats.




Examples
--------

Astronomy
^^^^^^^^^

iDaVIE is primarily developed around interacting with volumetric astronomical data, examples of which can be seen in the :ref:`how_to_demos` page. However, the software can also be used to visualise sparse multidimensional data sets using its particle rendering capabilities. This is currently only available by building iDaVIE-p from source, and a preview is documented in :ref:`particle_overview`. We plan to add this functionality to the standalone iDaVIE release in the future. We feature some examples below.

All-sky Surveys
~~~~~~~~~~~~~~~

.. figure:: _static/2mrs_logo.gif
    :alt: iDaVIE used with 2MRS survey data
    :width: 60% 

Results of Friends-of-Friends (FoF) algorithm applied to the 2MRS survey. The FoF algorithm is used to identify groups of galaxies in the 2MRS data set to visualise large-scale structure of the observable universe. See `(Lambert et al. 2019) <http://ui.adsabs.harvard.edu/abs/2020MNRAS.497.2954L/abstract>`_ for more details.

Simulations
~~~~~~~~~~~
.. image:: _static/cosmo_logo.gif
    :alt: iDaVIE used with a cosmological simulation
    :width: 60% 

Single timestamp from a cosmological simulation using smoothed particle hydrodynamics (SPH) code for cosmological simulations. Local features resulting from simulated galaxy formation and gas accretion can be identified by tweaking the rendering parameters. See `(Huang et al. 2019) <https://academic.oup.com/mnras/article/484/2/2021/5288633>`_ for more background on the data used.


.. image:: _static/galaxies_logo.gif
    :alt: iDaVIE used with simulated galaxy mergers
    :width: 60% 

Single timestamp of a simulated galaxy merger. Particles can be rendered with different colours, sizes, opacities, and shapes depending on different parameters from the data set. Here particles are coloured by their origin (disk, bulge, halo, etc.) with diverging colourmaps to be reviewed in a post-merger time stamp. See `(Deg et al. 2019) <https://academic.oup.com/mnras/article/486/4/5391/5484877>`_ for more background on the data used.


Neuroscience
^^^^^^^^^^^^

.. image:: _static/mouse_logo.gif
    :alt: iDaVIE being used with confocal microscopy images
    :width: 60% 

Stacked confocal microscopy images of a mouse brain. The volume can be used to help study the brain's structure and function, including the causes of diseases such as Alzheimer's. See `(Ntsapi, C. et al. 2018) <https://www.intechopen.com/chapters/66223>`_ for more background on the data.


Medical Imaging
^^^^^^^^^^^^^^^

.. image:: _static/brain_logo.gif
    :alt: iDaVIE being used with MRI data
    :width: 60% 

MRI data of a human brain. This was loaded as a proof of concept to show how iDaVIE can be used to visualise medical imaging data. We have also discussed with the neuroscience community about potentially adapting iDaVIE to be used as a training tool for neurosurgeons to achieve spatial awareness of the brain.


Biology
^^^^^^^^^^^^

.. image:: _static/octopus_logo.gif
    :alt: iDaVIE used with octopus CT scan
    :width: 60% 

CT scan of an octopus for visualizing the complex decentralized nervous systems that make up alternative forms of intelligence. See `(Sivitilli et al. 2023) <https://www.biorxiv.org/content/10.1101/2023.07.31.551380v1.abstract>`_ for more details on the project.


Chemical Engineering
^^^^^^^^^^^^^^^^^^^^
.. image:: _static/ice_cube_logo.gif
    :alt: iDaVIE being used with ice
    :width: 60% 

Observing brine and air inclusions in a CT scan of sea ice from the Antarctic marginal ice zone. iDaVIE is being considered as an open-source visualization alternative to the proprietary software currently used in the field. See [#]_ for more details on the project.

.. [#]  Investigating Brine and Air Porosity from Sea Ice Samples from the Antarctic Marginal Ice Zone. Masters Dissertation. University of Cape Town. 2023.