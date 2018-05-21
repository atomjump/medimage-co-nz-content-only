<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.



# FAQ



__Q. Where do the photos appear?__

A. If you use the default settings a folder will be created on your desktop, and the photos will go there once transferred. However, this is configurable (and if a Medical package is detected e.g. MedTech, it may default to it’s media folder) during installation. In ver >= 1.3.4, you can view and change this in ‘Settings’.  Note: The photos will appear temporarily in C:\MedImage\photos as a staging space before being moved into your target folders.  Prior to ver 1.3.4, a back-up of the photos also remained in C:\MedImage\photos.

 

__Q. How do I re-open the server?__

A. You will find ‘MedImage Server’ on your Windows start bar under your ‘programs’, depending on which version of Windows you are using. There is also a desktop icon. If you cannot find this, you can also enter ‘localhost:5566’ into your browser URL bar.

 

__Q. Do I need any technical knowledge?__

A. You do not need technical knowledge. You should have a Windows PC (e.g. Vista, 7, 10, Server. Note: <= Win XP is not supported). You should also have ‘Administrator’ access, so that you can install the server. If not, you will likely need to get in touch with your system administrator.

 

__Q. What sort of phone can I use?__

A. Almost any Android phone or tablet, and almost any iPhone or iPad.

 

__Q. Can I use MedImage out of the office, with patients?__

A. Yes, provided you have connected initially via an AJ (AtomJump) server, or your own cloud proxy server.

 

__Q. Do I need to keep my PC on all the time?__

A. No you don’t have to.

If you have synced your phone initially via an AJ (AtomJump) server, or your own cloud proxy server, and the PC is off, it will get the images that you took as soon as you turn the PC back on again.

If you are connected via Wifi, then the app will wait until your PC is switched on.

 

__Q. Can I send photos from the phone gallery?__

A. No, only new photos can currently be taken with the app. The photo is stored in the app’s directory, until the app knows it has transferred the image fully to the server, when the photo is then removed from the phone.

 

__Q. Can I sync to a network folder?__

A. Yes, when you install the server, you have the choice of which folder to write to, and this can be a network folder. You can also choose to add additional backup folders if you have some technical configuration skill. Please note: the user that installs the MedImage Server must have administrative privileges, and be able to read and write to the target network folder.  Any network drive mappings should be available to the user that installed MedImage Server, when run as a background service, but if not, you can use the network path e.g. \\server\folder format. Also see the Technical Guide for further troubleshooting tips.

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/technical-guide.md


__Q. I have looked at setting up a cloud proxy server, but it looks difficult. Can you help?__

A. Yes, we have people trained to help with your own private setups. While the server software is free and open source, and we can offer advice over the web, we do charge for custom installations, particularly if there is any need for us to be on-site.

 

__Q. How does the app transfer the image?__

A. The app uses Wifi, if available and desired, and if not, it will transfer via your 3G or 4G mobile data connection. See a detailed transfer explanation here:

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/how-does-it-work.md

Note: 3G or 4G connections have standard data transfer fees depending on your mobile provider.

 

__Q. How long will your 500MB free transfer via the AtomJump (AJ) servers last me?__

A. If you take 10 photos a week, this will last around two months.

 

__Q. Is it secure?__

Simple A. Yes, as MedImage, unlike other applications, does not store the images in the phone memory, but instead sends the file directly to the destination specified, and then deletes it from the phone immediately. Also you can have your own custom server built for high-end security, or use our AJ (AtomJump) servers.

Full A. Firstly, no digital system is ever 100% secure. Any provider who claims that their product is, does not know the reality of digital security. Instead, there are different levels of security and we would recommend taking a pragmatic approach as to what level you require.

We would grade the default installation of MedImage, over a 3G/4G connection, and using the AJ servers, as around the same level of security as a mobile phone banking app.

Using MedImage over a Wifi connection, it depends on how many people know your Wifi password and who has access to it, but we would generally grade this as closer to sending an email, which is less secure than a 3G/4G connection.

There are ways for you to enhance your security further, while still using our app:

a) by using dedicated devices such as tablets, and locking down their access to the internet. You would only let through images to your cloud servers.

b) you can take this further still, and block all network access to the tablet, until the tablet is connected by a physical cable, at which time the images can be transferred.

c) since you can download the MedImage server, the software can be placed within your own firewalled network. However, we would strongly recommend using an ‘https’ server, and only resort to an ‘http’ server for initial testing.

It should be noted, that the image is only kept on the phone until it has been transferred, after which it is deleted off the phone, and is not available in the ordinary phone gallery. This is important if the phone was lost, stolen or hacked.

Our software is open and available for review. We would suggest that if you have any concerns, you can employ an external security firm to audit your installation and our software. We are always open for security reviews, and happy to make adjustments if there are any flaws discovered. We can also offer guidance and carry out installations for you, if you wish.

 

__Q. How do I change the target images folder on a live installation?__

A. In ver >= 1.3.4, you can do this in the Settings page. Prior to this, the best idea is to edit the file C:\medimage\config.json on your server machine in a text editor (we would recommend ‘TextPad’, but Windows Notepad can be used too). Firstly, save a backup of this file just to know how it was originally.

You should see something similar to this:

```
{
“purpose“: “MedImage Server Configuration File. Example readproxy http://YOURIP:5566/read/yourdir“,
“backupTo“: [“C:/yourfolder” ],
“readProxy“: null,
“listenPort“: 5566,
“allowPhotosLeaving“: false,
“allowGettingRemotePhotos“: true
}
```

Change the “backupTo” entry to whatever you have changed the folder to. Note, the folder should always be using forward slashes ‘/’ rather than the conventional Windows backslash ‘\’.  Then save the file again, and either restart the whole machine (depending on how many people are using it), or you can enter the Windows ‘services’, look down for ‘MedImage’, click it once, and then click ‘Restart the service’.

 

__Q. Is there any research on using mobile phone cameras in a medical context?__

A. This is a good 2015 phone camera dermatology study https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4439742/, and Dermnet have some more recent guidelines.  It should be noted that we believe MedImage provides a more secure approach to the options mentioned in the first article.

https://www.dermnetnz.org/cme/dermatoscopy-photography/security-saving-sharing-images/
 

__Q. Our advice has been that mobile phones shouldn’t be used for medical imaging. How is this different?__

A. You should listen to your independent advisers. Indeed, as a software vendor, it is not our place to provide independent advice for you on your privacy and security policies.  However, please keep in mind that the majority of this advice was formed before MedImage existed.  We also agree with the general guidelines: that a mobile phone camera, in it’s native form, should not be used in a medical environment.

Since we are an open company, we invite your policy decision makers to make their own assessment of the technology that MedImage uses; and all of our software is available for review. Our internal assessment is that MedImage is at a similar level of security to a mobile phone banking app, and considerably more secure than emailing an image to a third party or using the built-in camera app. However, no digital system is ever 100% failsafe. The app was created at the request of GPs who deal with privacy matters, and is in active use by GPs. You can refer to the question about security above for further details.

 

__Q. Does this need to be configured to get past our firewall?__

A. No. You will only need your PC to have ‘read’ access to the Web. So, if you can use a browser and browse the internet on your PC, then you can install the MedImage Server software. It works by ‘polling’ the remote server for new images, and when it finds one, the image will be downloaded to your PC.

 

__Q. Are the images transferred full, original quality?__

A. Yes they are. The resolution will vary depending on which phone model is used, and you can configure this with the normal photo quality options on your phone (which varies slightly between makes and models). A typical full resolution Android photo might be 5312×2918 pixels, though you can reduce the size if you want a faster transfer.

 

__Q. How do I check which version of the server I am running?__

A. You can look in ‘Programs and Features’ in Windows control panel for the installer version that is installed. Or you can open the file C:\medimage\package.json in Notepad, and look for the ‘version’ entry e.g. “version”: “0.8.3”. This version number reflects the server software, but may be slightly different to the Windows installer version.

 

__Q. My photos don’t seem to appear in my EHR e.g. MedTech, using the add-on?__

A. Make sure you have a working database connection (under ‘Settings/EHR Connector’ from within the Server). If your connection is already working correctly, check the ‘EHR Logs’ link from within the server. It will show a live list of the photos that were entered into your EHR system and any errors.

The correct format from within the app is ‘[Patient ID number] [injury name]’, for example ‘BGDH1233 arm’, or if you have the app option ‘ID writes a folder’ off, you can enter e.g. ‘#BGDH1233 arm’. Please refer to the full user guide of the EHR Connector Add-on:

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/ehrconnect-addon.md


__Q. Can I remove the original full-sized photo when using the Resizer add-on?__

A. Yes, you can optionally choose to do this. If you don’t need to keep the original image, you can set the “Photo Filename Text to Replace” field to ‘.jpg’, and the “with this” field to ‘.jpg’, also, in your ‘Resize options’ settings tab.



 