.. _particle_inputs_outputs:

Inputs & Outputs
================

.. note:: This page is part of the preview of iDaVIE-p, the particle side of iDaVIE. It describes features that have not been released yet and may change. See :ref:`particle_overview`.

Inputs
------

iDaVIE-p loads tables in which each row is a particle and each column is a property of the particles. At least three numeric columns are needed for the positions of the particles. The following formats are supported:

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - **Format**
     - Details
   * - FITS binary table (:literal:`.fits`)
     - The recommended format. The table must be in the first extension of the file (HDU 2), which is where `Astropy <https://www.astropy.org/>`_ and most other tools write it. Text columns (:literal:`TFORM` :literal:`A`) are read as text and logical columns (:literal:`L`) as 0 or 1. All other columns are read as numbers. Units are read from the :literal:`TUNIT` keywords.
   * - CSV (:literal:`.csv`)
     - Comma-separated values, with the column names on the first line. Values may be quoted with double quotes, but a value cannot span several lines. A column is numeric if all its non-empty values are numbers, with a dot as the decimal separator. Otherwise, it is a text column.
   * - IPAC table (:literal:`.tbl`)
     - Lines starting with :literal:`\\` are skipped. The column names, types and units are read from the header lines separated with :literal:`|`. Columns of type :literal:`int`, :literal:`long`, :literal:`float`, :literal:`double` or :literal:`real` (or their first letters) are numeric. All other types are text.

.. warning:: Support for IPAC tables is incomplete in this preview, and rendering an IPAC table may fail. Please convert IPAC tables to FITS or CSV, e.g. with Astropy (see below).

.. note:: The file dialog also lists :literal:`.fit` and :literal:`.fts` files, but these cannot be loaded yet. Rename them to :literal:`.fits`.

Numbers are stored with single (32-bit) precision. Large integers, such as long object IDs, may therefore not be represented exactly. Store such columns as text if you need to filter or select by them.

Text columns
^^^^^^^^^^^^

Text columns can be used like numeric columns, e.g. to colour the particles by a category. Each distinct text value is given a number, in the order in which the values first appear in the table. In the simple layout of the RENDERING tab, text columns are marked :literal:`[string]`. The advanced layout only lists numeric columns.

Null values
^^^^^^^^^^^

The following values are treated as null:

* NaN and infinite values in numeric columns.
* Empty cells in a CSV file.
* Text values equal to the :literal:`Null string value` in the SETTINGS tab. This is empty by default, so that empty text values are null.

Integer null values defined with the :literal:`TNULL` keyword in a FITS file are not recognised yet. They are read as ordinary values.

Particles with a null value in a column that is mapped to their colour, opacity, size or shape are hidden by default. They can be drawn with a separate style instead. See :ref:`particle_settings_tab`.

Preparing data
^^^^^^^^^^^^^^

The easiest way to prepare a table for iDaVIE-p is to write it as a FITS file with `Astropy <https://www.astropy.org/>`_. The following code snippet creates a table of random particles with a position and a mass, and writes it to a FITS file and a CSV file:

.. code-block:: python

    import numpy as np
    from astropy.table import Table

    # Create a table of 10000 random particles.
    n = 10000
    particle_table = Table({
        'x': np.random.normal(0, 1, n),
        'y': np.random.normal(0, 1, n),
        'z': np.random.normal(0, 1, n),
        'mass': np.random.lognormal(0, 1, n),
    })

    # Write the table to a .fits file and to a .csv file.
    particle_table.write('particle_data.fits', format='fits')
    particle_table.write('particle_data.csv', format='csv')

An IPAC table can be converted in the same way with :literal:`Table.read('table.tbl', format='ipac')`.

Sample data
^^^^^^^^^^^

The iDaVIE-p source code includes a sample table, :literal:`Data/SampleData/test_catalog.fits`. It contains 121,280 rows with the columns :literal:`X1`, :literal:`Y1`, :literal:`Z1`, :literal:`X2`, :literal:`Y2`, :literal:`Z2` and :literal:`Weight`. Each row is the edge of a friends-of-friends group in the 2MRS survey, going from (:literal:`X1`, :literal:`Y1`, :literal:`Z1`) to (:literal:`X2`, :literal:`Y2`, :literal:`Z2`). It is used in :ref:`particle_how_to_demos`.

Outputs
-------

All output files are written to the :literal:`Outputs` folder, next to the iDaVIE-p executable. When iDaVIE-p is run from the Unity Editor, this folder is in the root folder of the Unity project.

Selected particles
^^^^^^^^^^^^^^^^^^

The selected particles of the active dataset can be exported with :literal:`Export Selection` in the SELECTION tab, :literal:`Export` in the VR Selection window, or the voice command :literal:`export selection`. The selected rows are copied, with all their columns, from the original table to a new file in :literal:`Outputs/Tables`. The file is called :literal:`iDaVIE-table_<date>_<time>`, followed by an extension that depends on the format of the original table:

.. list-table::
   :widths: 25 75
   :header-rows: 1

   * - **Original table**
     - Exported file
   * - FITS (:literal:`.fits`)
     - A FITS file with the selected rows in a binary table extension called :literal:`SELECTED`. The column names, formats and units are the same as in the original table. The exported file can be loaded in iDaVIE-p.
   * - CSV (:literal:`.csv`)
     - A CSV file with the header line and the selected lines of the original file.
   * - IPAC table (:literal:`.tbl`)
     - An IPAC table with the first two lines and the selected lines of the original file.

If the active dataset was created with :literal:`New Dataset from Selection`, the corresponding rows of the original table are exported. If no particles are selected, no file is written.

.. warning:: Exporting from an IPAC table only gives the correct rows if the table has exactly two header lines (names and types) and no lines starting with :literal:`\\`.

Datasets created from a selection are only kept in memory. Export the selection to keep it.

Mapping files
^^^^^^^^^^^^^

:literal:`Save Mapping File` in the RENDERING tab saves the mapping of the active dataset as a JSON file, in a folder of your choice. See :ref:`particle_mapping_files`.

Statistics
^^^^^^^^^^

:literal:`Copy Statistics` in the SELECTION tab copies the statistics of the selection to the clipboard as tab-separated text, which can be pasted into a spreadsheet.

Log files
^^^^^^^^^

All log messages are saved to :literal:`Outputs/Logs/i-DaVIE-v_Log.log`. When iDaVIE-p starts, the log of the previous session is kept as :literal:`i-DaVIE-v_Log_previous.log`. The log can also be saved to a file of your choice from the DEBUG tab. Please include the log file when you report a bug.
