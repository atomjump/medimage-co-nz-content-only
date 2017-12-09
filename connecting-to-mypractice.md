<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.





# myPractice – Guide

The myPractice medical system is a popular alternative to MedTech32 within New Zealand’s GP practices. The software is easy to use and you have a readily contactable supplier based in Auckland.

The good news for myPractice users who want to use MedImage – there is no add-on needed, and therefore no additional cost. The free MedImage Server works out of the box. If you want to have a shared group of photos that the whole practice has access to, make sure you select the scanned media folder that your myPractice system uses, during the MedImage Server installation. Then follow the regular steps to synchronise each phone.

You’re done!



 

## Frequently Asked Questions

__Q. How do I attach the photos MedImage creates in myPractice?__

A. If you selected your shared myPractice ‘scanned-media’  folder during your MedImage installation, then you should select the ‘Scan’ button and associate a patient ID with the photo that you have sent in the screen that appears.



If you have installed your own copy of MedImage Server on your local PC, then use the ‘Attachment’ link to pull the photo into the patient’s record.



 

__Q. How should I name the photos in MedImage?__

A. You would ideally enter an NHID or a name of the patient in the app before taking the photo, so that the photo can be matched up with the patient’s record in the Scan Media page. Typically you would also describe the wound. eg.

```
NHI5432 arm
``` 


__Q. Can I use subfolders in MedImage with myPractice?__

A. If you are using the scanned media folder, then we would not recommend using subfolders. You should also leave off the ‘ID writes a folder’ option in your MedImage app. If you wish to install a personal copy of MedImage Server on your own machine, then you can arrange these photos as you choose, however, and include subfolders.

 

__Q. Our myPractice setup has a Windows server and several client PCs. Should I install the MedImage Server on all of the PCs, or just the Windows server?__

You can choose either option, but it is usually easier to install the MedImage Server once, and put this on the central Windows server. For other users who wish to then pair their phones, they would either login to the Windows server once, or access the MedImage Server through their browser e.g. ‘http://your.windows.server.ip:5566’.

Alternatively, you could install the MedImage Server on individual PCs and point the photos into a shared network folder on the central server.

Or, you could install the MedImage Server on each individual PC and let users attach their own photos with the ‘Attachment’ link from their desktop.