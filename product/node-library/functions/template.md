---
description: Sets a property based on the provided template.
---

# Template

### Inputs

* `msg` (object) : A msg object containing information to populate the template.
* `template` (string) : A template to be populated from msg.payload. If not configured in the edit panel, this can be set as a property of msg.

### Outputs

* `msg` (object) : a msg with a property set by populating the configured template with properties from the incoming msg.

![](<../../../.gitbook/assets/image (55).png>)

### Details

By default this uses the [_mustache_](http://mustache.github.io/mustache.5.html) format, but this can be switched off if required.

For example, when a template of:

```
Hello {{payload.name}}. Today is {{date}}
```

receives a message containing:

```
{
  date: "Monday",
  payload: {
    name: "Fred"
  }
}
```

The resulting property will be:

```
Hello Fred. Today is Monday
```

It is possible to use a property from the flow context or global context. Just use `{{flow.name}}` or `{{global.name}}`, or for persistable store `store` use `{{flow[store].name}}` or `{{global[store].name}}`.

\*\*Note: \*\*By default, _mustache_ will escape any non-alphanumeric or HTML entities in the values it substitutes. To prevent this, use `{{{triple}}}` braces.
