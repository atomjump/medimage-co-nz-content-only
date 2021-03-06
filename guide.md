<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Guide


## The App

This app allows the medical professional to upload a photo and ID from their phone of a patient’s case e.g. a mole, and transfer the image directly to the patient’s file on their PC. The app is currently available for Android, and iOS iPhone/iPad. Each doctor will need an app for their own phone, and can also be found by searching the App Store for ‘medimage’, or ‘medimage atomjump’.

See the ‘How To’ guide, the ‘How does it work?’ section, or the FAQ for further tips.

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/how-to.md

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/how-does-it-work.md

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/faq.md


## The PC Server

In order for you to receive the photos from your phone, you need to download a companion server to your PC. This server has a straightforward installer ready for Windows machines. You can test this out directly, without any technical knowledge, if you have a Wifi connection shared between your PC and your phone. If you wish to use the internet only, you can choose an easy 4 digit pairing option via AtomJump’s (AJ) own servers. Some medical institutions require a private ‘proxy’ server to be set up, however. If your system admins have already set this up, and have given you an address for the ‘MedImage Proxy Server’, follow this Installation Guide.

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/SetupInstructionsforMedImage.pdf

## The Proxy Server [Optional]

You can choose this option if you prefer to keep all data transmission privately within your own network, although if this is not a requirement, it is more involved to install this way.

Note: this section requires technical and system administration knowledge.

What you will need: a linux (or Windows) web server with an incoming and outgoing internet connection. Any number of client Windows PCs potentially in different physical premises.

The setup: your server will receive photos over 3G or 4G wireless from your doctor’s mobile phones. The client Windows PCs are associated uniquely with each different mobile phone (via a code generated for each PC). A photo will stay on the proxy server for a few seconds before being downloaded to the doctor’s unique Windows machine, and then being removed from the proxy server.

More details can be found at:
https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/technical-guide.md


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

For commercial add-ons, our current license is: 
For our commercial add-ons, please read our current license here:

* You may use this software as-is, and browse the source code as-is for educational purposes, but cannot resell the product independently, unless you pay the license price to AtomJump Limited in New Zealand.
* Each instance of the MedImage Server typically requires the purchase of a license of the add-on for that server. E.g. if you have 20 different branches, each with one installation of the MedImage Server, you would need to purchase 20 licenses.
* Note: the intention of this license is that it would be functional for one GP practice of around 5 – 10 users. If you are using a cloud-based system where you service multiple practices, then you will need a license for each practice, or an agreed ‘cloud usage’ type license from AtomJump. Please contact us to arrange a specific agreement. If you are using the MedImage Server for each desktop, then please contact us to arrange a more cost-effective agreement, also.
* We offer technical assistance including networking, secure domains, maintenance and installation, at an agreed price, on a case by case basis.
* Most of our larger add-ons have a 30 day trial period where you can ensure that the software is working as expected. There is no time limit on usage of the add-on once purchased, and future updates are free, unless we are involved in their installation, or there is a particularly major change to the product.
* You may include the product in your own package, provided the correct number of licenses are purchased from AtomJump Limited in New Zealand, so we will need to see some evidence that you are calculating the quantity sold.
* Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an “AS IS” BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

Non-AtomJump add-ons will have their own licenses.
