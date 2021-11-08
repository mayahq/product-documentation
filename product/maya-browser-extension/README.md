---
description: >-
  Maya cannot directly control your browser by itself, it needs a man on the
  inside. This job is performed by our browser extension - it provides an
  interface to the Maya app for controlling the browser
---

# Web Extension

## Supported Browsers

| Browser        | Supported?       |
| -------------- | ---------------- |
| Google Chrome  | Yes              |
| Microsoft Edge | Yes              |
| Brave          | Yes              |
| Firefox        | No (Coming Soon) |
| Safari         | No               |

{% hint style="info" %}
For the savvy users out there - the extension supports all Chromium based browsers. If you're using some other Chromium-based browser not mentioned above, it will still work with it.
{% endhint %}

## Installation

If you try to install a Maya skill that uses browser automation, you will be taken through the extension setup. So you don't need to install the extension beforehand. Nevertheless, if you need it for some reason, you can [install it from the web store](https://chrome.google.com/webstore/detail/maya-web-automation/glhdiigjjllhlahaipipmkfknldhbnob).

## Permissions and Security

We employ several safeguards to prevent malicious applications from controlling your browser. There are two, especially, that you need to know about - encryption and permissions.

### Encryption

All communication between the Maya app and the extension is strongly encrypted using a 64-character encryption key. The key can be set only at the extension, and must be communicated with the app. This communication only needs to happen once - the app remembers the key after that.

When you install a skill that uses browser automation, you will be asked to configure the "Maya Browser Automation" module. From that point on, Maya will automatically take you through setting up the connection between the Maya app and the browser extension. The encryption key is communicated to the app during this process as well.

#### Changing the encryption key

If for some reason you need to change the encryption key, you can do so from the extension settings page. You can go to the settings by clicking on the extension icon in your toolbar (pin it if it isn't already) and then clicking the gear icon in the top right of the popup.

![Click the gear icon on the top-right to go to extension settings](<../../.gitbook/assets/image (1).png>)

Upon doing that, you'll be taken to this page. Just click on "Change Key" to change the encryption key, and you're done. You will never see the full key again once you leave this page.

![Click on the purple "Change Key" button to change the encryption key](<../../.gitbook/assets/image (2).png>)

Once you change key, all skills will immediately stop working - the Maya app does not know the new key yet! You can take care of that by connecting the app to the extension again - just reconfigure the "Maya Browser Automation" module from settings.

{% hint style="info" %}
If you're running Maya on a computer owned by your organisation, it might be good for security to change your encryption key once a month.
{% endhint %}

### Permissions

The following automation actions require explicit user permission -&#x20;

* Scrape from a page
* Click on an element
* Type in an input field
* Execute function

These permissions exist at a website level - if you want to perform one of these actions on mail.google.com, you need to give Maya permission for mail.google.com. Unless you give the permisison, Maya will not be able to perform these actions on that page.

{% hint style="info" %}
These permissions are managed by the browser and not by Maya, so Maya cannot give itself permission even if it wants to - it has to come from you.
{% endhint %}

Permissions are given for subdomains, so even if you have given permission to `docs.google.com`, you'll need to give a separate permission to automate `mail.google.com`. At the moment, Maya does not support giving permissions at the subdirectory level, i.e., you cannot give permission to `example.com/xyz` while not giving it for `example.com`. You can only give a permission at the subdomain level, and it applies to all possible URL paths at that subdomain.

You can tell whether or not the extension has permission to a website by looking at the extension icon on that website -

![If there's an "off" label on the extension icon, it does not have permission to the website](<../../.gitbook/assets/image (3).png>)

![No "off" label on the extension icon indicated that it has permission to the website](<../../.gitbook/assets/image (4).png>)

{% hint style="warning" %}
For security reasons, we recommend keeping the extension pinned to the toolbar so that you can always know if it has permissions to the website you're on.
{% endhint %}

#### How to give permissions

In a lot of cases, you do not need to give a permission beforehand - if a Maya skill tries to perform a permission-bound action on a pagethat you haven't given permission for, the skill will immediately fail and the extension will prompt the user for permission. You can give the permission at this point and try running the skill again.

If you want to give permission for a website beforehand, you can do so by navigating to the website in your browser, clicking the extension icon in the toolbar and then clicking the "Allow" button. This will take you to a new page where you'll need to confirm your action.

![](../../.gitbook/assets/permgrant.gif)

{% hint style="danger" %}
Be careful about granting Maya permission to sensitive websites like internet banking or stock trading platforms. Grant permission only when you need to automate such websites, and revoke it afterwards.
{% endhint %}

#### How to revoke permissions

Revoking permissions is as easy as granting them. Just navigate to the website you want to revoke permission for, click on the extension icon and click "Disallow". You will not need to confirm this action - the page will be immediately reloaded and the permission will be revoked.

![](../../.gitbook/assets/permrevoke.gif)

{% hint style="info" %}
Revoking a permission for a website always leads to an immediate page reload. Make sure you save your work on that page before revoking the permission.
{% endhint %}

Optionally, you can also revoke permissions from the extension settings page.

#### View all the permissions you've granted

You can view a list of all the websites you've granted permissions to on the extension settings page. The settings page can be accessed by clicking the extension icon in your browser toolbar and then clicking the gear icon in the top-right of the extension popup. You can also revoke permissions from here.

![You can click on the purple trashcan icon to delete a permission](<../../.gitbook/assets/image (2).png>)

## Browser Automation not working?

You might come accross situations where even though you seem to have set up the extension perfectly well, browser automation skills are still failing. There could be several reasons to this, we'll list out the most common ones here, along with ways to fix them. If none of the fixes work for you, please reach out to [dushyant@mayahq.com](mailto:dushyant@mayahq.com). Please note that sometimes you might have to employ more than one of these fixes to get it to work.

### The extension is not installed

This one's a no-brainer. Make sure the extension is installed on your browser.

### The extension is installed on multiple browsers

Our extension only supports installation on a single browser, and a single profile within that browser. So if you've installed it on more than one browser (or more than one profiles on a single browser), it could fail. To check if this is the case, open the browser you're expecting to control via Maya and click on the extension icon. If this really is the problem, you should see something like this -&#x20;

![](<../../.gitbook/assets/image (5).png>)

To fix this, close all other browsers and profiles where the extension is installed, and then click "Try Again". This should make this error dialogue go away. You might also have to reconfigure the Maya Browser Automation module after this (especially if you had configured it for another browser or profile in the past).

### Broken encryption

It's possible that the Maya desktop app has an outdated encryption key that is no longer used by the extension. You can fix it by reconfiguring the Maya Browser Automation module.

### Native Host Binary not found

Maya uses an additional piece of software to communicate with the extension, called the Native Host Binary. Without it, there cannot be communication and thus browser automation would not work. To check if this is the case, open the browser you're expecting to control via Maya and click on the extension icon. If this really is the problem, you should see something like this -&#x20;

![](<../../.gitbook/assets/image (6).png>)

To fix this, just do what the error dialogue says - make sure you have an active internet connection and restart the app, then click "Try Again". This should make the error go away.

