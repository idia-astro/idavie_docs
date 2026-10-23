.. _particle_mapping_files:

Mapping files
=============

.. note:: This page is part of the preview of iDaVIE-p, the particle side of iDaVIE. It describes features that have not been released yet and may change. See :ref:`particle_overview`.

A mapping file is a JSON file that describes how the columns of a table are mapped to the position and the appearance of the particles. Mapping files are useful to:

* keep a rendering, and restore it later;
* render several tables with the same column names in the same way;
* share a rendering with collaborators.

To save the mapping of the active dataset, click :literal:`Save Mapping File` in the RENDERING tab. To use a mapping file, click :literal:`Load Mapping File` in the LOAD tab (see :ref:`particle_load_tab`):

* **Before rendering**: click :literal:`Load Data Table` first, then :literal:`Load Mapping File`, then :literal:`Render Data`. Loading a table resets the mapping, so the mapping file must be loaded after the table. The positions are scaled to the :literal:`TargetSize` of each axis when the table is rendered.
* **On the active dataset**: the mapping file is applied immediately, including the :literal:`Scale` and :literal:`Offset` of the position axes. This is the best way to restore a mapping that was saved by iDaVIE-p.

Example
-------

The following mapping file places the particles using the :literal:`x`, :literal:`y` and :literal:`z` columns in a 5 m cube, colours them by the :literal:`mass` column with the :literal:`Viridis` colour map, and draws them as circles of the same size and opacity:

.. code-block:: json

    {
      "ColorMap": "Viridis",
      "UniformColor": false,
      "UniformOpacity": true,
      "UniformPointSize": true,
      "UniformPointShape": true,
      "Uniforms": {
        "Opacity": 0.8,
        "PointSize": 0.01,
        "PointShape": "Circle"
      },
      "Mapping": {
        "X": { "Source": "x", "TargetSize": 5 },
        "Y": { "Source": "y", "TargetSize": 5 },
        "Z": { "Source": "z", "TargetSize": 5 },
        "Cmap": { "Source": "mass", "Normalized": true }
      }
    }

Keys
----

Top-level keys
^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - **Key**
     - Description
   * - **ColorMap**
     - The colour map, e.g. :literal:`"Plasma"` or :literal:`"Viridis"`. The available colour maps are the ones listed in the RENDERING tab.
   * - **UniformColor**, **UniformOpacity**, **UniformPointSize**, **UniformPointShape**
     - :literal:`true` to give all particles the same colour, opacity, size or shape, set in :literal:`Uniforms`. :literal:`false` (the default) to map a column, set in :literal:`Mapping`.
   * - **Uniforms**
     - The uniform values (see below).
   * - **Mapping**
     - The mapping of columns to the position and appearance of the particles (see below).

Uniform values
^^^^^^^^^^^^^^

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - **Key**
     - Description
   * - **ColorString**
     - The uniform colour, as an HTML colour code such as :literal:`"#FF0000"` or :literal:`"#FF0000FF"`.
   * - **Opacity**
     - The uniform opacity, from 0 to 1. The default is 1.
   * - **PointSize**
     - The uniform size of the particles, in metres. The default is 0.1.
   * - **PointShape**
     - The uniform shape of the particles: :literal:`Halo`, :literal:`Circle`, :literal:`OutlinedCircle`, :literal:`Square`, :literal:`OutlinedSquare`, :literal:`Triangle`, :literal:`OutlinedTriangle` or :literal:`Star`.

Mapping entries
^^^^^^^^^^^^^^^

The :literal:`Mapping` object has an entry for each property that a column can be mapped to:

* :literal:`X`, :literal:`Y` and :literal:`Z`: the position of the particles. These are required.
* :literal:`Cmap`: the colour. The value is mapped to the colour map, from 0 to 1.
* :literal:`Opacity`: the opacity, from 0 to 1.
* :literal:`PointSize`: the size, in metres.
* :literal:`PointShape`: the shape. Values from 0 to 1 are spread over the eight shapes.

Each entry can have the following keys:

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - **Key**
     - Description
   * - **Source**
     - The name of the column. Column names are case-sensitive.
   * - **TargetSize**
     - For :literal:`X`, :literal:`Y` and :literal:`Z` only: the length, in metres, that the data range of the axis is scaled to when the table is rendered. If it is 0 or missing, the :literal:`Default coordinate scale (m)` in the SETTINGS tab is used (5 m by default).
   * - **Normalized**
     - :literal:`true` to rescale the column to the range 0 to 1, using its minimum and maximum, before applying the scaling. Not used for :literal:`X`, :literal:`Y` and :literal:`Z`.
   * - **ScalingType**
     - How the value is scaled: :literal:`Linear` (the default) gives :literal:`value × Scale + Offset`. :literal:`Log`, :literal:`Sqrt`, :literal:`Squared` and :literal:`Exp` apply that function to the value instead, and ignore :literal:`Scale` and :literal:`Offset`.
   * - **Scale**, **Offset**
     - The scale (default 1) and offset (default 0) of a linear mapping. For :literal:`X`, :literal:`Y` and :literal:`Z`, these are computed from :literal:`TargetSize` when the table is rendered.
   * - **Clamped**
     - :literal:`true` to clamp the scaled value to the range from :literal:`MinVal` to :literal:`MaxVal`.
   * - **MinVal**, **MaxVal**
     - The clamping range.

A property whose :literal:`Uniform...` key is :literal:`false`, but that has no entry or an unknown column, uses its uniform value.

Notes
-----

* Mapping files saved by iDaVIE-p write the colour map, shapes and other named values as numbers (e.g. :literal:`45` for :literal:`Plasma`). Both names and numbers are accepted when a file is loaded.
* Saved files also contain keys that are not described here, such as :literal:`Lat`, :literal:`Lng`, :literal:`R`, :literal:`X2`, :literal:`Y2`, :literal:`Z2`, :literal:`Spherical`, :literal:`RenderType` and :literal:`MetaMapping`. These are reserved for spherical coordinates and for drawing lines between two positions, which do not work correctly in this preview. Unknown keys are ignored.
* The filter, the selection and the null rendering settings are not part of the mapping file.
