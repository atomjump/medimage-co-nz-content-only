<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.

## Apps

* Android
https://play.google.com/store/apps/details?id=com.phonegap.medimage

* iPhone
https://itunes.apple.com/us/app/atomjump-medimage/id1087679463?ls=1&mt=8


## MedImage Server

* Windows 64-bit
https://medimage-download.atomjump.com/MedImageInstaller.exe?ver=1.7.8

* Windows 32-bit 
https://medimage-download.atomjump.com/MedImageInstaller32.exe?ver=1.7.8

* For Mac
http://medimage.co.nz/medimage-server-mac-installation/
Or https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/mac-installation.md

* For linux
https://www.npmjs.com/package/medimage



## Proxy Server Options

* For linux
https://www.npmjs.com/package/medimage

* Windows 64-bit
https://medimage-download.atomjump.com/MedImageInstaller.exe

* Windows 32-bit 
https://medimage-download.atomjump.com/MedImageInstaller32.exe


## Latest Beta

* Windows 64-bit:
https://medimage-download.atomjump.com/MedImageInstaller-beta.exe

* Windows 32-bit:
https://medimage-download.atomjump.com/MedImageInstaller-beta32.exe?ver=1.7.8


## Upgrading Notes

We recommend that you upgrade MedImage Servers prior to 1.6.1 (and >= 1.5.3) to version 1.6.1 via the version 1.6.1 patch. MedImage Servers <= 1.5.3 should be reinstalled/upgraded to 1.6.1 to fix this issue.

If you are upgrading from a Windows MedImage Server prior to 1.0, we recommend you back-up the following files/folders, uninstall the MedImage Server, and remove the folder C:\MedImage, before installing MedImage Server > 1.0, and then installing any add-ons once more.

```
C:\MedImage\config.json
C:\MedImage\photos\
```

If you are updating MedImage Server 1.4 versions to 1.5 versions, and want to take advantage of additional file types e.g. .pdf files, you should add a ‘fileWritten’ event into your C:\MedImage\addons\config.json file, in the same location as the ‘photoWritten’ event. Please refer to a technical person to do this, or reinstall your server again after backing up the files/folders above.
