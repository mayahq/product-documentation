---
description: >-
  Converts between a CSV formatted string and its JavaScript object
  representation, in either direction.
---

# CSV

### Inputs

* `payload` (object | array | string) : A JavaScript object, array or CSV string.

### Outputs

* `payload` (object | array | string) :
  * If the input is a string it tries to parse it as CSV and creates a JavaScript object of key/value pairs for each line. The node will then either send a message for each line, or a single message containing an array of objects.
  * If the input is a JavaScript object it tries to build a CSV string.
  * If the input is an array of simple values, it builds a single line CSV string.
  * If the input is an array of arrays, or an array of objects, a multiple-line CSV string is created.

![](<../../../.gitbook/assets/image (24).png>)

### Details

The column template can contain an ordered list of column names. When converting CSV to an object, the column names will be used as the property names. Alternatively, the column names can be taken from the first row of the CSV.

When converting to CSV, the columns template is used to identify which properties to extract from the object and in what order.

If the columns template is blank then you can use a simple comma separated list of properties supplied in `msg.columns` to determine what to extract and in what order. If neither are present then all the object properties are output in the order in which the properties are found in the first row.

If the input is an array then the columns template is only used to optionally generate a row of column titles.

If 'parse numerical values' option is checked, string numerical values will be returned as numbers, ie. middle value '1,"1.5",2'.

If 'include empty strings' option is checked, empty strings will be returned in result, ie. middle value '"1","",3'.

If 'include null values' option is checked, null values will be returned in result, ie. middle value '"1",,3'.

The node can accept a multi-part input as long as the `parts` property is set correctly, for example from a file-in node or split node.

If outputting multiple messages they will have their `parts` property set and form a complete message sequence.

**Note:** the column template must be comma separated - even if a different separator is chosen for the data.
