.. _particle_gui:

Graphical User Interface
========================

.. note:: This page is part of the preview of iDaVIE-p, the particle side of iDaVIE. It describes features that have not been released yet and may change. See :ref:`particle_overview`.

Like the volume side, iDaVIE-p presents two types of GUI: the :literal:`Desktop GUI`, which the user interacts with at the computer using the mouse and keyboard, and the :literal:`VR GUI`, which the user interacts with in the VR environment using the VR controllers.

Desktop GUI
-----------
This is the GUI that appears on the computer screen when iDaVIE-p starts. It is used to load tables, set up how they are rendered, and manage selections.

The Desktop GUI is divided into two main sections:

* The **left side** holds a vertical bar of icon tabs. Hover over an icon to see its name.
* The **right side** is the main control panel, called the inspector. It has five tabs: :literal:`LOAD`, :literal:`RENDERING`, :literal:`SELECTION`, :literal:`SETTINGS` and :literal:`DEBUG`. The :literal:`Collapse ->` button under the inspector hides it, so that the VR view fills more of the screen. Click :literal:`<- Expand` to show it again.

All the controls in the inspector act on the **active dataset**, which is chosen in the :literal:`Loaded tables` tab.

.. image:: /_static/particle/desktop_overview.png
    :alt: The desktop GUI of iDaVIE-p with a rendered table
    :width: 100%

Left tab bar
^^^^^^^^^^^^

The icons on the left are, from top to bottom:

#. :literal:`VR-View`: shows the view of the VR user. iDaVIE-p switches to this tab automatically when the first dataset has been rendered.
#. :literal:`About`: shows the iDaVIE logo.
#. :literal:`Loaded tables`: the list of loaded datasets (see below). The VR view stays visible behind the list.
#. :literal:`Exit iDaVIE`: closes iDaVIE-p immediately, without asking for confirmation.

.. _particle_tables:

Loaded tables
^^^^^^^^^^^^^

.. image:: /_static/particle/tables_list.png
    :alt: The Loaded tables tab with two datasets, one of them hidden
    :width: 100%

The first row of the list is :literal:`New Table...`. Click it to deselect the active dataset. This enables the :literal:`Load Data Table` and :literal:`Render Data` buttons on the LOAD tab, so that you can load another table.

Every other row is a loaded dataset. Click a row to make that dataset the active one. Each row contains:

#. The name of the dataset. This is the file name without its extension. If a name is already in use, a number is added, e.g. :literal:`catalogue (1)`. A dataset created from a selection is called :literal:`<name> selection`.
#. An eye button to show or hide the dataset. A hidden dataset is not drawn at all, including its selected particles.
#. The :literal:`Selectable` checkbox (on by default). When it is unchecked, selecting particles in VR does not affect this dataset. This is useful when several datasets overlap.
#. A remove button (bin icon). Click it once to arm it: it turns red and reads :literal:`Remove?`. Click it again within 3 seconds to remove the dataset. If you don't, it returns to normal.

When the active dataset is removed, the next dataset in the list becomes active. If the removed dataset was created from a selection, its parent dataset becomes active again and is shown if it was hidden.

All loaded datasets are drawn at the same time, in the same frame. See :ref:`particle_multiple_datasets`.

.. _particle_load_tab:

LOAD tab
^^^^^^^^

The LOAD tab is where a table is loaded and placed in the VR space. Loading a table is a two-step process: the table is first *staged* (only its column information is read), so that you can choose the position columns, and then *rendered* (all rows are read).

.. image:: /_static/particle/load_tab.png
    :alt: The LOAD tab with a staged table
    :width: 50%

#. :literal:`Load Data Table` opens a file dialog to choose a table. The supported formats are listed in :ref:`particle_inputs_outputs`. The name of the chosen file is shown above the button. This button is disabled while a dataset is active; click :literal:`New Table...` in the :literal:`Loaded tables` tab first to load another table.
#. :literal:`Load Mapping File` opens a file dialog to choose a JSON mapping file (see :ref:`particle_mapping_files`). If a dataset is active, the mapping is applied to it immediately. Otherwise it is used when the staged table is rendered.
#. :literal:`Position Mapping`: one row for each of the :literal:`X:`, :literal:`Y:` and :literal:`Z:` axes.

   * The :literal:`Column` dropdown chooses the column used for that axis. By default, the first three numeric columns of the table are used.
   * :literal:`Initial Size (m)` is the length, in metres in the VR space, that the data range of that axis is scaled to. The default is 5 m (set in the SETTINGS tab). Press Enter to apply a new value.

   Changes to an active dataset are applied immediately.
#. :literal:`Render Data` loads all rows of the staged table and renders it. A progress bar shows the loading progress and turns green when loading has finished. The new dataset becomes the active dataset. This button is disabled while a dataset is active.

When a table is rendered, iDaVIE-p picks a starting particle size that suits the density of the data: it estimates the typical spacing between particles and sets the uniform size to 0.3 times that spacing, within the minimum and maximum point sizes set in the SETTINGS tab. This is not done if the size was set in a mapping file.

.. _particle_filter:

Filter
~~~~~~

The :literal:`Filter` section of the LOAD tab (collapsed by default) shows only the particles of the active dataset that match a set of conditions, and hides the rest.

.. image:: /_static/particle/load_filter.png
    :alt: The Filter section of the LOAD tab with one condition
    :width: 50%

* :literal:`Enable Filter` (on by default) turns the applied filter on or off. When it is off, all particles are shown. This takes effect immediately.
* :literal:`Invert Filter` hides the matching particles instead of the others. This takes effect immediately.
* :literal:`Match` chooses whether a particle must match :literal:`All` of the conditions or :literal:`Any` of them.
* To add a condition, choose a column, an operator and a value, then click :literal:`Add Condition`. To remove one, select it in the :literal:`Filter Conditions` list and click :literal:`Remove Condition`.
* Click :literal:`Apply Filter` to apply the conditions in the list. Adding or removing conditions has no effect until you do.
* :literal:`Clear Filter` removes all the conditions and shows all particles again.

Each dataset keeps its own filter. The filter is not saved in the mapping file.

.. _particle_conditions:

The same conditions are used by the filter and by :literal:`Select by condition` in the SELECTION tab:

.. list-table::
   :widths: 20 80
   :header-rows: 1

   * - **Operator**
     - Matches a particle when
   * - :literal:`=`, :literal:`!=`
     - the value is (or is not) equal to the given value. Text is compared without regard to case.
   * - :literal:`<`, :literal:`<=`, :literal:`>`, :literal:`>=`
     - the value is less than, at most, greater than or at least the given number.
   * - :literal:`between`
     - the value lies within two numbers, given separated by a comma, semicolon or space (e.g. :literal:`10, 20`). Both ends are included.
   * - :literal:`contains`
     - the value contains the given text, regardless of case.
   * - :literal:`is null`, :literal:`is not null`
     - the value is (or is not) null. The value field is ignored.

Use a dot as the decimal separator. A condition on a column that a dataset does not have never matches.

.. _particle_rendering_tab:

RENDERING tab
^^^^^^^^^^^^^

The RENDERING tab sets how the columns of the active dataset are mapped to the colour, opacity, size and shape of the particles. It has two layouts: the simple layout, described first, and an advanced layout, which is enabled with the :literal:`Advanced mapping mode` toggle in the SETTINGS tab. Changes apply to the active dataset straight away.

Simple mode
~~~~~~~~~~~

.. image:: /_static/particle/rendering_simple.png
    :alt: The RENDERING tab in simple mode, with the colour mapped to a column
    :width: 100%

The simple layout has four blocks: :literal:`Color`, :literal:`Opacity`, :literal:`Particle Size` and :literal:`Particle Shape`. The top row of each block has:

#. A source dropdown to choose the column that drives this property. Numeric columns are listed first, then text columns, marked :literal:`[string]`. Each distinct text value is treated as a category.
#. :literal:`Nulls (N)`, where N is the number of null values in the chosen column. When it is checked, particles with a null value are drawn with the null style set in the SETTINGS tab. When it is unchecked, they are hidden.
#. :literal:`Invert` reverses the direction of the mapping, e.g. so that larger values give smaller particles.
#. :literal:`Uniform` gives every particle the same value instead of mapping a column.

When :literal:`Uniform` is off, the block shows a histogram of the chosen column, with a range slider and :literal:`Min` and :literal:`Max` fields below it. Values from the minimum to the maximum are mapped to:

* :literal:`Color`: the full colour map, chosen in the dropdown below the slider. The default colour map is :literal:`Plasma`.
* :literal:`Opacity`: from fully transparent to fully opaque.
* :literal:`Particle Size`: from the minimum to the maximum point size set in the SETTINGS tab.
* :literal:`Particle Shape`: the eight shapes, in order: Halo, Circle, OutlinedCircle, Square, OutlinedSquare, Triangle, OutlinedTriangle and Star.

When you return to a column you used before, the range you set for it is restored.

When :literal:`Uniform` is on, the block shows a single control instead: a rainbow slider for the colour, a slider for the opacity (0 to 1), a slider for the size (0 is the minimum and 1 the maximum point size), or a slider to choose one of the eight shapes.

Advanced mode
~~~~~~~~~~~~~

.. image:: /_static/particle/rendering_advanced.png
    :alt: The RENDERING tab in advanced mode
    :width: 50%

The advanced layout shows the full mapping as a grid, with a column for each of :literal:`Color`, :literal:`Opacity`, :literal:`Point Size` and :literal:`Point Shape`, and a colour map dropdown above it. The rows of the grid are:

.. list-table::
   :widths: 20 80
   :header-rows: 1

   * - **Row**
     - Description
   * - :literal:`Source`
     - The numeric column that drives this property.
   * - :literal:`Uniform?`
     - Use the same value for every particle. Enables :literal:`Value` and disables the rows below it.
   * - :literal:`Value`
     - The uniform value: a named colour, an opacity from 0 to 1, a point size, or a shape.
   * - :literal:`Normalize?`
     - Rescale the column to the range 0 to 1 before applying the scale and offset.
   * - :literal:`Scale`, :literal:`Offset`
     - The value used is :literal:`column × Scale + Offset`.
   * - :literal:`Clamp?`
     - Clamp the value to the range given by :literal:`Min` and :literal:`Max`.
   * - :literal:`Min`, :literal:`Max`
     - The clamping range. Only editable when :literal:`Clamp?` is checked.

Click :literal:`Update Active Dataset Mapping` to apply the grid to the active dataset. This is needed after changing a :literal:`Source`.

Saving the mapping
~~~~~~~~~~~~~~~~~~

:literal:`Save Mapping File`, at the bottom of both layouts, saves the current mapping of the active dataset as a JSON file. Load it again with :literal:`Load Mapping File` on the LOAD tab to restore the same rendering later, or to use it for another table with the same columns. See :ref:`particle_mapping_files`.

.. _particle_selection_tab:

SELECTION tab
^^^^^^^^^^^^^

The SELECTION tab shows the selected particles of the active dataset, and has tools to change, analyse and export the selection. Particles are selected in VR (see :ref:`particle_how_to_interact`) or by condition from this tab.

.. image:: /_static/particle/selection_tab.png
    :alt: The SELECTION tab, with the selected particles highlighted in the VR view
    :width: 100%

At the top, the tab shows the name of the active dataset and the number of selected particles, e.g. :literal:`1,204 selected of 121,280 (0.99%)`. If some of the selected particles are hidden by the filter, a note in orange says how many.

The buttons below act on the selection:

* :literal:`Clear Selection` unselects all particles.
* :literal:`Invert Selection` selects the particles that are not selected, and unselects the others. Particles skipped by the selection rules (see below) are not selected.
* :literal:`Export Selection` writes the selected rows to a new table file. See :ref:`particle_inputs_outputs`.
* :literal:`New Dataset from Selection` creates a new dataset that contains only the selected particles, called :literal:`<name> selection`. It is drawn in the same way and in the same place as the original dataset, which is hidden. The new dataset becomes the active dataset, so you can filter, select and export within it. Remove it to return to the original dataset.

A status line under the buttons shows the result of the last action.

Select by condition
~~~~~~~~~~~~~~~~~~~

This section adds particles to the selection, or removes them from it, using conditions. It works like the :ref:`filter <particle_filter>`, with its own list of conditions:

* Choose :literal:`All` or :literal:`Any` under :literal:`Match`, then add conditions with :literal:`Add Condition`.
* :literal:`Add Matching` adds the particles that match the conditions to the selection. The selection rules apply.
* :literal:`Remove Matching` removes the selected particles that match the conditions from the selection.

The operators are described in the :ref:`table of conditions <particle_conditions>`.

Statistics
~~~~~~~~~~

This section shows statistics of the selected particles for the column chosen in the :literal:`Column` dropdown:

.. image:: /_static/particle/selection_stats.png
    :alt: Statistics of the selected particles in the SELECTION tab
    :width: 50%

* For a numeric column: the number of values and nulls, the mean, standard deviation, minimum, quartiles, median and maximum. A histogram compares the selected particles (white) with all particles (grey). Each is scaled to its own peak.
* For a text column: the number of values, nulls and unique values, and the 10 most frequent values with their counts.
* For a true/false column: the number of true, false and null values.

:literal:`Copy Statistics` copies the statistics to the clipboard as tab-separated text, which can be pasted into a spreadsheet.

The statistics are only computed while the SELECTION tab is showing and the :literal:`Statistics` section is open, and are updated shortly after the selection changes.

Selected particle rendering
~~~~~~~~~~~~~~~~~~~~~~~~~~~

These settings set how selected particles are drawn, in every dataset. Each property has an :literal:`Enabled?` checkbox:

* :literal:`Colour` (enabled by default): :literal:`Smart`, :literal:`Red`, :literal:`Green`, :literal:`Cyan`, :literal:`Grey` or :literal:`White`. :literal:`Smart` (the default) picks a colour that stands out against the colour map of the dataset.
* :literal:`Opacity` (enabled by default): the opacity of selected particles (default 1), and a :literal:`Frequency` that makes them blink. A frequency of 0 (the default) turns blinking off.
* :literal:`Point Size` (disabled by default): :literal:`Small`, :literal:`Medium` or :literal:`Large`.
* :literal:`Point Shape` (disabled by default): one of the eight particle shapes.

Selection rules
~~~~~~~~~~~~~~~

These rules decide which particles can be added to a selection, in VR, with :literal:`Invert Selection`, and with :literal:`Add Matching`:

* :literal:`Skip Invisible Particles` (off by default): don't select particles that are not visible, e.g. particles with zero opacity.
* :literal:`Skip Null Particles` (off by default): don't select particles that have a null value in a mapped column.
* :literal:`Skip Filtered-Out Particles` (on by default): don't select particles that the filter hides.
* :literal:`Reset Time (s)` (default 3 s): in VR, holding the selection-mode button for this long clears the selection. See :ref:`particle_how_to_interact`.

.. _particle_settings_tab:

SETTINGS tab
^^^^^^^^^^^^

.. image:: /_static/particle/settings_tab.png
    :alt: The SETTINGS tab
    :width: 50%

Null rendering
~~~~~~~~~~~~~~

A value in a table can be null, e.g. a NaN value or an empty cell (see :ref:`particle_inputs_outputs`). Particles with a null value in a mapped column are hidden by default. To show them, check :literal:`Nulls (N)` for that property in the RENDERING tab, or :literal:`Enabled?` in this section. This section sets how null values are drawn in the active dataset:

* :literal:`Null string value`: text cells equal to this string are treated as null.
* :literal:`Colour`, :literal:`Opacity` and :literal:`Point Size` of null particles, with the same options as in :ref:`selected particle rendering <particle_selection_tab>`.

Primary Controller Hand
~~~~~~~~~~~~~~~~~~~~~~~

Slide to :literal:`Left` or :literal:`Right` to choose which VR controller is the primary one. The primary controller is used to select particles. The default is :literal:`Right`. Left-handed use is not fully supported in this preview. See :ref:`particle_how_to_interact`.

Default physical mapping
~~~~~~~~~~~~~~~~~~~~~~~~

* :literal:`Default coordinate scale (m)` (default 5): the starting :literal:`Initial Size (m)` of each axis for the next table that is loaded.
* :literal:`Min point size (cm)` (default 0.1) and :literal:`Max point size (cm)` (default 20): the range of particle sizes used by the size mapping and the uniform size slider.

Advanced mapping mode
~~~~~~~~~~~~~~~~~~~~~

Switches the RENDERING tab between the simple and the advanced layouts.

.. note:: The settings on this tab, apart from the primary controller hand, last only for the current session.

DEBUG tab
^^^^^^^^^

The DEBUG tab shows the log messages of the current session. :literal:`Save log file` saves them to a file of your choice. The log is also saved automatically, see :ref:`particle_inputs_outputs`.

.. image:: /_static/particle/debug_tab.png
    :alt: The DEBUG tab
    :width: 50%

VR GUI
------

The VR GUI consists of the Quick Menu and a set of windows. Point at them with the laser of the right controller, and press the right trigger to click.

.. _particle_quickmenu:

Quick Menu
^^^^^^^^^^

Hold **Y** on the left controller to show the Quick Menu next to it. It disappears when you release the button. While you hover over a button with the laser, its name is shown at the bottom of the menu.

.. image:: /_static/particle/vr_quick_menu.png
    :alt: The VR Quick Menu
    :width: 40%

The buttons open the following windows:

#. :literal:`Data List`: the Dataset List window.
#. :literal:`Inquiry Window`: the Particle Inquiry window.
#. :literal:`Voice Commands`: the Voice Commands List window.
#. :literal:`Render Parameter Tuning`: the Render Mapping window.
#. :literal:`Colormaps`: the Color Map List window.
#. :literal:`Selection`: the Selection window.

A window opens 1.5 m in front of you.

Moving windows
^^^^^^^^^^^^^^

* To move a window, point at its title bar, press and hold the trigger, and move the controller. The window turns to face you. While you hold the trigger, push the right thumbstick up or down to push the window away or pull it closer. The Color Map List window can also be resized by pushing the thumbstick left or right.
* The Particle Inquiry and Voice Commands List windows work in the same way, with their header. Pushing the thumbstick left or right resizes them.
* To scroll a list, point at it and push the right thumbstick up or down.
* To close a window, click the square at the right end of its title bar. Open it again from the Quick Menu.

.. _particle_vr_dataset_list:

Dataset List
^^^^^^^^^^^^

.. image:: /_static/particle/vr_dataset_list.png
    :alt: The VR Dataset List window
    :width: 50%

The Dataset List window has the same functions as the :ref:`Loaded tables <particle_tables>` tab of the desktop GUI. Click the name of a dataset to make it the active dataset. Each row has:

* the :literal:`Selectable` checkbox, which sets whether the selection sphere affects this dataset;
* an eye button, which shows or hides the dataset;
* a remove button. Click it once and the row turns red and reads :literal:`Remove <name>?`. Click it again within 3 seconds to remove the dataset.

.. _particle_vr_inquiry:

Particle Inquiry
^^^^^^^^^^^^^^^^

The Particle Inquiry window lists the values of all the columns of the particle that was last looked up (see :ref:`particle_how_to_interact`). Use the arrow buttons below the list to scroll it. The reset button in the header clears the look-up.

.. image:: /_static/particle/vr_inquiry.png
    :alt: The VR Particle Inquiry window
    :width: 40%

.. _particle_vr_render_mapping:

Render Mapping
^^^^^^^^^^^^^^

The Render Mapping window, opened with :literal:`Render Parameter Tuning`, shows and changes the mapping of the active dataset in VR.

.. image:: /_static/particle/vr_render_mapping.png
    :alt: The VR Render Mapping window, showing the colour mapping
    :width: 100%

The lower part of the window is a grid. It has a column for each property that a data column can be mapped to: :literal:`X`, :literal:`Y`, :literal:`Z`, :literal:`Color`, :literal:`Opacity`, :literal:`Size` and :literal:`Shape`, and a row for each column of the table. The first row, :literal:`Uniform`, gives every particle the same value. Each cell shows:

* :literal:`(*)`: the column is mapped to this property;
* :literal:`( )`: the column can be mapped to this property. Click the cell to map it;
* :literal:`---`: the column cannot be mapped to this property. Text columns can only be mapped to :literal:`Color` and :literal:`Shape`, and :literal:`Uniform` cannot be used for the positions.

Click a property name at the top of the grid to show its mapping in the upper part of the window. Click the name of a column to show the distribution of its values.

* For a property that is mapped to a column, the upper part shows a histogram of the column, with the minimum and maximum of the range. The :literal:`Nulls (N)` and :literal:`Invert` checkboxes work as in the RENDERING tab of the desktop GUI. Click the histogram to start a range edit with both controllers (see :ref:`particle_vr_editing`).
* For a uniform property, the upper part shows a slider with the current value. Drag the slider with the trigger, or point at it and push the right thumbstick left or right.

.. _particle_vr_colormaps:

Color Map List
^^^^^^^^^^^^^^

The Color Map List window lists the available colour maps, grouped by type (sequential, diverging, cyclic, qualitative and miscellaneous), with a preview of each. Click a colour map to apply it to the active dataset.

.. image:: /_static/particle/vr_colormaps.png
    :alt: The VR Color Map List window
    :width: 35%

.. _particle_vr_selection:

Selection
^^^^^^^^^

The Selection window shows the selection of the active dataset, like the :ref:`SELECTION tab <particle_selection_tab>` of the desktop GUI: the number of selected particles, and the statistics of the selected particles for one column.

.. image:: /_static/particle/vr_selection.png
    :alt: The VR Selection window
    :width: 35%

* :literal:`Invert` selects the particles that are not selected, and unselects the others.
* :literal:`Export` writes the selected rows to a new table file. See :ref:`particle_inputs_outputs`.
* :literal:`New Dataset` creates a new dataset from the selected particles, and hides the original dataset.
* :literal:`Clear Selection` unselects all particles.
* Click the column button next to :literal:`Column` to choose the column of the statistics from a list.

Voice Commands List
^^^^^^^^^^^^^^^^^^^

The Voice Commands List window lists all voice commands. Click a command to run it. See :ref:`particle_how_to_interact`.

.. image:: /_static/particle/vr_voice_commands.png
    :alt: The VR Voice Commands List window
    :width: 40%
