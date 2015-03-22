FIELDTYPE SELECT EXTERNAL OPTION
================================

Fieldtype which generates the options for a Select Inputfield from *any* table in the database.
Define the source table, columns (to pull value & label) and the preferred Inputfieldtype (Select, Radios, Checkboxes SelectMultiple or ASMSelect) in field settings.
Access to all values in the corresponding row of the source table via API. Frontend safe.

## Installation

## Create a new field
+ # Step 1: Create a new field select fieldtype **SelectExtOption**.
+ # Step 2: Define options under tab **Details**
+ # Step 3: Save. Done! 😃

## Settings
![Screenshot](https://raw.githubusercontent.com/kixe/FieldtypeSelectExtOption/master/screenshot.jpg)

+ #### Inputfieldtype
Fieldtype **SelectExtOption** is compatible with the following Inputfieldtypes.

 + InputfieldSelect
 + InputfieldRadios
 + InputfieldCheckboxes
 + InputfieldSelectMultiple
 + InputfieldAsmSelect

 InputfieldAsmSelect selections are sortable.

+ #### Source Table
Choose any datatable in the database including those which are not depending to Processwire. 
This Field is required.

+ #### Option Value
Select a column of the source datatable to get the value for the option tag.  
Only Integer types allowed. (*This Class extends FieldtypeMulti which stores values as int(11)*.)  
Default Value or Value if nothing selected is always the first column of the table.  
    &lt;option value="**Option Value**" &gt; ...
    
    *note: Option will overwrite the preceding option with same value while generating the select. Unique values recommended.*

+ #### Option Label
Select a column of the source datatable to get the label for the option tag.  
    &lt;option&gt;**Option Label**&lt;/option&gt;  
All types allowed.
Default Value or Value if nothing selected same as **Option Value**.

+ #### Order by Label
Options are ordered by **Option Value**. Check to order by **Option Label**. 

+ #### Order Descending
Order is Ascending by default. Check to switch to **Descending**

## Value
Stored value is simply an integer which makes this fieldtype safe for frontend use too.
Complete access to the belonging row of the selected sourcetable in the database via the following API.


## API 
*note: Access possible to every table in the database, not only PW-Tables or PW-Fields.*

### Access via $page->[fieldname] 
*note: Throws an error notice or fatal error trying to access non existing values.*

```

/** single values (InputfieldSelect)
 *
 * @return WireData Object
 *
 **/
 
$page->myfield->value
$page->myfield->label
$page->myfield->row // associative array of all values of the selected datatablerow

/** muliple values (InputfiedSelectMultiple, InputfieldAsmSelect)
 *
 * @return WireArray Object with WireData elements for each single value like above
 *
 **/

// Examples
$page->myfield->last()->row['land'] // value in datatablerow of the last selection
$page->myfield->first()->row['id']
$page->myfield->eq(3)->value

```

### Access via $modules->get('FieldtypeSelectExtOption') 
*note: Recommended for development to verify Api above. No errors.*

```

/**
 *
 * @return array or multiple array. Elements for each single value like above
 * @return string in case of non existing values
 *
 **/

// call the module
$getdata = $modules->get('FieldtypeSelectExtOption')

// will find the first or only field of type SelectExtOption in current page
$getdata->row();

// will find a specific field of type SelectExtOption in current page, useful if more than one of same type
$getdata->row('myfield');

// will find a specific field of type SelectExtOption in a page found by selector string
$getdata->row('myfield','selectorstring');

// will find the first or only field of type SelectExtOption in a page found by selector string
$getdata->row(null,'selectorstring');

```

Output will be an MultipleArray with the stored value as key.
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

## Links
+ [Support Board processwire.com](https://processwire.com/talk/topic/9320-fieldtype-select-external-option/)
+ [Project Page github.com](https://github.com/kixe/FieldtypeSelectExtOption)

## License
[GNU-GPLv3](http://www.gnu.org/licenses/gpl-3.0.html)

## Author
kixe (Christoph Thelen)