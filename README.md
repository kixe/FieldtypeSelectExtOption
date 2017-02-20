FIELDTYPE SELECT EXTERNAL OPTION
================================

Fieldtype which generates the options for a Select Inputfield from *any* table in *any* (accessible) database not only PW-Tables or PW-Fields. Define the source table, columns (to pull value & label) and the preferred Inputfieldtype (Select, Radios, Checkboxes SelectMultiple or ASMSelect) in field settings. Access to all values in the corresponding row of the source table via API. Frontend safe.

## Create a new field
+ Step 1: Create a new field select fieldtype **SelectExtOption**.
+ Step 2: Define options under tab **Details**
+ Step 3: Save. Done! ![smile](data:image/svg+xml;base64,PHN2ZyB2ZXJzaW9uPSIxLjEiIGJhc2VQcm9maWxlPSJmdWxsIiB4bWxuczpldj0iaHR0cDovL3d3dy53My5vcmcvMjAwMS94bWwtZXZlbnRzIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiBwcmVzZXJ2ZUFzcGVjdFJhdGlvPSJ4TWlkWU1pZCBtZWV0IiB6b29tQW5kUGFuPSJtYWduaWZ5IiB2aWV3Qm94PSItMjEgLTIxIDQyIDQyIiB3aWR0aD0iMjUiIGhlaWdodD0iMjUiPjwhLS0gaHR0cHM6Ly91cGxvYWQud2lraW1lZGlhLm9yZy93aWtpcGVkaWEvY29tbW9ucy84Lzg1L1NtaWxleS5zdmctLT48ZGVmcz48cmFkaWFsR3JhZGllbnQgaWQ9InNoaW5lIiBjeD0iLjIiIGN5PSIuMiIgcj0iLjUiIGZ4PSIuMiIgZnk9Ii4yIj48c3RvcCBvZmZzZXQ9IjAiIHN0b3AtY29sb3I9IndoaXRlIiBzdG9wLW9wYWNpdHk9Ii43Ii8+PHN0b3Agb2Zmc2V0PSIxIiBzdG9wLWNvbG9yPSJ3aGl0ZSIgc3RvcC1vcGFjaXR5PSIwIi8+PC9yYWRpYWxHcmFkaWVudD48cmFkaWFsR3JhZGllbnQgaWQ9ImdyYWQiIGN4PSIuNSIgY3k9Ii41IiByPSIuNSIgPjxzdG9wIG9mZnNldD0iMCIgc3RvcC1jb2xvcj0ieWVsbG93Ii8+PHN0b3Agb2Zmc2V0PSIuNzUiIHN0b3AtY29sb3I9InllbGxvdyIvPjxzdG9wIG9mZnNldD0iLjk1IiBzdG9wLWNvbG9yPSIjZWUwIi8+PHN0b3Agb2Zmc2V0PSIxIiBzdG9wLWNvbG9yPSIjZThlODAwIi8+PC9yYWRpYWxHcmFkaWVudD48L2RlZnM+PGNpcmNsZSByPSIyMCIgc3Ryb2tlPSJibGFjayIgc3Ryb2tlLXdpZHRoPSIuMTUiIGZpbGw9InVybCgjZ3JhZCkiLz48Y2lyY2xlIHI9IjIwIiBmaWxsPSJ1cmwoI3NoaW5lKSIvPjxnIGlkPSJyaWdodCI+PGVsbGlwc2Ugcng9IjIuNSIgcnk9IjQiIGN4PSItNiIgY3k9Ii03IiBmaWxsPSJibGFjayIvPjxwYXRoIGZpbGw9Im5vbmUiIHN0cm9rZT0iYmxhY2siIHN0cm9rZS13aWR0aD0iLjUiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgZD0iTSAxMC42LDIuNyBhIDQsNCwwIDAsMCA0LDMiLz48L2c+PHVzZSB4bGluazpocmVmPSIjcmlnaHQiIHRyYW5zZm9ybT0ic2NhbGUoLTEsMSkiLz48cGF0aCBmaWxsPSJub25lIiBzdHJva2U9ImJsYWNrIiBzdHJva2Utd2lkdGg9Ii43NSIgZD0iTSAtMTIsNSBBIDEzLjUsMTMuNSwwIDAsMCAxMiw1IEEgMTMsMTMsMCAwLDEgLTEyLDUiLz48L3N2Zz4=)

## Settings
![Screenshot](https://raw.githubusercontent.com/kixe/FieldtypeSelectExtOption/master/screenshot.jpg)

+ #### Inputfieldtype
Fieldtype **SelectExtOption** is compatible with the following Inputfieldtypes. You maybe need to adapt InputfieldPage to make all the options available.

 + InputfieldSelect
 + InputfieldRadios
 + InputfieldCheckboxes
 + InputfieldSelectMultiple
 + InputfieldAsmSelect
 + InputfieldSelectMultipleTransfer [**(note)**](#multitransfer)

 InputfieldAsmSelect selections are sortable.
 3d party modules maybe supported too.  
 Have a look here: [**Developers Note**](#devnote).

+ #### Source Table
Choose any datatable in the database including those which are not depending to Processwire. 
This Field is required.

+ #### Option Value
Select a column of the source datatable to get the value for the option tag.  
Only Integer types allowed. (*This Class extends FieldtypeMulti which stores values as int(11)*.)  
Default column or column if not selected is always the first column of the table.  
    &lt;option value="**Option Value**" &gt; ...
    
    *note: Option will overwrite the preceding option with same value while generating the select. Unique values recommended.*

+ #### Option Label
Select a column of the source datatable to get the label for the option tag.  
    &lt;option&gt;**Option Label**&lt;/option&gt;  
All types allowed.
Default label or label if not selected same as **Option Value**.

+ #### Filter
Small Filter to limit the options if needed. Adds a **WHERE** condition to the **SELECT** statement 
which pulls the options from the datatable. Function filter() is hookable.

+ #### Order by Label
Options are ordered by **Option Label**. Select to order by any other column. 

+ #### Order Descending
Order is Ascending by default. Check to switch to **Descending**


## API 

### Return a field value: $page->[fieldname]->[property]
All column values are populated as a property (columnname) except values of columns 
named with reserved words ('label', 'value', 'row', 'options' and 'data').  

```

/** 
 * single values (InputfieldSelect)
 * @return SelectExtOption Object (extended WireData Object)
 *
 **/
 
$page->myfield->value
$page->myfield->label
$page->myfield->row // assoc array (columnname => value) of all values of the selected datatablerow
$page->myfield->options // assoc array (value => label) of all selectable options
$page->myfield->columnname-1
$page->myfield->columnname-2 // ...

/**
 * muliple values (InputfiedSelectMultiple, InputfieldAsmSelect)
 * @return WireArray Object with SelectExtOption elements for each single value like above
 *
 **/

// Usage Examples
$page->myfield->last()->row['land'] // value of column 'land' of last selected item
$page->myfield->first()->row['id']
$page->myfield->eq(3)->value // integer value of 4th item in array of selected items
$page->myfield->each('pages_id') // array of value of column 'pages\_id' of each item

```

*note: to get the value of a column named by reserved word use the row property, like $page->myfield->row['data']*

### Set a field value

```

/* Inputfieldtype Select */
$page->of(false);
$page->myfield->value = 3;
$page->save('myfield');


/* Inputfieldtype SelectMultiple (add a single value) */
$v = new SelectExtOption;
$v->value = 3;
$page->of(false);
$page->myfield->add($v);
$page->save('myfield');


/* Inputfieldtype Select/SelectMultiple. Will replace existing values */
$page->of(false);
$page->myfield = array(3,7,9); // Example Values
$page->save('myfield');

```

*note: trying to set a not existing value will be ignored*

### Public module functions options() and row()

```

// call the module
$getdata = $modules->get('FieldtypeSelectExtOption');

// return array of all possible value/ label pairs version >= 1.1.6 
$getdata->options('selector'); // selector = field-name, field-id or field-instance

// will find the first or only field of type SelectExtOption in current page
$getdata->row();

// will find a specific field of type SelectExtOption in current page, useful if more than one of same type
$getdata->row('myfield');

// will find a specific field of type SelectExtOption in a page found by selector string
$getdata->row('myfield','selectorstring');

// will find the first or only field of type SelectExtOption in a page found by selector string
$getdata->row(null,'selectorstring');

```

Function row() will return a MultipleArray with the stored value as key.

#### Example
+ Field Settings

 + **Inputfieldtype** = 'InputfieldAsmSelect'
 + **Source Table** = 'pages'
 + **Option Value** = 'id'
 + **Option Label** = 'name'

+ Selected Values in Frontend

 + 'admin'
 + 'user'

+ Code
 + $getdata = $modules->get('FieldtypeSelectExtOption');
 + $getdata->row();

+ Output

```

array (size=2)
  2 => 
    array (size=10)
      'id' => string '2' (length=1)
      'parent_id' => string '1' (length=1)
      'templates_id' => string '2' (length=1)
      'name' => string 'admin' (length=5)
      'status' => string '1035' (length=4)
      'modified' => string '2015-01-29 06:37:43' (length=19)
      'modified_users_id' => string '41' (length=2)
      'created' => string '0000-00-00 00:00:00' (length=19)
      'created_users_id' => string '2' (length=1)
      'sort' => string '15' (length=2)
  29 => 
    array (size=10)
      'id' => string '29' (length=2)
      'parent_id' => string '28' (length=2)
      'templates_id' => string '2' (length=1)
      'name' => string 'users' (length=5)
      'status' => string '29' (length=2)
      'modified' => string '2011-04-05 00:39:08' (length=19)
      'modified_users_id' => string '41' (length=2)
      'created' => string '2011-03-19 19:15:29' (length=19)
      'created_users_id' => string '2' (length=1)
      'sort' => string '0' (length=1)

```

## Developers Note<a id="devnote"></a>
3d party Inputfieldtypes are supported too, if they are subclasses of **InputfieldSelect**. Furthermore they should be added in settings of **InputfieldPage** module. No guarantees that these Inputfieldtypes will work as expected.  
Please test carefully.  
Working example: [InputfieldChosenSelect](http://modules.processwire.com/modules/inputfield-chosen-select/).

<a id="multitransfer"></a>[InputfieldSelectMultipleTransfer](http://modules.processwire.com/modules/inputfield-select-multiple-transfer/) will be supported after removing the '&gt;' in the selector string of javascript file.
(Line 3 and 19 InputfieldSelectMultipleTransfer.js)

## Changelog
+ **1.1.3** function filter() is hookable  
   filter() returns the WHERE clause which will be added to the SELECT command.  
   You can specify more than one condition using AND or OR operators.  
+ **1.1.6** function options() to get the array of all possible value/label pairs
+ **1.1.7** all options provided as property
+ **1.1.8** support for other databases and external hosts set in field settings
+ **1.1.9** corrected translatable strings
+ **1.2.0** changed Version to make available for PW 3.0
+ **1.2.1** fixed namespace issue (selectable Inputfields)
+ **1.2.3** added config field for initial selection (default value)
+ **1.2.4** added config field for other language labels)

## Links
+ [Support Board processwire.com](https://processwire.com/talk/topic/9320-fieldtype-select-external-option/)
+ [Project Page github.com](https://github.com/kixe/FieldtypeSelectExtOption)

## License
[GNU-GPLv3](http://www.gnu.org/licenses/gpl-3.0.html)

## Author
kixe (Christoph Thelen)
