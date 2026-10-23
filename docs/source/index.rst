.. iDavie-v documentation master file, created by
   sphinx-quickstart on Wed Mar  3 15:06:57 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

iDaVIE: immersive Data Visualisation Interactive Explorer
=====================================================================================

.. note:: This is a **preview** of the iDaVIE documentation that includes the particle side of iDaVIE (iDaVIE-p), which has not been released yet. For the documentation of the current release, please see the `latest version <https://idavie.readthedocs.io/en/latest/>`_.

iDaVIE lets you explore 3D data in virtual reality. It has two sides that share the same VR environment, controllers and voice commands:

* **Volume** (iDaVIE-v) renders volumetric data, such as FITS data cubes, as a cube in VR space. See :ref:`inputs_outputs` to get started.
* **Particle** (iDaVIE-p) renders tables of points, such as catalogues or simulation snapshots, as a cloud of particles. See :ref:`particle_overview` to get started.

.. index:: Table of Contents


.. toctree::
   :maxdepth: 3
   :caption: Getting started

   introduction.rst
   requirements.rst
   installation_and_configuration.rst

.. toctree::
   :maxdepth: 3
   :caption: iDaVIE Volume

   volume/inputs_outputs.rst
   volume/gui.rst
   volume/how_to_interact.rst
   volume/how_to_demos.rst
   volume/videoMaker.rst
   volume/idvs_ref.rst
   volume/build.rst

.. toctree::
   :maxdepth: 3
   :caption: iDaVIE Particle (preview)

   particle/overview.rst
   particle/inputs_outputs.rst
   particle/mapping_files.rst
   particle/gui.rst
   particle/how_to_interact.rst
   particle/how_to_demos.rst
   particle/build.rst

.. toctree::
   :maxdepth: 3
   :caption: Community and development

   contribute.rst
   develop.rst
   future.rst
   about.rst
   multidisciplinary.rst
