.. _inputs_outputs:

Input & Outputs
===============
In this section we describe what kinds of file can be ingested by iDaVIE and what files and formats are saved as data products of iDaVIE.

Inputs
------
Standard Real*4 (32-bit) FITS cubes for both the data and the (optional) mask.  There should be three axes, as defined by NAXIS1, NAXIS2, and NAXIS3 in the header. If the third visual dimension is in NAXIS4 (e.g., some ASKAP cubes), the user can choose which axis to use as the third (*z*) dimension. Multiple catalogs can also be loaded if in VOTable format.

Outputs
-------
iDaVIE provides:

* **PNG** Screenshots and moment maps exported as PNG files, stored in :literal:`Output/Camera` and :literal:`Output/MomentMaps` respectively.
* **VOTable** Catalog exported from an edited or created mask, stored in :literal:`Output/Catalogs`.

  * iDaVIE outputs the following columns:

.. list-table::
   :widths: 25 65
   :header-rows: 1

   * - **Column name**
     - **Description**
   * - :literal:`id`
     - The unique number (in this catalogue) associated with the source.
   * - :literal:`x`
     - The x-position of the source's centre.
   * - :literal:`y`
     - The y-position of the source's centre.
   * - :literal:`z`
     - The z-position of the source's centre.
   * - :literal:`x_min`
     - The lowest x-value of the source's bounds.
   * - :literal:`x_max`
     - The highest x-value of the source's bounds.
   * - :literal:`y_min`
     - The lowest y-value of the source's bounds.
   * - :literal:`y_max`
     - The highest y-value of the source's bounds.
   * - :literal:`z_min`
     - The lowest z-value of the source's bounds.
   * - :literal:`z_max`
     - The highest z-value of the source's bounds.
   * - :literal:`ra`
     - The right ascension of the source's position.
   * - :literal:`dec`
     - The declination of the source's position.
   * - :literal:`\<z-coordinate\>`
     - The physical coordinate of the z-axis (i.e. velocity, frequency, redshift, etc.).
  
       The name of the column will depend on the header of the cube.
   * - :literal:`Flag (dd/MM/yy_HH:mm)`
     - The user-defined flag attached to the source when the table is saved.
   * - :literal:`\<others\>`
     - Other columns may be included as well, depending on the type of source
       
       list being exported. For example, masked sources will have columns pertaining
       
       to the calculated mask statistics that are viewable in the :ref:`infowindow`
       
       while imported sources will include the imported columns that were selected 
       
       in the :ref:`sourcestab`.

* **log** Debug files created by iDaVIE, stored in :literal:`Output/Logs`. Used for error reporting and should be attached when reporting issues.
* **CSV** Spectral profiles calculated from masked sources in the VR :ref:`plots` can be exported as CSV files, stored in :literal:`Output/SpectralProfiles`.
* **FITS** Created or modified masks, or moment maps exported as FITS files:

  * If a mask is loaded and modified in VR then it can be saved either overwriting the original mask **or**  as a copy. In the former case the mask will be saved with the same name of the original mask and in the same directory, in the latter case the suffix :literal:`-copy.fits` will be added to the original mask name and the edited mask will be saved in the same directory as the original mask (e.g. the edited mask file name will then be :literal:`originalmaskname-copy.fits`).
  * If no mask is provided in input, but one is created in iDaVIE, then the created mask is saved in the same directory of the data cube and a suffix :literal:`-mask.fits` will be addedd to the cube name to indicate the maks file (e.g. the created mask file name will then be :literal:`originalcubename-mask.fits`).
  * Moment maps are saved to :literal:`Output/MomentMaps/Moment_map_[0/1]_yyyyMMdd_Hmmss.png`, where :literal:`yyyyMMdd_Hmmss` is the timestamp when the files are saved.
