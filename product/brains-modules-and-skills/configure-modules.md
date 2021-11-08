---
description: Learn how to change the accounts linked with their corresponding modules
---

# Config Profiles

When installing skills or modules via the Maya desktop app, you might have been asked to add config profiles. In this guide, we'll explore config profiles in detail, including what they are, how you can manage them and how they help keep your accounts safe.

## What is a configuration profile

Maya integrates with a range of external services like Google Calendar, Spotify, Zoom, etc. Naturally, to use these services you need to log into them and allow access to Maya - this is where config profiles come in.&#x20;

Each config profile represents a connection to the service accessed by a module. For example, a config profile for the Google Drive module represents a Google account (say `example@gmail.com`) that you've connected to Maya - if you use this config profile with the module, you'll be able to access Google Drive for the related Google account (`example@gmail.com`, in this case).

{% hint style="info" %}
We do things this way because it allows you to connect different accounts to the same module across different brains.
{% endhint %}

## Configuring modules

When we say "configuring modules", what we really mean is selecting config profiles to use for the module. There are two ways you can configure modules.

1. At the time of module installation
2. From the settings

### At the time of module installation

When you install a module from store, Maya might ask you to configure it first. If no config profiles exist for the module, you'll see something like this -

![Config profile prompt for the Google Drive module](<../../.gitbook/assets/image (8).png>)

Just click the purple button (in this case, the "Sign-in with Google" button) and sign in to the service - Maya will take care of the rest. It is important to give the config profile a descriptive name - we've named it `gdrive-personal` because we'll be signing in with our personal mail account.

In this case, on clicking "Sign-in with Google" takes us to this page -&#x20;

![](<../../.gitbook/assets/image (9).png>)

From here we can simply choose an account and sign in. Upon successful sign in, we're redirected to the app again, with a config profile saved. In the module installation dialogue, we can now see this -&#x20;

![The config profile highlighted in purple (gdrive-personal) is selected to be used with this module installation](<../../.gitbook/assets/image (10).png>)

The config profile is now created and saved. It's highlighted in purple, which means it will be used with this module installation.&#x20;

{% hint style="info" %}
You won't have to do this again when you install the Google Drive module the next time - just select this config profile and install the module, the corresponding Google account will automatically be linked.
{% endhint %}

#### Adding more config profiles

Let's say you want to install the Google Drive module in some other brain as well, and this time you want to connect it to your work gmail account instead of your personal account. To do that, click the "+" sign to the right of "Setup Configurations" at the module installation dialog.

![](<../../.gitbook/assets/image (11).png>)

You'll again see this dialog box to create a new profile -&#x20;

![](<../../.gitbook/assets/image (12).png>)

Click "Sign-in with Google" and go through the sign in flow like we did above. When done, you'll see a new profile added to the module installation dialog -&#x20;

![](<../../.gitbook/assets/image (13).png>)

Now, the `gdrive-work` profile is highlighted, which means it will be used when the module is installed, and consequentially the module will access the work account's Google Drive. Both of these config profiles will be available the next time you install the Google Drive module somewhere else, you won't need to login to Google again.

{% hint style="info" %}
You cannot change the module's config profile linked to a brain once it's installed, but you can change the account linked to the config profile.
{% endhint %}

### From the settings

Say you used a config profile linked to your work account for the Google Drive module in five different brains, let's call the config profile `gdrive-work`. Now, you're switching jobs and have a new work account. Naturally, you'd want to change the account linked to `gdrive-work` to your new work account. You can do this from the settings.

1. Open app settings from the side navigation menu.
2. Click on "Configurations" in the top menu. You'll see a list of modules.
3. Find the module you want to change a config profile for, and click the "Configure" button on it's card. In this case, we're doing it for "Google Drive".
4. Find the configuration you want to change and click the edit button on it.

From this point on, the flow is similar to creating a new config profile during module installation. Just click on the "Sign-in" button and complete the sign-in flow of the respective service to finish changing the config profile.

{% hint style="info" %}
Once you change a config profile, you must restart all runtimes that use it.
{% endhint %}

![](../../.gitbook/assets/fromsettings.gif)

{% hint style="warning" %}
You can also add new profiles or delete existing ones from settings as well, but brains will break if you delete profiles that are in use.
{% endhint %}



