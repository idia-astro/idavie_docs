Introduction
============
.. note:: The current version of the software is in beta testing so please be aware that issues might arise. We also appreciate your collaboration in identifying them and, if you do, please post them in the issues page on `Github <https://github.com/idia-astro/idavie_releases/issues>`_. All issues will be fixed for the first data release. 

The mission of iDaVIE-v
-----------------------
iDaVIE-v is part of the iDaVIE software suite which is under development at `IDIA <https://www.idia.ac.za>`_. The DaVIE-v application has been developed in collaboration with `INAF-OACT <https://www.oact.inaf.it>`_ . The specific goal of iDaVIE-v is to enable the interrogation of data cubes using Virtual Reality Technology. For more details about the iDaVIE software suite development and all its aspects please refere to `Jarrett et al. 2021 (in press.) <https://ui.adsabs.harvard.edu/abs/2020arXiv201210342J/abstract>`_.

Codebase and releases
---------------------
iDavIE-v is an open-source project. Its source code will be made available after the Beta testing is concluded. 

Installation guides are provided in the section :ref:`installation_configuration`, including the installation of the needed VR environment.

The release plan and major goals are the following:

* v1.0-Beta.0: complete software only in executable format (released on 18th March 2021)
* v1.0-Beta.1: fixed deployment DLL bug (released on 29th March 2021
* v1.0-Beta.2: fixed loading frequency-based cubes issue (released on 10th April 2021)
* v1.0-Beta.3: added ability to load and interact with large catalgoue (released on 7th July 2021)
* v1.0-Beta.5: added ability to export sub-cubes and edit settings using a JSON config file (released on 8th October 2021)
* v1.0-Beta.6: added ability to load new cubes without exiting iDaVIE; Updated file browser to use system-default browser; added toaster notifications for information, warnings and errors  (released 18th February 2022)
* **v1.0-Beta.7 (current release)**: fixed memory leak, fixed behaviour of edited masks when viewing downsampled cubes, added ability to paint small cubes without cropping (released 20 July 2022)
* v1.0: complete software and source code (release date TBC)

Getting help
------------
The iDaVIE team welcomes any suggestion, feature request, or bug report, to make iDaVIE-v better via 

* Recommended: `Github Issue <https://github.com/idia-astro/idavie_releases/issues>`_
* Only if necessary: `IDIA vislab help <vislab@idia.ac.za>`_ (vislab@idia.ac.za) 


Contributors
------------
The development of the iDaVIE-v project is a joint effort from:

* `The Inter-university Institute for Data Intensive Astronomy (IDIA) <https://www.idia.ac.za>`_
* `The IDIA Visualisation Lab <https://vislab.idia.ac.za>`_
* `Osservatorio Astronomico di Catania, Istituto Nazionale di Astrofisica (INAF-OACT) <https://www.oact.inaf.it>`_
* `Osservatorio Astronomico di Cagliari, Istituto Nazionale di Astrofisica (INAF-OACA) <http://www.oa-cagliari.inaf.it/>`_

Software citation
-----------------
Please use the following DOI as a citation when using iDavie-v for publications.

.. image:: https://zenodo.org/badge/DOI/10.5281/zenodo.4614116.svg
   :target: https://doi.org/10.5281/zenodo.4614116

Other relevant references are:

* "Exploring and Interrogating Astrophysical Data in Virtual Reality", `Jarrett et al. 2021 (in press.) <https://ui.adsabs.harvard.edu/abs/2020arXiv201210342J/abstract>`_
* "iDaVIE-v: immersive Data Visualisation Interactive Explorer for volumetric rendering", `Marchetti et al. 2021 (in press.) <https://ui.adsabs.harvard.edu/abs/2020arXiv201211553M/abstract>`_
* "Virtual Reality and Immersive Collaborative Environments: the New Frontier for Big Data Visualisation", `Sivitilli et al. 2021 (in press.) <https://ui.adsabs.harvard.edu/abs/2021arXiv210314397S/abstract>`_

Acknowledgements
----------------
* The Inter-University Institute for Data Intensive Astronomy is a partnership of the University of Cape Town, the University of Pretoria and the University of the Western Cape. 

* This project received support from the National Research Foundation under the Research Career Advancement and South African Research Chair Initiative programs (SARChI)

* This project received support from the Italian Ministry of Foreign Affairs and International Cooperation (MAECI Grant Number ZA18GR02) and the South African NRF (Grant Number 113121) as part of the ISARP RADIOSKY2020 Joint Research Scheme

iDaVIE-v is mainly built using the Unity game engine and with the following third-party libraries:

* SteamVR
* CFITSIO

Copyright and License
---------------------
Copyright (C) 2022 IDIA, INAF-OACT. This program is free software; you can redistribute it and/or modify it under the terms of the `GNU General Public License version 3 <http://www.gnu.org/copyleft/gpl.html>`_ as published by the Free Software Foundation.
