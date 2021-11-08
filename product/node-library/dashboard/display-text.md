---
description: Will display a non-editable text field on the Maya dashboard.
---

# Display Text

Each received `msg.payload` will update the text based on the provided **Value Format**.

The **Value Format** field can be used to change the displayed format and can contain valid HTML and [Angular filters](https://scotch.io/tutorials/all-about-the-built-in-angularjs-filters).

For example: `{{value | uppercase}} &deg;` will uppercase the payload text and add the degree symbol.

The label can also be set by a message property by setting the field to the name of the property, for example `{{msg.topic}}`.

The following icon fonts are also available: [Material Design icon](https://klarsys.github.io/angular-material-icons/) _(e.g. 'check', 'close')_ or a [Font Awesome icon](https://fontawesome.com/v4.7.0/icons/) _(e.g. 'fa-fire')_, or a [Weather icon](https://github.com/Paul-Reed/weather-icons-lite/blob/master/css\_mappings.md). You can use the full set of google material icons if you add 'mi-' to the icon name. e.g. 'mi-videogame\_asset'.

The widget also has a class of `nr-dashboard-widget-{the_widget_label_with_underscores}` which can be used for additional styling if required. You may need to use the _!important_ flag to override the theme.
