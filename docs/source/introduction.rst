Introduction
============
.. note:: The software is in active development, and while all precautions are taken to ensure as smooth an experience as possible, some issues might still occur. We would appreciate a bug report. Please see :ref:`contribution` for more detail. 

iDaVIE is a data visualisation tool for exploring 3D data in virtual reality. It has two sides:

* **iDaVIE-v** (volume) is for 3D volumetric data, with analysis tools aimed at astronomical data in particular (e.g. spectral line data cube analysis, such as HI or CO data cubes). It renders 3D volumetric data as a cube within VR space. See the *iDaVIE Volume* section, starting with :ref:`inputs_outputs`.
* **iDaVIE-p** (particle) is for sparse, multiparameter point data, such as galaxy catalogues or particle simulations. It renders each row of a table as a particle in VR space, and maps the table's columns to the position, colour, opacity, size and shape of the particles. iDaVIE-p is currently a preview. See the *iDaVIE Particle* section, starting with :ref:`particle_overview`.

Both sides share the same VR environment, controllers and voice commands. This provides profound insight for a multitude of scientific disciplines. While our focus has been on astronomical data and the included analysis tools are tailored to that domain, the visualisation on its own provides substantial benefit to other disciplines. This includes 3D models of neurological systems constructed from MRI images and 3D models of ice cores constructed from microscope images. See :ref:`multidisciplinary` for showcase videos of iDaVIE in use.

The mission of iDaVIE
-----------------------
iDaVIE is under development at `IDIA <https://www.idia.ac.za>`_. The iDaVIE application has been developed in collaboration with `INAF-OACT <https://www.oact.inaf.it/en/>`_ . The specific goal of iDaVIE is to enable the interrogation of 3D data using virtual reality technology. For more details about the iDaVIE software suite development and all its aspects, please refer to `Jarrett et al. 2021 <https://ui.adsabs.harvard.edu/abs/2020arXiv201210342J/abstract>`_.

Codebase and releases
---------------------
iDavIE is an open-source project. Its source code is available on the project's GitHub `repository <https://github.com/idia-astro/iDaVIE/>`_. 

Installation guides are provided in the section :ref:`installation_configuration`, including the installation of the required VR environment.

If you want to build iDaVIE from source, please see :ref:`build`.

iDaVIE-p is developed in a separate repository that is currently only available to collaborators, and has no release yet. See :ref:`particle_build` to build it from source.

Getting help
------------
iDaVIE hosts a `discussion forum <https://github.com/idia-astro/iDaVIE/discussions>`_ on the GitHub repository, which is a good way to get in touch with other users of iDaVIE. We encourage users to ask questions and answer others in our community. Tutorials for basic movement and the use of the analysis tools included can be found at :ref:`how_to_demos` (volume) and :ref:`particle_how_to_demos` (particle).
The iDaVIE team welcomes any suggestion, feature request, or bug report to make iDaVIE better via:

* Recommended: `GitHub Issues <https://github.com/idia-astro/iDaVIE/issues>`_
* Only if necessary: `IDIA vislab help <vislab@idia.ac.za>`_ (vislab@idia.ac.za)

See :ref:`about` for more information.
