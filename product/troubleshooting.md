---
description: Tips to avoid and recover from some common problems during usage.
---

# Troubleshooting

### Resetting To Defaults

Go to Dashboard > Settings > General > Reset Defaults to reset default settings and start from scratch. This will reset your app and restart it from scratch.

{% hint style="warning" %}
Note, this action is not reversible and deletes all local workspaces, configurations and settings. Backup your workflows by going to the relevant workspace > Hamburger Menu > Export > Download JSON.&#x20;
{% endhint %}

![](<../.gitbook/assets/image (16).png>)

### Browser Not Connecting

By default, the Maya chrome extension and browser integration only works with Chromium based browsers (Chrome, Brave etc). It tries to connect to your default browser, and will not work if tried with non-default or non-Chromium based browsers. If you're still get the error below, drop us a mail at `human@mayahq.com`

![](<../.gitbook/assets/image (54).png>)

### Failed Redirections From Browser On Linux

Features like browser-based authentication and login which require the browser to communicate with the desktop app might fail on a Linux-based OS if `xdg-open` is missing/not working. Try the following : \


1. Install `xdg-utils` on Ubuntu/Debian based installations
2. Use `AppImageLauncher` (install from [here](https://github.com/TheAssassin/AppImageLauncher)) to help easily launch the AppImage file

### Windows Defender Blocking Install

On some older versions of Maya, Windows Defender might show this screen due to lack of an updated EV certificate.

&#x20;![](<../.gitbook/assets/image (19).png>):&#x20;

If you wish to bypass this, click on "More Info" and then press "Run Anyway".

