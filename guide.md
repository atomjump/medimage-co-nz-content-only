<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Guide


## The App

This app allows the medical professional to upload a photo and ID from their phone of a patient’s case e.g. a mole, and transfer the image directly to the patient’s file on their PC. The app is currently available for Android, and iOS iPhone/iPad. Each doctor will need an app for their own phone, and can also be found by searching the App Store for ‘medimage’, or ‘medimage atomjump’.

See the ‘How To’ guide, the ‘How does it work?’ section, or the FAQ for further tips.

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/how-to.md

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/how-does-it-work.md

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/faq.md


## The PC Server

In order for you to receive the photos from your phone, you need to download a companion server to your PC. This server has a straightforward installer ready for Windows machines. You can test this out directly, without any technical knowledge, if you have a Wifi connection shared between your PC and your phone. If you wish to use the internet only, you can choose an easy 4 digit pairing option via AtomJump’s (AJ) own servers. Some medical institutions require a private ‘proxy’ server to be set up, however. If your system admins have already set this up, and have given you an address for the ‘MedImage Proxy Server’, follow this Installation Guide.

https://github.com/atomjump/medimage-co-nz-content-only/blob/master/SetupInstructionsforMedImage.pdf

## The Proxy Server [Optional]

You can choose this option if you prefer to keep all data transmission privately within your own network, although if this is not a requirement, it is more involved to install this way.

Note: this section requires technical and system administration knowledge.

What you will need: a linux (or Windows) web server with an incoming and outgoing internet connection. Any number of client Windows PCs potentially in different physical premises.

The setup: your server will receive photos over 3G or 4G wireless from your doctor’s mobile phones. The client Windows PCs are associated uniquely with each different mobile phone (via a code generated for each PC). A photo will stay on the proxy server for a few seconds before being downloaded to the doctor’s unique Windows machine, and then being removed from the proxy server.

More details can be found at:
https://github.com/atomjump/medimage-co-nz-content-only/blob/master/technical-guide.md


## Data Transfers

You have three options for transferring data via your phone to your PC

* Via Wifi. This option is free, and very fast, but for security purposes many doctors’ practices do not have a local wifi network set up. The other limitation is that you must be within the vicinity of the network for the transfer to happen.

* Via AtomJump.com’s Secure Servers. This option is easy to set up, and we provide 500MB of initial free transfer. You can purchase unlimited data transfer at a later date, at $US 2 per month (or $NZ 3/month).
Purchase Bandwidth (contact atomjumpcom AT gmail.com)

* Via your own Servers. This option takes a little technical expertise, and is free, although you will have standard bandwidth charges from your hosting providers. You have full control over the security of the servers, using http or https.


## Privacy Policy

MedImage take your privacy and that of your clients very seriously.

Our system is designed from the ground-up to assure security:

* Images can be sent securely by a 3G/4G connection, and over your own networks directly to your computer.
* Images are deleted from your phone once they are received at your computer.
* Web services delete images as soon as receipt is confirmed.
* No image is stored for longer than is required for onward transmission
* Images are transmitted using 256 bit AES encryption.

Our system will not compromise your server:

* Medimage Server will only access computers you specify.
* We do not collect any information from your computer.
* We do not access any medical software on your computer.

How we use your personal information

* We only collect the information we need to manage your account and contact you if we need to.
* Any information we collect is stored in an encrypted archive.
* We will never share your information with any third party.
* You may ask for a copy of any information we hold about you at any time and you have the right to ask us to correct any mistakes.

If you need to contact us about this policy, please email privacy AT atomjump.com (or atomjumpcom AT gmail.com)

We believe AtomJump Ltd. and it’s MedImage product meet the core requirements of the HISO (Health Information Security Framework), from the New Zealand Health Information Standards Organisation. We are currently working towards full Certification.

 

 

## Software License

The app and server are open source, under the Apache 2.0 license and (c) AtomJump Limited (New Zealand).  

http://www.apache.org/licenses/LICENSE-2.0

For commercial add-ons, please read our current license here: 

https://www.binpress.com/license/view/l/a84bbfba8bde4e2da7644e10c6143c45

Non-AtomJump add-ons will have their own licenses.
