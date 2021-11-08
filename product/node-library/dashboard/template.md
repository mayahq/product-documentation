---
description: Add any valid piece of HTML to the Maya dashboard.
---

# Template

The template widget can contain any valid html and Angular/Angular-Material directives.

This node can be used to create a dynamic user interface element that changes its appearance based on the input message, and can send messages back to Maya.

Will display if the number received as `msg.payload` is even or odd. It will also change the color of the text to green if the number is even or red if odd.\
The next example shows how to set a unique id for your template, pick up the default theme colour, and watch for any incoming message.

```
<div id="{{'my_'+$id}}" style="{{'color:'+theme.base_color}}">Some text</div>
<script>
(function(scope) {
  scope.$watch('msg', function(msg) {
    if (msg) {
      // Do something when msg arrives
      $("#my_"+scope.$id).html(msg.payload);
    }
  });
})(scope);
</script>
```

Templates made in this way can be copied and remain independent of each other.

**Sending a message:**

```
<script>
var value = "hello world";
// or overwrite value in your callback function ...
this.scope.action = function() { return value; }
</script>
<md-button ng-click="send({payload:action()})">
    Click me to send a hello world
</md-button>
```

Will display a button that when clicked will send a message with the payload `'Hello world'`.

**Using `msg.template`:**\
You can also define the template content via `msg.template`, so you can use external files for example.\
Template will be reloaded on input if it has changed.\
Code written in the Template field will be ignored when `msg.template` is present.

The following icon fonts are available: [Material Design icon](https://klarsys.github.io/angular-material-icons/) _(e.g. 'check', 'close')_ or a [Font Awesome icon](https://fontawesome.com/v4.7.0/icons/) _(e.g. 'fa-fire')_, or a [Weather icon](https://github.com/Paul-Reed/weather-icons-lite/blob/master/css\_mappings.md). You can use the full set of google material icons if you add 'mi-' to the icon name. e.g. 'mi-videogame\_asset'.
