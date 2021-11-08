---
description: This is an out node that sends search results back to the command bar.
---

# Custom Search Out

### Inputs

This needs msg.payload to be a list of formatted items for searching.

* `payload` (array) : Array of search items. Each item object should be a JSON object of the form&#x20;
  * `value` (string) : Main value used for searching and display
  * `meta` (object) : miscellaneous meta data
    * `subtext` (string) : subtext to show in list display
    * `icon` (url) : icon to show in list display
    * other key-value pairs can also be included in this object.

```jsonp
//Sample msg.payload
[
    {
        "value":"Template 1",
        "meta":{
            "subtext":"This is template 1"
            "icon" : "https://favicon.com/example1.png"
        }
    },
    {
        "value":"Template 2",
        "meta":{
            "subtext":"This is template 2"
            "icon" : "https://favicon.com/example2.png"
        }
    }
]
```

### Outputs

No outputs since this is an out-node.
