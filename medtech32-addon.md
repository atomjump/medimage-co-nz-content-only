<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.



# MedTech32 MedImage Add-on

The MedTech32 MedImage Server Add-on provides the ability to add photos directly from your app into the MedTech32 interface, under the patient’s ‘Attachments’ section.

* Enter the NHI number of your patient on the app, and potentially an injury name
* Optionally resize all incoming images down to a smaller size
* Optionally modify the photo file naming scheme
* Choose which MedTech database to access
* Future-proofed with editable queries, should MedTech32 change their data tables
* 10% of our income from this product goes to an ‘AtomJump Medical Open-Source Software Fund’ designed to bring more open source medical products to the market, particularly for the developing world.




# Add-on User Guide


## Installation

You will need to install the MedImage Server version ( > 0.8.1), and for testing purposes, we would recommend trying this on a test server or PC, first, to check everything works in your environment. Please back-up your MedTech database before first use – our add-on shouldn’t adversely affect anything, but it is always a safe policy. You can do a file-level back-up, and we would recommend doing this process out-of-hours, so that no users are currently accessing the MedTech32 system.

## Once the MedImage Server is installed, you should download and install the MedTech add-on from

http://medimage.co.nz/addon-medtech32/

To download this, register to purchase from that page – it will give you a 30-day free trial, and take you to the download section.

You can download both the Server software and the MedTech add-on as many times as you need to run it on your system. If you don’t find it works in with your set-up, you can cancel the Paypal dual-payment ‘subscription’  at any time within the 30 day period. MedImage support is available if you need on-site or remote assistance in installing this. Please remember that the license is per hardware server, so you will need to purchase a new copy if you plan on running the software on a new site.

## Post Installation Set-up

Once the installation is complete the MedImage Server software will pop up in a browser with the MedTech32 add-on settings page showing.

The general approach here is to configure, ‘Save & Check connection’, configure, ‘Save & Check connection’, etc. until you have a green ‘Connection Success’ message showing.


Be careful of:

* If the MedImage add-on settings for ‘Show Identifier Options/Location’ are set to ‘M’, by default, the photos will only be visible when you click the link within MedTech32 on client PCs, not the server itself (since the file reference will be from M:\Attachments\…). However you can work around this:

1. You can switch the ‘Location’ setting in MedImage to ‘C’ on a single machine installation of MedTech32
2. Or, on the server you can run the following in a cmd prompt: ‘subst M: C:\mt32’

* If the standard ‘native’ connection does not work when connecting to your MedTech Interbase database, you should try to connect via the ODBC connection method. There is no difference in the end-result, but the ODBC method is simply more involved to set up.  There are several different ODBC drivers on the market that work with Interbase, and you will need one of them installed. The only non-commercial option we have found comes from Embarcadero themselves, and modern-day Interbase installations provide the ODBC driver as an option during the installation process, so you may already have the Interbase ODBC driver installed. If not, you will need to login to https://www.embarcadero.com/products/interbase with your account, or create a new account with them and download & install their ODBC driver software. Make sure the ODBC driver matches your Interbase version.
* Once this ODBC driver is installed, you need to create a ‘system’ DSN connection to your MedTech32 database through the Windows ODBC page (enter ‘ODBC’ under your Windows start bar). Make sure you use the 64-bit version or the 32-bit version, depending on the Interbase software installed. There are instructions for specific fields in the MedImage add-on settings page under the ‘ODBC Guide’ link.  Test the connection within the ODBC driver to ensure it is working. Then add the name of your ODBC connection back into your MedImage MedTech32 settings page. Save and check the connection once more.

Once you have successfully connected to your MedTech32 database you are ready to try sending images from your MedImage phone app to MedTech32.


## Using the app

The app can be used in much the same manner as you would without the add-on installed, but you should be aware of the following:

The preferred format to enter is ‘#[NHID number] [injury name]’, for example ‘#BGDH1233 arm’, or if you have the app option ‘ID writes a folder’ on, you can ignore the ‘#’ at the start and enter simply e.g. ‘BGDH1233 arm’.

This will create a folder for each NHID number, and include multiple photos within it. While it is possible to modify this recommended structure (under the ‘Advanced Options’), you will need to be technically capable to do so (i.e. have a knowledge of, or the aptitude to learn about ‘regular expressions’).

Once a photo has been sent, you should initially check the status of the photo transfer in the MedImage Server interface, under the ‘MedTech Log’ link on the left-hand-side. This page provides an up-to-date log of success or failure, that is refreshed every few seconds. It can take a few seconds from when the app mentions the photo has transferred successfully, to the entry getting displayed here.

 
Please note:

* You cannot send a photo to an ‘inactive’ NHID number
* If an NHID number is duplicated, this will return an error, and you will need to manually add the photo to MedTech
* If nothing appears at all on this log, please check your internet connection from your server

Once you have a green ‘success’ message on this log, you typically wouldn’t need to keep referring to the log page (unless you find a photo has not arrived, of course).

You then need to close and re-open the ‘Attachments Manager’ for that patient, from within MedTech32. The new photo should be visible, and clickable.


