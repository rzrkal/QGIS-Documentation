|updatedisclaimer|

.. index:: Attribute table
.. _sec_attribute_table:

**********************************
 Working with the Attribute Table
**********************************

The attribute table displays information on features of a selected layer. Each
row in the table represents a feature (with geometry or not), and each column
contains a particular piece of information about the feature.
Features in the table can be searched, selected, moved or even edited.

.. only:: html

   .. contents::
      :local:

.. index:: Non Spatial Attribute Tables, Geometryless Data
.. _non_spatial_attribute_tables:

Non spatial tables
==================

QGIS allows you to load spatial and non-spatial layers. This currently includes
tables supported by OGR and delimited text, as well as the PostgreSQL, MSSQL,
SpatiaLite, DB2 and Oracle provider. When loaded in QGIS, they are listed in
the :guilabel:`Layers Panel`. Whether the layer you are working with is
spatially enabled or not doesn't change features you can have access to,
except map canvas interaction.

Non spatial tables can be used for field lookups or just generally browsed and
edited using the table view. 
As an example, you can use columns of the non-spatial table to define attribute
values, or a range of values that are allowed, to be added to a specific vector
layer during digitizing. Have a closer look at the edit widget in section
:ref:`vector_attributes_menu` to find out more.

.. _attribute_table_overview:

Manipulate the Attribute table interface
=========================================

Dialog overview
----------------

To open the attribute table for a vector layer, make the layer active by
clicking on it in the :ref:`label_legend`. Then, from the main
:menuselection:`Layer` menu, choose |openTable| :menuselection:`Open Attribute
Table`. It is also possible to right-click on the layer and choose
|openTable| :menuselection:`Open Attribute Table` from the drop-down menu,
or to click on the |openTable| :guilabel:`Open Attribute Table` button
in the Attributes toolbar.

This will open a new window that displays the feature attributes for the
layer (figure_attributes_table_). According to the setting in
:menuselection:`Settings --> Options --> Data sources` menu, the attribute table
will open in a docked window or not. The total number of features in the layer
and the number of currently selected/filtered features are shown in the
attribute table title as well as if the layer is spatially limited.


.. _figure_attributes_table:

.. figure:: /static/user_manual/working_with_vector/vectorAttributeTable.png
   :align: center

   Attribute Table for regions layer

The buttons at the top of the attribute table window provide the
following functionality:

.. _table_attribute_1:

+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| Icon                    | Label                               | Purpose                                    | Default Shortcut    |
+=========================+=====================================+============================================+=====================+
| |toggleEditing|         | Toggle editing mode                 | Enable editing functionalities             | :kbd:`Ctrl+E`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |multiEdit|             | Toggle multi edit mode              | Update multiple fields of many features    |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |saveEdits|             | Save Edits                          | Save current modifications                 | :kbd:`Ctrl+S`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |draw|                  | Reload the table                    |                                            |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |newTableRow|           | Add feature                         | Add new geometryless feature               |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |deleteSelected|        | Delete selected features            | Remove selected features from the layer    |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |expressionSelect|      | Select features using an Expression |                                            |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |selectAll|             | Select All                          | Select all features in the layer           | :kbd:`Ctrl+A`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |invertSelection|       | Invert selection                    | Invert the current selection in the layer  | :kbd:`Ctrl+R`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |deselectAll|           | Deselect all                        | Deselect all features in the current layer | :kbd:`Ctrl+Shift+A` |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |filterMap|             | Filter/Select features using form   |                                            | :kbd:`Ctrl+F`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |selectedToTop|         | Move selected to top                | Move selected rows to the top of the table |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |panToSelected|         | Pan map to the selected rows        |                                            | :kbd:`Ctrl+P`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |zoomToSelected|        | Zoom map to the selected rows       |                                            | :kbd:`Ctrl+J`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |copySelected|          | Copy selected rows to clipboard     |                                            | :kbd:`Ctrl+C`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |editPaste|             | Paste features from clipboard       | Insert new features from copied ones       | :kbd:`Ctrl+V`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |newAttribute|          | New field                           | Add a new field to the data source         | :kbd:`Ctrl+W`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |deleteAttribute|       | Delete field                        | Remove a field from the data source        | :kbd:`Ctrl+L`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |calculateField|        | Open field calculator               | Update field for many features in a row    | :kbd:`Ctrl+I`       |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+
| |conditionalFormatting| | Conditional formatting              | Enable table formatting                    |                     |
+-------------------------+-------------------------------------+--------------------------------------------+---------------------+

Table Attribute 1: Available Tools

.. note:: Depending on the format of the data and the OGR library built with
   your QGIS version, some tools may not be available.

Below these buttons is the Quick Field Calculation bar (enabled only in
:ref:`edit mode <sec_edit_existing_layer>`), which allows to quickly apply
calculations to all or part of the features in the layer. This bar uses the same
:ref:`expressions <vector_expressions>` as the |calculateField| :sup:`Field
Calculator` (see :ref:`calculate_fields_values`).

Table view vs Form view
-----------------------

QGIS provides two view modes to easily manipulate data in the attribute table:

* the |openTable| Table view, displaying values of multiple features in a
  tabular mode, each row representing a feature and each column a field;
* and the |formView| Form view which shows identifiers of features in a first
  panel and displays only the attributes of the clicked identifier in the second
  one. Form view uses the layer fields configuration
  (see :ref:`vector_attributes_menu`).
  
You can switch from one mode to the other by clicking the convenient icon at the
bottom right of the dialog.

You can also specify the :guilabel:`Default view` mode at the opening of the
attribute table in :menuselection:`Settings --> Options --> Data Sources` menu.
It can be 'Remember last view', 'Table view' or 'Form view'.

.. _figure_attribute_table_views:

.. figure:: /static/user_manual/working_with_vector/attribute_table_views.png
   :align: center

   Attribute table in form view (top) vs table view (bottom)


.. index:: Sort columns, Add actions
   pair: Attributes; Columns

Configure the columns
----------------------

Right-click in a column header when in table view to have access to tools that
help you configure what can be displayed in the attribute table and how.

Hide, organize columns and enable actions
.........................................

By right-clicking in a column header, you can choose to hide it from the
attribute table. To change several columns behavior at once, unhide a column or
change the order of the columns, choose :guilabel:`Organize columns ...`.
In the new dialog, you can:

* check/uncheck columns you want to show or hide
* drag-and-drop items to reorder the columns in the attribute table. Note that
  this change is for the table rendering and does not alter the fields order in
  the layer datasource
* enable a new virtual :guilabel:`Actions` column that displays in each row a
  drop-down box or button list of actions for each row, see :ref:`actions_menu`
  for more information about actions.

Resize columns width
.....................

Columns width can be set through a right-click on the column header and
select either:

* :guilabel:`Set width...` to enter the desired value. By default, the current
  value is displayed in the widget
* :guilabel:`Autosize` to resize at the best fit the column.

It can also be changed by dragging the boundary on the right of the column
heading. The new size of the column is maintained for the layer, and restored at
the next opening of the attribute table.

Sort columns
.............

The table can be sorted by any column, by clicking on the column header. A
small arrow indicates the sort order (downward pointing means descending
values from the top row down, upward pointing means ascending values from
the top row down).
You can also choose to sort the rows with the :guilabel:`sort` option of the
column header context menu and write an expression, e.g. to sort the row
using multiple columns you can write ``concat(col0, col1)``.

In form view, features identifier can be sorted using the |sort| :guilabel:`Sort
by preview expression` option.

.. index:: Conditional formatting
.. _conditional_formatting:

Conditional formatting of Table Cells
--------------------------------------

The conditional formatting settings can be used to highlight in the attribute
table features you may want to put a particular focus on, using custom
conditions on feature's:

* geometry (e.g., identifying multi-parts features, small area ones or in a
  defined map extent...);
* or field value (e.g., comparing values to a threshold, identifying empty
  cells...)

You can enable the conditional formatting panel clicking on
|conditionalFormatting| at the top right of the attributes window in table
view (not available in form view).

The new panel allows user to add new rules to format rendering of
|radioButtonOn|:guilabel:`Field` or |radioButtonOff|:guilabel:`Full row`.
Adding new rule opens a form to define:

* the name of the rule;
* a condition using any of the :ref:`expression builder <vector_expressions>`
  functions;
* the formatting: it can be choosen from a list of predefined formats or created
  based on properties like:

  * background and text colors;
  * use of icon;
  * bold, italic, underline, or strikeout;
  * font.

.. _figure_conditional_format:

.. figure:: /static/user_manual/working_with_vector/attribute_table_conditional_formating.png
   :align: center

   Conditional Formatting of an attribute table

.. index::
   pair: Attributes; Selection

Interacting with features in an attribute table
===============================================

Selecting features
------------------

In table view, each row in the attribute table displays the attributes of a
unique feature in the layer. Selecting a row selects the feature and likewise,
selecting a feature in the map canvas (in case of geometry enabled layer)
selects the row in the attribute table. If the set of features selected in the
map canvas (or attribute table) is changed, then the selection is also updated
in the attribute table (or map canvas) accordingly.

Rows can be selected by clicking on the row number on the left side of the
row. **Multiple rows** can be marked by holding the :kbd:`Ctrl` key.
A **continuous selection** can be made by holding the :kbd:`Shift` key and
clicking on several row headers on the left side of the rows. All rows
between the current cursor position and the clicked row are selected.
Moving the cursor position in the attribute table, by clicking a cell in the
table, does not change the row selection. Changing the selection in the main
canvas does not move the cursor position in the attribute table.

In form view of the attribute table, features are by default identified in the
left panel by the value of their displayed field (see :ref:`maptips`). This
identifier can be replaced using the drop-down list at the top of the panel,
either by selecting an existing field or using a custom expression. You can
also choose to sort the list of features from the drop-down menu.

Click a value in the left panel to display the feature's attributes in the
right one. To select a feature, you need to click inside the square symbol at
the left of the identifier. By default, the symbol turns into yellow. Like in
the table view, you can perform multiple feature selection using the keyboard
combinations previously exposed.

.. actually, it looks like there's a difference in keyboard usage but i feel
   it's a bug. Report at https://issues.qgis.org/issues/16553.

Beyond selecting features with the mouse, you can perform automatic selection
based on feature's attribute using tools available in the attribute table
toolbar, such as (see section :ref:`automatic_selection` and following one for
more information and use case):

* |expressionSelect| :guilabel:`Select By Expression...`
* |formSelect| :guilabel:`Select Features By Value...`
* |deselectAll| :guilabel:`Deselect Features from All Layers`
* |selectAll| :guilabel:`Select All Features`
* |invertSelection| :guilabel:`Invert Feature Selection`.

It is also possible to select features using the :ref:`filter_select_form`.


.. _filter_features:

Filtering features
------------------

Once you have selected features in the attribute table, you may want to display
only these records in the table. This can be easily done using the
:guilabel:`Show Selected Features` item from the drop-down list at the bottom
left of the attribute table dialog. This list offers the following filters:

* :guilabel:`Show All Features`
* :guilabel:`Show Selected Features`
* :guilabel:`Show Features visible on map`
* :guilabel:`Show Edited and New Features`
* :guilabel:`Field Filter` - allows the user to filter based on value of a field:
  choose a column from a list, type a value and press :kbd:`Enter` to filter.
  Then, only the matching features are shown in the attribute table.
* :guilabel:`Advanced filter (Expression)` - Opens the expression builder
  dialog. Within it, you can create complex expressions to match table rows.
  For example, you can filter the table using more than one field.
  See :ref:`vector_expressions` for more information.

It is also possible to filter features using the :ref:`filter_select_form`.

.. note::
  
  Filtering records out of the attribute table does not filter features out
  of the layer; they are simply momentaneously hidden from the table and can be
  accessed from the map canvas or by removing the filter. For filters that do
  hide features from the layer, use the
  :ref:`Query Builder <vector_query_builder>`.

.. tip:: **Update datasource filtering with** ``Show Features Visible on Map`` 

  When for performance reasons, features shown in attribute table are spatially
  limited to the canvas extent at its opening (see :ref:`Data Source Options
  <tip_table_filtering>` for a how-to), selecting :guilabel:`Show Features
  Visible on Map` on a new canvas extent updates the spatial restriction.



.. _filter_select_form:

Filter/Select features using form
---------------------------------

Clicking the |filterMap| :sup:`Filter/Select features using form` or
pressing :kbd:`Ctrl+F` the attribute table dialog will switch to form view
and all widgets are replaced with their search variant.

From this point onwards, this tool functionality is similar to the one described
in the :ref:`select_by_value`, where you can find descriptions of all operators
and selecting modes.

Moreover, in the attribute table case, there is also a :guilabel:`Filter
features` button that allows filtering features instead of selecting them (by
creating an Advanced Filter (Expression) for the user).

.. _figure_filter_select_form:

.. figure:: /static/user_manual/working_with_vector/tableFilteredForm.png
    :align: center

    Attribute table filtered by the filter form

If there are already filtered features, you can refine the filter using the
drop-down list next to the :guilabel:`Filter features` button. The options are:

* :guilabel:`Filter within ("AND")`
* :guilabel:`Extend filter ("OR")`

To clear the filter, either select :guilabel:`Show all features` option
mentioned in :ref:`filter_features`, or click the clear the expression and
click **[Apply]**.

Action on features
==================

Users have several possibilities to manipulate feature with the contextual menu
like:

* Select all (:kbd:`Ctrl+A`) the features
* Copy the content of a cell in the clipboard with :guilabel:`Copy cell content`.
* :guilabel:`Zoom to feature` without having to select it beforehand
* Open form. It toggles attribute table into form view with a focus on the
  clicked feature

.. _figure_copy_cell:

.. figure:: /static/user_manual/working_with_vector/copyCellContent.png
    :align: center

    Copy cell content button

If you want to use attribute data in external programs (such as Excel,
LibreOffice, QGIS or a custom web application), select one or more row(s) and
use the |copySelected| :sup:`Copy selected rows to clipboard` button or press
:kbd:`Ctrl+C`.

.. _geometry_format:

In :menuselection:`Settings --> Options --> Data Sources` menu you can
define the format to paste to with :guilabel:`Copy features as` dropdown
list:

* Plain text, no geometry,
* Plain text, WKT geometry,
* GeoJSON

You can also display a list of actions in this contextual menu. This is enabled
in the :menuselection:`Layer properties --> Actions` tab.
See :ref:`actions_menu` for more information on actions.

Save selected features as new layer
------------------------------------

The selected features can be saved as any OGR-supported vector format and
also transformed into another coordinate reference system (CRS). In the
contextual menu of the layer, from the :guilabel:`Layers Panel`, click on
:menuselection:`Save as` to define the name of the output file, its format
and CRS (see section :ref:`general_saveas`). To save the selection ensure
that the |checkbox| :menuselection:`Save only selected features` is selected.
It is also possible to specify OGR creation options within the dialog.

.. index:: Field Calculator, Derived Fields, Virtual Fields, Fields edit
.. _calculate_fields_values:

Editing attribute values
=========================

Editing attribute values can be done by:

* typing the new value directly in the cell, whether the attribute table is in
  table or form view. Changes are hence done cell by cell, feature by feature;
* using the :ref:`field calculator <vector_field_calculator>`: update in a row
  a field that may already exist or to be created but for multiple features; it
  can be used to create virtual fields.
* using the quick field :ref:`calculation bar <quick_field_calculation_bar>`:
  same as above but for only existing field
* or using the :ref:`multi edit <multi_edit_fields>` mode: update in a row
  multiple fields for multiple features.

.. _vector_field_calculator:

Field Calculator
----------------

The |calculateField| :sup:`Field Calculator` button in the attribute table
allows you to perform calculations on the basis of existing attribute values or
defined functions, for instance, to calculate length or area of geometry
features. The results can be written to a new attribute field, a virtual field,
or they can be used to update values in an existing field.

The field calculator is available on any layer that supports edit.
When you click on the field calculator icon the dialog opens (see
figure_field_calculator_). If the layer is not in edit mode, a warning is
displayed and using the field calculator will cause the layer to be put in
edit mode before the calculation is made.

Based on the :ref:`Expression Builder <functions_list>` dialog, the field
calculator dialog offers a complete interface to define an expression and apply
it to an existing or a newly created field.
To use the field calculator dialog, you first must select whether you want to
only update selected features, create a new attribute field where the results
of the calculation will be added or update an existing field.

.. _figure_field_calculator:

.. figure:: /static/user_manual/working_with_vector/fieldcalculator.png
   :align: center

   Field Calculator

If you choose to add a new field, you need to enter a field name, a field type
(integer, real, date or string) and if needed, the total field length and the
field precision. For example, if you choose a field length of 10 and a field
precision of 3, it means you have 6 digits before the dot, then the dot and
another 3 digits for the precision.

A short example illustrates how field calculator works when using the
:guilabel:`Expression` tab. We want to calculate the length in km of the
``railroads`` layer from the QGIS sample dataset:

#. Load the shapefile :file:`railroads.shp` in QGIS and press |openTable|
   :sup:`Open Attribute Table`.
#. Click on |toggleEditing| :sup:`Toggle editing mode` and open the
   |calculateField| :sup:`Field Calculator` dialog.
#. Select the |checkbox| :guilabel:`Create a new field` checkbox to save the
   calculations into a new field.
#. Add ``length`` as Output field name and ``real`` as Output field type, and
   define Output field length to be 10 and Precision, 3.
#. Now double click on function ``$length`` in the :guilabel:`Geometry` group
   to add it into the Field calculator expression box.
#. Complete the expression by typing ``/ 1000`` in the Field calculator
   expression box and click **[Ok]**.
#. You can now find a new field ``length`` in the attribute table.

.. _virtual_field:

Create a Virtual Field
-----------------------

A virtual field is a field based on an expression calculated on the fly, meaning
that its value is automatically updated as soon as the underlying parameter
changes. The expression is set once; you no longer need to recalculate the field
each time underlying values change.
For example, you may want to use a virtual field if you need area to be evaluated
as you digitize features or to automatically calculate a duration between dates
that may change (e.g., using ``now()`` function).

.. note:: **Use of Virtual Fields**

   * Virtual fields are not permanent in the layer attributes, meaning that
     they're only saved and available in the project file they've been created.
   * A field can be set virtual only at its creation and the expression used
     can't be changed later: you'll need to delete and recreate that field.

.. _quick_field_calculation_bar:

The Quick Field Calculation Bar
-------------------------------

While Field calculator is always available, the quick field calculation bar on
top of the attribute table is only visible if the layer is in edit mode. Thanks
to the expression engine, it offers a quicker access to edit an already existing
field.

In quick field calculation bar, you simply need to:

* select the existing field name in the drop-down list
* fill the textbox with an expression you directly write or build using the
  |expression| expression button
* and click on **[Update All]**, **[Update Selected]** or **[Update Filtered]**
  button according to your need.

.. index:: Multi edit
.. _multi_edit_fields:

Edit multiple fields
---------------------

Unlike the previous tools, multi edit mode allows multiple attributes of
different features to be edited simultaneously. When the layer is toggled to
edit, multi edit capabilities are accessible:

* using the |multiEdit| :sup:`Toggle multi edit mode` button from the toolbar
  inside the attribute table dialog,
* or selecting :menuselection:`Edit -->` |multiEdit| :menuselection:`Modify
  attributes of selected features` menu.

In order to edit multiple fields in a row: 

#. select the features you want to edit;
#. from the attribute table toolbar, click the |multiEdit| button. This will
   toggle the dialog to its form view. Feature selection could also be made
   at this step;
#. at the right side of the attribute table, fields (and values) of selected
   features are shown. New widgets appear next to each field allowing for
   display of the current multi edit state:

   * |multiEditMixedValues| the field contains different values for selected
     features. It's shown empty and each feature will keep its original value.
     You can reset the value of the field from the drop-down list of the widget.
   * |multiEditSameValues| all selected features have the same value for this
     field and the value displayed in the form will be kept. 
   * |multiEditChangedValues| the field has been edited and the entered value
     will be applied to all the selected features. A message appears at the top
     of the dialog, inviting you to either apply or reset your modification.

   Clicking any of these widgets allows you to either set the current value for
   the field or reset to original value, meaning that you can roll back changes
   on a field-by-field basis. 

#. make the changes to the fields you want and click on **Apply changes** in
   the upper message text or any other feature in the left panel.

Changes will apply to **all selected features**. If no feature is selected, the
whole table is updated with your changes. Modifications are made as a single
edit command. So pressing |undo| :sup:`Undo` will rollback the attribute
changes for all selected features at once.

.. note::

 Unlike the tool from the attribute table, hitting the :menuselection:`Edit
 --> Modify Attributes of Selected Features` option provides you with a modal
 dialog to fill attributes changes. Hence, features selection is required
 before execution.
 
.. _figure_field_multiedit:

.. figure:: /static/user_manual/working_with_vector/attribute_multiedit.png
   :align: center

   Editing fields of multiple features

.. note:: 

  Multi edit mode is only available for auto generated and drag and drop forms
  (see :ref:`customize_form`); it is not supported by custom ui forms.


.. index:: Relations, Foreign key
.. _vector_relations:

Creating one or many to many relations
======================================

Relations are a technique often used in databases. The concept is that
features (rows) of different layers (tables) can belong to each other.

.. _one_to_many_relation:

1-N relation
------------

As an example you have a layer with all regions of alaska (polygon)
which provides some attributes about its name and region type and a
unique id (which acts as primary key).

Then you get another point layer or table with information about airports
that are located in the regions and you also want to keep track of these. If
you want to add them to the regions layer, you need to create a one to many
relation using foreign keys, because there are several airports in most regions.

.. _figure_relations_map:

.. figure:: /static/user_manual/working_with_vector/relations1.png
   :align: center

   Alaska region with airports

Layers
......

QGIS makes no difference between a table and a vector layer. Basically, a vector
layer is a table with a geometry. So you can add your table as a vector layer.
To demonstrate the 1-n relation, you can load the :file:`regions` shapefile and
the :file:`airports` shapefile which has a foreign key field (``fk_region``) to
the layer regions. This means, that each airport belongs to exactly one region
while each region can have any number of airports (a typical one to many
relation).

Foreign keys
............

In addition to the already existing attributes in the airports attribute table,
you'll need another field ``fk_region`` which acts as a foreign key (if you have
a database, you will probably want to define a constraint on it).

This field fk_region will always contain an id of a region. It can be seen like
a pointer to the region it belongs to. And you can design a custom edit form
for editing and QGIS takes care of the setup. It works with different
providers (so you can also use it with shape and csv files) and all you have
to do is to tell QGIS the relations between your tables.

Definition (Relation Manager)
.............................

The first thing we are going to do is to let QGIS know about the relations
between the layers. This is done in :menuselection:`Project --> Project Properties...`.
Open the :guilabel:`Relations` tab and click on **[Add Relation]**.

* **name** is going to be used as a title. It should be a human readable string,
  describing, what the relation is used for. We will just call say **Airports**
  in this case.
* **referencing layer** also considered as child layer, is the one with the
  foreign key field on it. In our case, this is the ``airports`` layer
* **referencing field** will say, which field points to the other layer so this
  is ``fk_region`` in this case
* **referenced layer** also considered as parent layer, is the one with the
  primary key, pointed to, so here it is the ``regions`` layer
* **referenced field** is the primary key of the referenced layer so it is ``ID``
* **id** will be used for internal purposes and has to be unique. You may need
  it to build :ref:`custom forms <customize_form>`. If
  you leave it empty, one will be generated for you but you can assign one
  yourself to get one that is easier to handle.

.. _figure_relations_manager:

.. figure:: /static/user_manual/working_with_vector/relations2.png
   :align: center

   Relation Manager

.. index:: Feature form, Linked forms, Embedded form

Forms
.....

Now that QGIS knows about the relation, it will be used to improve the
forms it generates. As we did not change the default form method (autogenerated)
it will just add a new widget in our form. So let's select the layer region in
the legend and use the identify tool. Depending on your settings, the form might
open directly or you will have to choose to open it in the identification dialog
under actions.

.. _figure_embedded_form:

.. figure:: /static/user_manual/working_with_vector/relations3.png
   :align: center

   Identification dialog regions with relation to airports

As you can see, the airports assigned to this particular region are all shown in
a table. And there are also some buttons available. Let's review them shortly

* The |toggleEditing| button is for toggling the edit mode. Be aware that it
  toggles the edit mode of the airport layer, although we are in the feature
  form of a feature from the region layer. But the table is representing
  features of the airport layer.
* The |signPlus| button will add a new feature to the airport layer. And it will
  assign the new airport to the current region by default.
* The |remove| button will delete the selected airport permanently.
* The |link| symbol will open a new dialog where you can select any existing
  airport which will then be assigned to the current region. This may be handy
  if you created the airport on the wrong region by accident.
* The |unlink| symbol will unlink the selected airport from the current region,
  leaving them unassigned (the foreign key is set to NULL) effectively.
* The two buttons to the right switch between table view and form view where
  the later let's you view all the airports in their respective form.

If you work on the airport table, a new widget type is available which lets you
embed the feature form of the referenced region on the feature form of the
airports. It can be used when you open the layer properties of the airports
table, switch to the :menuselection:`Fields` menu and change the widget type of
the foreign key field 'fk_region' to Relation Reference.

If you look at the feature dialog now, you will see, that the form of the region
is embedded inside the airports form and will even have a combobox, which allows
you to assign the current airport to another region.

.. _figure_linked_forms:

.. figure:: /static/user_manual/working_with_vector/relations4.png
   :align: center

   Identification dialog airport with relation to regions

.. index:: Many-to-many relation; Relation
.. _many_to_many_relation:

N-M relation
-------------

N-M relation is a many-to-many relation between two tables. For instance, the
``airports`` and ``airlines`` layers: an airport receives several airline
companies and an airline company flies to several airports.

In such case, we need a pivot table to list all airlines for all airports. In
QGIS, you should setup two :ref:`one-to-many relations <one_to_many_relation>`
as explained above:

* a relation between ``airlines`` table and the pivot table;
* and a second one between ``airports`` table and the pivot table.

When we add a new child (i.e. a company to an airport), QGIS will add a new row
in the pivot table and in the ``airlines`` table. If we link a company to an
airport, QGIS will only add a row in the pivot table.

In case you want to remove a link, an airline or an airport, QGIS won't remove
the row in the pivot table. The database administrator should add a *ON DELETE
CASCADE* instruction in the foreign key constraint:

.. code-block:: sql

   ALTER TABLE location.airlines
   ADD CONSTRAINT location_airlines_airports_id_fkey
      FOREIGN KEY (id)
         REFERENCES location.airports(id)
            ON DELETE CASCADE;

.. note:: **Combine N-M relation with automatic transaction group**

  You should enable the transaction mode in :menuselection:`Project Properties
  --> Data Sources -->` when working on such context. QGIS should be able to
  add or update row(s) in all tables (airlines, airports and the pivot tables).

Finally, adding such relations in a form is done in the same way that for a
one-to-many relation. The :guilabel:`Relations` panel in the :guilabel:`Fields`
properties of the vector layer will let the user add the relation in the form.
It will appear as a **Many to many relation**.

