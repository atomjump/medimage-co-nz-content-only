<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.

# How To


## Pair a phone with your PC

Assuming you have installed both your MedImage server on your PC and the MedImage app on your phone.

1. Open your MedImage server on your PC
2. Click on one of the large ‘pairing buttons’ (and consider any options in the ‘View Details’ section)
3. With the generated code, enter this into your phone app. If this is the first time you have used the app, tap on the large button in the middle of the app, and enter this code when asked. If it is a new PC, see the instructions below under ‘Use MedImage across multiple locations, or PCs’.


 

## Take a photo with your app

In your app:

1.  enter an identifier for your photo
2. Click the large ‘Camera to PC’ button, and take your photo
3. Confirm it is the photo you want
4. Wait for the photo to transfer to your PC

On your PC:

1. Open up your MedImage folder, which is where you set it during installation (it defaults to your desktop, and will be created in a few seconds, if it isn’t there already. If this doesn’t appear, look in C:\MedImage\Photos)
2. Go to the subfolder of your patient ID
3. You will see the patient’s photo, already named



## Create a folder, or create more advanced directories/filenames

You can prepend a ‘#’ to any word in the ID field of your app, and it will create a folder. The folder will be created if it doesn’t exist, or add to it, if it already exists, so nothing is ever removed.

Here are some examples of what to enter in the ID field:

```
Enter                        Created on your PC
file                         \file-datetime.jpg
#folder                      \folder\datetime.jpg
#folder file                 \folder\file-datetime.jpg
#folder #subfolder file      \folder\subfolder\file-datetime.jpg
file fileagain               \file-fileagain-datetime.jpg
[blank]                      \image-datetime.jpg
``` 

## Create a folder by default for every Patient ID

In your app:

1. Tap on the ‘Settings’ three bars in the bottom right hand corner.
2. Switch on ‘ID writes a folder’
3. Close the options.
4. Tap inside the ID field and start typing your patient ID.
5. Capture the image and send. The folder will be called your patient ID on your PC. The ‘#’ works just as normal on any secondary words and would creates a subfolder for the image off the parent folder.




 

## Install multiple MedImage servers on the same Wifi Network

Currently, this configuration is not fully supported with fast WiFi scanning/sending. The app will choose the first MedImage server that it finds, which could result in photos being sent to the wrong PC.

Instead, each phone should be paired with the corresponding PC manually, and you should select ‘no’ when asked ‘Do you want to connect via WiFi, if it is available, also?’ during the pairing. The phone will still potentially use a Wifi network to upload, but it will go via the internet before coming down to the PC.

 

## Use MedImage across multiple locations, or PCs

1. Tap on the ‘Settings’ three bars in the bottom right hand corner.
2. Touch ‘Add a New PC’
3. Enter a name for the PC
4. Touch the large ‘Camera to PC’.
5. Open the MedImage server in the new location and choose one of the pairing options. Enter this code in your phone.

To switch between locations in future, click ‘Settings’ and then touch the PC you have added. You can delete obsolete PCs with the ‘trash can’ next to each of them.