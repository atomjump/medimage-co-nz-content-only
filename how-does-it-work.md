
# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.

# How does it work?


## How does the image get sent?

MedImage makes a decision when an image is being sent to the PC:

* Is a local Wifi MedImage server software on the PC available, and is it on, and enabled in the app? If so, the image will transfer across the local Wifi network. This takes about 1 second for a large definition photo.
* Is a local Wifi MedImage server software on the PC available, and is it on, and enabled in the app? If so, the image will transfer across the local Wifi network. This takes about 1 second for a large definition photo.
* If neither of the above connections are available, it will use the available mobile network e.g. 3G or 4G, to transfer to the internet server, and then down to your local PC via it’s internet connection. This takes around 10-30 seconds total for a high definition image, depending on your connection speed.
* If none of the above are available or if the connection breaks part way through, it will retry after a short period, until the photo is fully transferred. If the mobile network connection keeps dropping the transfer, the gap of attempts will gradually widen, up to 6 hours maximum gap, to allow you to reach a new location and prevent battery drain.


## How does the pairing work?

MedImage uses a unique code which is only valid for one PC server. This unique code is unguessable and only available for 1 hour. Once it is generated, any number of your phones can be used to attach to that local PC.

Once the pairing is complete for a phone, you do not have to do any pairing in future. You can still choose to pair once more if there is a configuration change, however.
