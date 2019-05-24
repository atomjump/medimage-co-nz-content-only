
# Software Updates

When we release updates they are either

* new features,
* non-critical fixes,
* or critical fixes.

All of these software fixes are available free of charge, for immediate download.
Critical / Security fixes

We provide notifications of critical fixes (which are often security fixes, but they can also be fixes that could prevent your software from working).

To be notified of these updates, we have two forums which you can opt-in to, by subscribing with your email address:

* Public notification of critical updates
* Vetted notification of critical updates

See/Get Public Notifications
https://medimagepublicupdates.atomjump.com/?autostart=true

The vetted notification is for known customers/partners, who require updates before a public security notification, to allow them to update their software before any potential hackers get a hold of this information. This forum requires password access, and you will need to contact us to get access.

To subscribe to one of these forums: go into the forum (click the large start button, if it hasn’t automatically gone into the chat box), click on the ‘Settings’ button on the bottom left corner, and enter your email address. If you download the free AtomJump Messaging app (available for iPhone and Android), you can also get live ping notifications on your phone.

 
## MedImage Server Upgrade Notes

For Windows platforms :

Unless warned otherwise, upgrading the MedImage Server is a case of downloading the new .exe file,  and installing it over the top of the current MedImage Server. This should retain all of your configuration files, add-ons, and add-on configuration files. We always advise to take a manual back-up of your current C:\MedImage folder before doing this, however, in case you have any issues and wish to roll back.

We also suggest doing this upgrade out-of-office hours.

For Linux/Mac platforms :

There are upgrade scripts available for each of these platforms on their respective download pages.

 
## EHR Connector Upgrade Notes

Please take a backup of the C:\MedImage\addons\ehrconnect\config\ehrconnect.json file before upgrading. You may also like to back up your log files in C:\MedImage\addons\ehrconnect\log\*

A core EHR Connector upgrade involves installing the .exe file over the existing installation. This will clear the existing settings for the connection. You then need to install your EHR specific configuration installer (a .zip add-on), once more. You can either reconfigure the connection, or assuming there were no new additions to the configuration, copy back your old ehrconnect.json file into it’s original location.

If you are only upgrading the EHR specific configuration installer, you can do so, but keep in mind that you will need to reconfigure the connection manually afterwards.

Please do this upgrade out-of-office hours, to ensure that no live users are affected.

 
## Wound Mapp Upgrade Notes

You should install over your current installation.

Before upgrading the Wound Mapp Add-on, you should stop the ‘MedImage’ service (and restart it afterwards). Please keep in mind that if you upgrade the MedImage Server, you will lose the ‘See Photos’ link on the main menu, so you will need to reinstall the Wound Map Add-on afterwards. It is often a good idea to back-up the C:\MedImage\config.json file before any upgrades.

 
## App Upgrade Notes

Depending on the settings on you individual phone, app updates can be set up to occur automatically, when in Wifi range, or on user confirmation.

We will let you know if there are any critical updates via the forums above, but we recommend allowing automatic updates on the app.
