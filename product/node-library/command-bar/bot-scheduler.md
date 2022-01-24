# Bot Scheduler

The Bot Scheduler node can be used to trigger workflows at repeated intervals. CRON expressions are enabled for more granular control.

![In this example, the bot-scheduler outputs the string "teststring" in msg.payload every minute.](<../../../.gitbook/assets/image (47).png>)

{% hint style="info" %}
To aid rapid development of workflows, the schedules are not auto-started by default upon deployment. To start/stop a schedule, tick the 'Autostart' button, or control it via the Play/Pause button on the list of Tasks on the Home screen.
{% endhint %}

![](<../../../.gitbook/assets/image (40).png>)

### Attributes

**Output property**

The `msg.` property to send the payload to. Typically this would be payload.

**Timezone (optional)**

A timezone to use. Leave blank for system timezone. Alternatively, enter UTC or a timezone in the format of Region/Area ([list](https://en.wikipedia.org/wiki/List\_of\_tz\_database\_time\_zones))\
TIP: Timezone should be perceived from your own perspective. See the [Understanding Timezone](http://localhost:3000/edit?id=61ee74abb3a859ad92722097#understanding-timezone) example below.

**Outputs**

* 1 output: All messages to output 1 (schedules + command responses)
* 2 outputs: Schedule messages to output 1, command responses to output 2
* Fan out: Separate outputs for static, dynamic and command messages

**Persist dynamic schedules**

Enabling this option causes dynamic schedules to be saved to file and re-loaded when the bot-scheduler node is loaded or re-deployed.\
NOTES...

* Any time an update to any dynamic schedule occurs, all dynamic schedules are saved to file
* The schedules are saved in a directory called `botschedulerdata` under your node-red folder

**Schedules**

A table of schedules. Entries here are considered static and will be reloaded when node-red starts or the bot-scheduler node is (re)deployed.

**Schedules - Name**

The name is used to identify the schedule. Dynamic adjustments to an individual schedule will need to specify this name.

**Schedules - Topic**

The topic will be sent in `msg.topic` when the schedule triggers. This is to permit the flow to act on the triggered schedule.

**Schedules - Payload**

The value to send in the payload when the schedule triggers. (NOTE: the property that the payload gets written to is determined by "Output property").

**Schedules - Type**

The type determines what type of schedule. Options are `cron`, `dates sequence` or `solar events`

**Schedules - Expression**

_NOTE: Only displayed when the type is set to **cron** or **date sequence**_\
A CRON expression, a date, a comma separated list of dates or an array of dates\
\


Date or Date Sequence Format : \
When you wish to use a fixed date or sequence of dates, the expression can be a string date, comma separated list of dates, an array of dates (The array can contain a mix of string, date objects and timestamps). When specifying a string date, you can use timezone e.g. "2020-01-01 00:00 GMT+2". You can even mix time zones e.g. "2020-01-01 00:00 GMT+2, 2020-01-01 00:00 GMT-7"

CRON Format...

```
 * * * * * * *    Field              Allowed values    Special symbols
     | | | | | | |    -----------------  ---------------   ---------------
     `-|-|-|-|-|-|->  Second (optional)  0-59              * / , -
       `-|-|-|-|-|->  Minute             0-59              * / , -
         `-|-|-|-|->  Hour               0-23              * / , -
           `-|-|-|->  Day of Month       1-31              * / , - ? L W
             `-|-|->  Month              1-12 or JAN-DEC   * / , -
               `-|->  Day of Week        0-7 or SUN-SAT    * / , - ? L #
                 `->  Year (optional)    1970-2099         * / , -
```

Notes...

* `*` Asterisks indicate that the cron expression matches for all values of the field. For example, "\*" in the minute field means every minute
* `?` Question marks are used to specify 'no specific value' and is allowed for the day-of-month and day-of-week fields. It is used instead of the asterisk (\*) for leaving either day-of-month or day-of-week blank.
* `-` Hyphens are used to define ranges. For example, "10-12" in the hour field means the hours of 10, 11, and 12.
* `,` Commas are used to separate items of a list. For example, "MON,WED,FRI" in the day-of-week field means the days Monday, Wednesday, and Friday.
* `/` Forward slash are used to indicate increments. For example. "0/15" in the seconds field means the seconds 0, 15, 30, and 45. Additionally, "1/3" in the day-of-month field means every 3 days starting on the first day of the month.
* `L` Short-hand for "last" and is allowed for the day-of-month and day-of-week fields. The "L" character has a different meaning in each of the two fields. For example, "L" in the day-of-month field means the last day of the month. If used in the day-of-week field, it means 7 or SAT. However, if used in the day-of-week field after another value, it means the last xxx day of the month. For example, "6L" in the day-of-week field means the last Friday of the month
* `W` Short-hand for "weekday" and is allowed for the day-of-month field. The "W" character is used to specify the weekday nearest the given day. For example, "15W" in the day-of-month field means the nearest weekday to the 15th of the month. Therefore, if the 15th is a Saturday, the job runs on Friday the 14th. The "L" and "W" characters can be combined in the day-of-month field. For example, "LW" means the last weekday of the month.
* `#` Hash marks specify constructs. For example, "6#3' in the day-of-week field means the third Friday of the month.

Examples...

* `* * * * * *` Every Second
* `0 * * * * *` Every minute
* `0 */10 * * * *` Every 10 minutes
* `0 */20 1 * * *` Every 20 minutes, between 01:00 AM and 01:59 AM
* `0 15,30,45 * * * *` At 15, 30, and 45 minutes past the hour
* `0 0 12 * * *` Every day at noon - 12pm
* `0 0 2 29 FEB * 2020/4` At 02:00 AM, on day 29 of February (leap years)
* `0 0 7 * * MON#1 *` At 07:00 AM, on the first Monday of the month
* `0 0 12 * JAN,FEB,MAR,APR *` Every day at noon in January, February, March and April
* `* * 1W * *` Every minute, on the first weekday of the month
* `* * * * Tue#3` Every minute, on the third Tuesday of the month
* `0 12 * * MONL` At 12:00 PM, on the last Monday of the month
* See [here](https://github.com/jaclarke/cronosjs) for more examples and info

**Schedules - Solar Events**

_NOTE: Only displayed when the type is set to **solar events**_\
The Solar Events field permits you to chose which solar events you want a schedule to fire upon.\
Solar Events...

| Event ID               | Event                           | Information                                                                      |
| ---------------------- | ------------------------------- | -------------------------------------------------------------------------------- |
| nightEnd               | night end / astronomical dawn   | night ends, astronomical twilight starts (-18°)                                  |
| nauticalDawn           | nautical dawn                   | astronomical twilight ends, nautical twilight starts (-12°)                      |
| civilDawn              | civil dawn / golden hour        | nautical twilight ends, civil twilight and golden hour starts (-6°)              |
| sunrise                | sunrise                         | top edge of the sun appears on the horizon (-0.833°)                             |
| sunriseEnd             | sunrise end                     | bottom edge of the sun touches the horizon (-0.3°)                               |
| morningGoldenHourEnd   | morning golden hour ends        | when the sun is 6 degrees above the horizon (6°)                                 |
| solarNoon              | solar noon                      | sun is at its highest position                                                   |
| eveningGoldenHourStart | evening golden hour start       | when the sun is 6 degrees above the horizon (6°)                                 |
| sunsetStart            | sunset start                    | bottom edge of the sun touches the horizon (-0.3°)                               |
| sunset                 | sunset                          | civil twilight starts, sun disappears below the horizon (-0.833°)                |
| civilDusk              | civil dusk / golden hour end    | civil twilight and golden hour ends, nautical twilight starts (-6°)              |
| nauticalDusk           | nautical dusk                   | nautical twilight ends, astronomical twilight starts (-12°)                      |
| nightStart             | astronomical dusk / night start | astronomical twilight ends, night starts (-18°)                                  |
| nadir                  | solar midnight                  | when the sun is closest to nadir and the night is equidistant from dusk and dawn |

**Schedules - Location**

_NOTE: Only displayed when the type is set to **solar events**_\
The location field is expected to contain longitude and latitude coordinates for the calculation of solar events.\
Accepted formats...

* Decimal Degrees E.g: `54.9992500,-1.4170300` or `54.9992500° N 1.4170300° W`
* Degrees Minutes Seconds E.g: `54° 59' 57.3'' N 1° 25' 1.308'' W`
* Decimal Minutes E.g: `54° 59.955' , -1° 25.0218'`
* GPS E.g: `N54°59'57.3, W1°25'1.308"`, `54°59'57.3"N, 1°25'1.308"W`, `54d 59' 57" N 1d 25' 1" W` or `54:59:57.3N 1:25:1.308W`

**Schedules - Offset**

_NOTE: Only displayed when the type is set to **solar events**_\
The offset field can be used to add a positive or negative offset in minutes to the sunrise or sunset time.

### Outputs

_payload (see 'Output property')_ number|string|boolean|object|buffermsg\[Output property] will contain whatever is configured in 'payload'e.g. if 'Output property' is set to **data.value** then `msg.data.value` will contain the value of the _payload._ msg.topic will contain the name of the schedule. This simplifies separating out which schedule has triggeredAdditional properties are also added to the msg object. Check the debug output (use show complete msg)

### Inputs (advanced usage)



&#x20;_ **\`topic\` (**_**string)** : Most of the commands can be provided in the topic with the name of schedule in the payload (where appropriate).\
Supported command topics...

* trigger
* status
* export
* remove
* pause
* stop
* start

This includes the `-all`, `-all-dynamic`, `-all-static`, `-active`, `-active-dynamic`, `-active-static`, `-inactive`, `-inactive-all-dynamic` and `-inactive-static` command topics (e.g. export-all, stop-all-dynamic, start-all-static, remove-inactive-dynamic)\
See [commands](http://localhost:3000/edit?id=61ee74abb3a859ad92722097#bot-scheduler-commands-info) below for details._payload_string|object|ArrayIt is possible to dynamically add, remove and control schedules by injecting a payload into the node. The format of the payload object (or array of objects) depends on the operation. See below for details.

**Adding one (or more) schedules**\
Example...\


```
payload: [
      {
        "command": "add",
        "name": "every 6",
        "expression": "*/6 * * * * * *",
        "expressionType": "cron",
        "payloadType": "default",
        "limit": 3 
      },
      {
        "command": "add",
        "name": "alarm1",
        "expressionType": "solar",
        "solarType": "selected",
        "solarEvents": "civilDawn,sunrise,sunset",
        "location": "54.999320540937035 -1.417407989501953",
        "offset": "-60",
        "payloadType": "str",
        "payload": "In 60 mins, it will be a great time to take photographs",
        "limit": null
      }
    ]
```

_Details..._\
Adding a CRON expression

* Multiple schedules can be added if the payload is an array of objects
* command: (string|required) The operation to perform - in this case "add"
* name: (string|required) This will identify schedule
* topic: (string|required) This will be used as the topic when the schedule triggers
* expression: (string|optional) A CRON expression, a date, a comma separated list of dates or an array of dates
* expressionType: (string|optional) specify the schedule type. (if omitted, "cron" is the default)
* payloadType: (string|optional) The payload type (e.g. 'default', 'flow', 'global', 'str', 'num', 'bool', 'json', 'bin', 'date' or 'env')
* payload: (any|optional) What to send when schedule triggers
* limit: (number|optional) Maximum number of times the schedule should trigger

\
Adding a date sequence

* Multiple schedules can be added if the payload is an array of objects
* command: (string|required) The operation to perform - in this case "add"
* name: (string|required) This will identify schedule
* topic: (string|required) This will be used as the topic when the schedule triggers
* expression: (string|optional) A CRON expression, a date, a comma separated list of dates or an array of dates
* expressionType: (string|required) specify the schedule type - in this case "dates"
* payloadType: (string|optional) The payload type (e.g. 'default', 'flow', 'global', 'str', 'num', 'bool', 'json', 'bin', 'date' or 'env')
* payload: (any|optional) What to send when schedule triggers
* limit: (number|optional) Maximum number of times the schedule should trigger

\
Adding a solar event schedule

* Multiple schedules can be added if the payload is an array of objects
* command: (string|required) The operation to perform - in this case "add"
* name: (string|required) This will identify schedule
* topic: (string|required) This will be used as the topic when the schedule triggers
* expressionType: (string|required) specify the schedule type. Set to "solar" for solar events
* solarType: (string|required) specify the events to fire. Accepted values are "all" or "selected"
* solarEvents: (string|optional) specify the events to fire. Only required when solarType == "selected". Accepted values are listed under **Schedules - Solar Events** [see above](http://localhost:3000/edit?id=61ee74abb3a859ad92722097#bot-scheduler-solar-events-info)
* location: (string|required) longitude latitude, DNS, DMM or GPS coordinates for sunrise or sunset
* offset: (number|optional) number of minutes to offset a sunrise or sunset
* payloadType: (string|optional) The payload type (e.g. 'default', 'flow', 'global', 'str', 'num', 'bool', 'json', 'bin', 'date' or 'env')
* payload: (any|optional) What to send when schedule triggers
* limit: (number|optional) Maximum number of times the schedule should trigger

_Notes..._\


* This option has no output.

**Getting status of a schedule or removing / stopping / pausing / starting a schedule**\
\
Topic Method...\


```
msg.topic = "command"; // command name - *see details below*,
    msg.payload = "name"; //  name of the schedule
```

Payload Method...\


```
payload: {
      "command": "*see details below*",
      "name": "* name of schedule",
    }
```

_Details..._\


* **command (string|required) :** The operation to perform - this can be one of the following...
  * "trigger"
  * "status"
  * "export"
  * "remove"
  * "stop"
  * "pause"
  * "start"
* name: (string|optional) The name of the schedule to affect (not required when using the -all, -active or -inactive filters)

_Notes..._\


* `trigger` fires schedule named in `msg.payload`
* `status` returns an object with the config and status of the named schedule
* `export` returns an object with the config of the named schedule
* `remove` will stop and remove the schedule. This option has no output.
* `stop` will stop the schedule specified by `name` and reset its internal counter. This option has no output.
* `pause` will stop the schedule specified by `name` but will not reset its internal counter. This option has no output.
* `start` will (re)start all schedules. Any schedule that reached its limit will start from the beginning. Paused schedules will resume. This option has no output.
* FILTER: adding `-all` to any of these commands will operate on all schedules. e.g. `status-all` will return the status of all schedules
* FILTER: adding `-all-dynamic` to any of these commands will only affect dynamic schedules e.g. `remove-all-dynamic` will remove all dynamic schedules
* FILTER: adding `-all-static` to any of these commands will only affect static schedules e.g. `stop-all-static`
* FILTER: adding `-active` to status, export and remove commands will operate on all active schedules. e.g. `status-active`
* FILTER: adding `-active-static` to status, export and remove commands will operate on all static schedules that are active. e.g. `status-active-static`
* FILTER: adding `-active-dynamic` to status, export and remove commands will operate on all dynamic schedules that are active. e.g. `status-active-dynamic`
* FILTER: adding `-inactive` to status, export and remove commands will operate on all inactive schedules. e.g. `status-inactive`
* FILTER: adding `-inactive-static` to status, export and remove commands will operate on all static schedules that are inactive. e.g. `status-inactive-static`
* FILTER: adding `-inactive-dynamic` to status, export and remove commands will operate on all dynamic schedules that are inactive. e.g. `status-inactive-dynamic`

_Examples..._\
Example : Using a simple topic command to manually trigger a schedule named "schedule1"\


```
msg: {
      "topic": "trigger",
      "payload": "schedule1"
    }
```

Example : Using a simple topic command to export all dynamically added schedules...\


```
msg: {
      "topic": "export-all-dynamic"
    }
```

Example : Using a simple topic command to delete a schedule named "schedule1"\


```
msg: {
      "topic": "remove",
      "payload": "schedule1"
    }
```

Example : Using a cmd payload to pause all schedules...\


```
payload: {
      "command": "pause-all"
    }
```

Example : Using a simple topic command to delete all dynamic schedules that have finished\


```
msg: {
      "topic": "remove-inactive-dynamic"
    }
```

**Describe**\
Example : cmd payload to describe a cron expression...\


```
{
      "command": "describe",
      "expressionType": "cron",
      "expression": "0 */5 * * * MON *",
      "timeZone": "Europe/London"
    }
```

Example : cmd payload to get all solar event times + solar state at this time...\


```
{
      "command": "describe",
      "expressionType": "solar",
      "location": "54.9992500,-1.4170300",
      "solarType": "all",
      "timeZone": "Europe/London"
    }
```

Example : cmd payload to get 4 solar event times + solar for a specific point in time...\


```
{
      "command": "describe",
      "expressionType": "solar",
      "time": "2020-03-22 18:40",
      "location": "54.9992500,-1.4170300",
      "solarType": "selected",
      "solarEvents": "civilDawn,sunrise,sunset,civilDusk",
      "timeZone": "Europe/London"
    }
```

_Details..._\
Returns an object in payload containing human readable info for the given expression.

* command: (string|required) The operation to perform
* expression: (string|required) The expression to describe
* timeZone: (string|optional) A timezone to use. Leave blank for system timezone. Alternatively, enter UTC or a timezone in the format of Region/Area ([list](https://en.wikipedia.org/wiki/List\_of\_tz\_database\_time\_zones))

GENERAL NOTES...\


* Adding a schedule with the same name as an existing schedule will replace the existing one
* Adding a schedule with property `"limit":3` will cause that schedule to be stopped after the third trigger. It can be started again by injecting a payload of `{"command":"start" "name": "schedule name"}`
* Static (UI added) schedules can be also be updated by using the name specified in the UI
* When a bot-scheduler-plus node is modified and deployed (or node-red is restarted), dynamic entries are discarded and must be injected again
* When a bot-scheduler-plus node outputs a msg in response to a command, `msg.commandResponse` will be `true` to indicate the message is in response to a command and not a scheduled event
* When a bot-scheduler-plus node outputs a msg for a cron/solar event, `msg.scheduledEvent` will be `true` to indicate the message is due to a scheduled event and not a control response
* The status indicator will be shown as a "ring" for dynamic schedules or shown as a "dot" for static schedules
* if the payload is to "Default Payload", then the content of `msg.botscheduler` is moved to `msg.payload`
