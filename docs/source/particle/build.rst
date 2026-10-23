.. _particle_build:

Building iDaVIE-p from source
=============================

.. note:: This page is part of the preview of iDaVIE-p, the particle side of iDaVIE. It describes features that have not been released yet and may change. See :ref:`particle_overview`.

iDaVIE-p has no release yet, so it has to be built from source. The source code is in the `iDaVIE-particle-work <https://github.com/idia-astro/iDaVIE-particle-work>`_ repository on GitHub. This repository is currently only available to collaborators. Please contact the iDaVIE team at vislab@idia.ac.za to request access.

The steps are similar to :ref:`building the volume side <build>`, with three differences: iDaVIE-p uses a newer version of Unity, the configure script installs its own copy of vcpkg, and the source code must be cloned with Git. As for the volume side, only Windows is supported.

.. note:: The :literal:`BUILD.md` file in the repository still lists Unity 2021.3. Use the Unity version given on this page, which is the one in :literal:`ProjectSettings/ProjectVersion.txt`.

Prerequisites
-------------

1. Install Unity

  - Download `Unity Hub for Windows <https://public-cdn.cloud.unity3d.com/hub/prod/UnityHubSetup.exe>`_ from Unity's website and install it.
  - From the Unity Hub, install Unity version ``6000.3.17f1`` (Unity 6.3).
  - Make note of where the Unity Editor executable is installed. By default, this is ``C:\Program Files\Unity\Hub\Editor\6000.3.17f1\Editor\Unity.exe``.

2. Install Visual Studio, or the Visual Studio Build Tools, with the ``Desktop development with C++`` workload. See :ref:`build` for screenshots of this step.

3. Install `CMake <https://cmake.org/download/>`_, version 3.24 or newer. Check that it is installed by running ``cmake --version`` in a terminal.

4. Install `Git <https://git-scm.com/downloads>`_. Check that it is installed by running ``git --version`` in a terminal.

There is no need to install vcpkg: the configure script fetches it.

Building iDaVIE-p
-----------------

1. Clone the repository with Git. Downloading the source code as a ZIP file does not work, because the configure script needs Git to fetch vcpkg. These pages describe the ``alex/selection_tab`` branch:

  ::

     git clone https://github.com/idia-astro/iDaVIE-particle-work.git
     cd iDaVIE-particle-work
     git checkout alex/selection_tab

2. With the Unity Editor closed, run the configure script in PowerShell from the root folder of the repository, with the path to the Unity Editor executable:

  ::

     .\Configure.ps1 "C:\Program Files\Unity\Hub\Editor\6000.3.17f1\Editor\Unity.exe"

  The script:

  - fetches vcpkg as a Git submodule, and uses it to build the libraries that the native plugin needs (cfitsio, cminpack and starlink-ast);
  - builds the native plugin and copies it, with its libraries, to ``Assets/Plugins``;
  - downloads and imports the Unity packages that iDaVIE-p needs: TextMeshPro, the SteamVR plugin, NuGetForUnity, a file browser and a recyclable scroll view.

  The first run builds the libraries from source, which takes several minutes. Later runs reuse them. The output of each package import is written to ``import0.log`` to ``import4.log`` in the root folder.

  To rebuild only the native plugin, e.g. after it was changed, run ``.\Configure.ps1 -NativePluginsOnly``. The Unity path is not needed in that case.

3. Open the project folder in the Unity Hub, with Unity ``6000.3.17f1``.

4. In the Unity Editor, open ``Window → SteamVR Input`` and click ``Save and generate``.

5. Open ``Edit → Project Settings → XR Plug-in Management`` and check that ``OpenVR Loader`` is selected.

6. Open ``File → Build Profiles``. The list of scenes should contain only ``Assets/Scenes/ui_particles``. Click ``Build`` and choose an empty folder for the executable.

To run iDaVIE-p from the Unity Editor instead, open the scene ``Assets/Scenes/ui_particles`` and click Play. In that case, output files are written to the ``Outputs`` folder in the root folder of the project.

The configuration file, ``config.json``, is created next to the executable, or in the root folder of the project when running from the Unity Editor. See :ref:`installation_configuration`.

For the recommended development environment and the merging procedure, see :ref:`develop`.

Troubleshooting
---------------

- **The configure script fails to find Git, or fails while fetching vcpkg**: check that Git is installed and on your ``PATH``, and that you cloned the repository with Git.
- **The configure script fails with an error about** ``--fresh``: your version of CMake is too old. Install CMake 3.24 or newer.
- **Run the script from the root folder of the repository.** It uses relative paths.
