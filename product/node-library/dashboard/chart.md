---
description: Add dynamic line, bar, pie, polar area and radar charts to the Maya dashboard.
---

# Chart

![](<../../../.gitbook/assets/image (24).png>)

### Live data

To display live data just wire up an input with a `msg.payload` that contains a number.

#### Line charts

To display two or more lines on the same chart then each `msg` must also contain `topic` property that identifies which data series it belongs to - for example:

```
{topic:"temperature", payload:22}
{topic:"humidity", payload:66}
```

Each series will be represented by a different colour. Alternatively you can use the property `series` instead of `topic` if you prefer.

It is possible to create "gaps" in line charts by sending either a null or boolean false as the payload.

You can also insert extra data points by specifying the `timestamp` property. This must be in either epoch time (in miliseconds, not seconds), or ISO8601 format.

```
{topic:"temperature", payload:22, timestamp:1520527095000}
```

#### Bar, and other charts

If you want all the bars to be the same colour, then use the `label` property instead.

```
{label:"indoor temperature", payload:22}
{label:"outdoor temperature", payload:15}
```

You can have both a label and series property if you want.

### Stored data

To display a complete chart in one go - for example from a set of points retrieved from a database, the data must be supplied in the form of an array, that holds an object that has `series`,`labels`, and `data` arrays. This is broadly the same as the raw format used by the angular chart.js library.

You will need to process your data into this structure in order to render it correctly.

#### Line charts

For line charts an example is given below

```
[{
"series": ["A", "B", "C"],
"data": [
    [{ "x": 1504029632890, "y": 5 },
     { "x": 1504029636001, "y": 4 },
     { "x": 1504029638656, "y": 2 }
    ],
    [{ "x": 1504029633514, "y": 6 },
     { "x": 1504029636622, "y": 7 },
     { "x": 1504029639539, "y": 6 }
    ],
    [{ "x": 1504029634400, "y": 7 },
     { "x": 1504029637959, "y": 7 },
     { "x": 1504029640317, "y": 7 }
    ]
],
"labels": [""]
}]
```

For non-timeseries data - for example data in labelled categories, rather than use x and y, the format should be as follows:

```
[{
    "series": ["X", "Y", "Z" ],
    "data": [ [5,6,9,10], [3,8,5,10], [6,7,2,10] ],
    "labels": [ "Jan", "Feb", "Mar", "Apr" ]
}]
```

#### Bar and Pie charts

for bars of different colours

```
[{
    "series": [ "X", "Y", "Z"],
    "data": [ [5], [3], [6] ],
    "labels": [ "Jan" ]
}]
```

for bars of the same colour, set the flag `Use first colour for all bars` in the node configuration, and set labels for each column

```
[{
    "series": [ "X" ],
    "data": [ [5,6,9] ],
    "labels": [ "Jan", "Feb", "Mar" ]
}]
```

and these can be mixed - you can have series and labels defined...

```
[{
    "series": ["X", "Y", "Z" ],
    "data": [ [5,6,9,10], [3,8,5,11], [6,7,2,12] ],
    "labels": [ "Jan", "Feb", "Mar", "Apr" ]
}]
```

### Example

You can import this directly into the Maya dashboard to see how it works.

{% file src="../../../.gitbook/assets/charts.json" %}

Source : [Node-RED](https://github.com/node-red/node-red-dashboard/blob/master/Charts.md)
