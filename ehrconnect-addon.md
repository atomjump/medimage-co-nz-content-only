<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# MedImage EHR Connector


The MedImage EHR Connector Add-on provides the ability to add photos directly from your app into your EHR interface, under the patient’s record.

* Enter the ID number of your patient on the app, and potentially an injury name
* Optionally resize all incoming images down to a smaller size
* Optionally modify the photo file naming scheme
* Future-proofed with editable queries, should your EHR change their data tables
* 10% of our income from this product goes to an ‘AtomJump Medical Open-Source Software Fund’ designed to bring more open source medical products to the market, particularly for the developing world.
* 1 month free trial. If you’re happy with the product, you then pay a one-off license price (split in two 50% installments), for each MedImage Server installation, with no ongoing costs. Any future updates are free.
* For developers, DBAs and system integrators, the software is free.


# Supported EHR software

Note: this Windows-only product is intended for developers and integrators, unless your EHR is mentioned below, in which case you will be able to install your system-specific integration after installation of the package:

* MedTech32
 
EHR Connector
US$ 480 .00
Per Server
EHR Connector
Unlimited Usage
1 Month Free Trial


Warning: this add-on software requires version >= 1.3.8 of the MedImage Server




## Start the Free Trial

http://medimage.co.nz/addon-ehr-connector-download/

Trial terms: Make sure you read the Guide before installation.

If you are happy with the software, please let us know, and we will arrange an invoice. If not, we’re grateful for your feedback.

Note: Prices are in $US. To convert to New Zealand dollars, $US480 = $NZ680.


# Add-on User Guide


	
## Is this the correct package for me?

The EHR Connector provides a standard, relatively user-friendly, way of sending photos from the MedImage app directly into the patient record of many EHR (Electronic Health Record) systems.

However, if your EHR has not already been added to the ‘compatible list’ of systems, you may find it difficult to make this add-on product work for you, depending on your technical level. The standard basic MedImage Server without the EHR Connector may be simpler, which allows you to target the correct folder for your photos to go, but still requires you to manually add the photo through your EHR interface to the particular patient.

As __an end-user__, with the EHR Connector, you have some options:

1. Write your own EHR specific queries (which takes some ‘SQL query’ ability)

2. Employ MedImage, or a 3rd party, to remotely log into your system and determine the correct set of queries for your EHR system.

3. Request your EHR developers to write the SQL queries for you, and build an add-on package for general use.

 

If you’re a __developer or system integrator__ you have several options, also:

1. If the target EHR system has

    an accessible database, and you can make ‘ODBC queries’ against the database,
    a patient’s photo ‘local file path’ field in one of the data tables

then making a working connection will be fairly straightforward with this EHR Connector, as you will only need to determine 3 different SQL queries. If you want to publish the connection for others to use, you can duplicate this open source project and replace the 3 queries above, along with providing the relevant ODBC driver for the database.

2. If you want more control over the connection, or you want to build other functionality, you can make your own general purpose MedImage add-on using the MedImage Open Developer API.

 
## Installation

You will need to install the MedImage Server version ( >= 1.3.8), and for testing purposes, we would recommend trying this on a test server or PC, first, to check everything works in your environment. Please back-up your EHR database before first use – this add-on shouldn’t adversely affect anything, but it is always a safe policy. We would recommend doing this process out-of-hours, so that no users are currently accessing the system, but that depends partly on the type of EHR you have.

Once the MedImage Server is installed, you should download and install the EHR Connector add-on from

http://medimage.co.nz/addon-ehrconnect/

To download this, click ‘Start the Free Trial’ from that page – it will take you to the download section.

You can download both the Server software and the EHR Connector add-on as many times as you need to run it on your system. If you don’t find it works in with your set-up, please let us know and we’ll see how we can help. MedImage support is available if you need on-site or remote assistance in installing this. Please remember that the license is per hardware server, so you will need to purchase a new copy if you plan on running the software on a new site.
Post Installation Set-up

Once the installation is complete you should install your specific EHR add-on e.g. ‘MedTech32’ from the same page. If your EHR is not on the list, you will still be able to change the EHR queries to match your situation, although this takes some technical ability.

The MedImage Server software will pop up in a browser with the MedTech32 add-on settings page showing.

If your queries have not been set up for your specific type of EHR (i.e. you have not installed a specific EHR add-on), your should re-write these in the ‘Advanced options’ section, before going any further.

Scrolling down further:

The general approach here is to configure, ‘Save & Check connection’, configure, ‘Save & Check connection’, etc. until you have a green ‘Connection Success’ message showing.

 

You can preview the ‘Show Extended options’ in this picture, and the ‘Advanced Options’ in this picture.

 

## Setting up ODBC

You need to create a ‘system’ DSN connection to your EHR database through the Windows ODBC page (enter ‘ODBC’ under your Windows start bar). Make sure you use the 64-bit version or the 32-bit version, depending on the database software installed. There are instructions for specific fields in the MedImage add-on settings page under the ‘ODBC Guide’ link. Test the connection within the ODBC driver to ensure it is working. Then add the name of your ODBC connection back into your MedImage MedTech32 settings page. Save and check the connection once more.

Once you have successfully connected to your MedTech32 database you are ready to try sending images from your MedImage phone app to your EHR.
Using the app

The app can be used in much the same manner as you would without the add-on installed, but you should be aware of the following:

The preferred format to enter is ‘#[Patient ID] [injury name]’, for example ‘#BGDH1233 arm’, or if you have the app option ‘ID writes a folder’ on, you can ignore the ‘#’ at the start and enter simply e.g. ‘BGDH1233 arm’.

This will create a folder for each patient ID, and include multiple photos within it. While it is possible to modify this recommended structure (under the ‘Advanced Options’), you will need to be technically capable to do so (i.e. have a knowledge of, or the aptitude to learn about ‘regular expressions’).

Once a photo has been sent, you should initially check the status of the photo transfer in the MedImage Server interface, under the ‘EHR Log’ link on the left-hand-side. This page provides an up-to-date log of success or failure, that is refreshed every few seconds. It can take a few seconds from when the app mentions the photo has transferred successfully, to the entry getting displayed here.

 

## Please note:

* You cannot send a photo to an ‘inactive’ patient ID
* If a patient ID number is duplicated, this will return an error, and you will need to manually add the photo to your EHR
* If nothing appears at all on this log, please check your internet connection from your server

Once you have a green ‘success’ message on this log, you typically wouldn’t need to keep referring to the log page (unless you find a photo has not arrived, of course).

You then need to close and re-open the record for that patient, from within your EHR interface. The new photo should be visible, and clickable. E.g.

Developers: Building Your Own

To create your own EHR connection package, use this project as a template. The only files you will need to change are:

1. ehrconnect.json

Which should include queries specific to your database  and system tables. Make sure you have valid JSON (use an online json validator)

2. odbc\*

The ODBC driver .exe or .msi that your database requires should be in here

3. medimage-installer.json

You should change the install commands to install your ODBC driver file silently

Once you have changed the files, you should .zip the project up (we recommend a Windows machine for this as the Mac zip format is sometimes incompatible), and make it accessible to your users to install on the internet via the MedImage Server Add-on installer. MedImage are always happy to add newly compatible EHR projects to our own list, also.

 

An example ehrconnect.json file

```
{
    "photoPathMatch": "(.*)\\\\(.*)\\\\(.*).jpg",
    "photoVars": ["parentphotodir", "NHID", "photoname"],
    "testConnectionSQL": "SELECT * FROM ATTACHMENTSMGR ORDER BY WHENADDED DESC ROWS 1;",
    "testConnectionShowField": "PATHTOFILE",
    "createUserSQL": "GRANT ALL ON ATTACHMENTSMGR TO MEDIMAGE; GRANT SELECT ON PATIENT TO MEDIMAGE; GRANT SELECT ON ANYBODY TO MEDIMAGE;",    
    "getIdSQL": "SELECT ANYBODYANY.ANYBODYID AS ANYBODYID FROM PATIENT ANYBODYPAT LEFT JOIN ANYBODY ANYBODYANY ON ANYBODYANY.ANYBODYID = ANYBODYPAT.PATIENTID WHERE ANYBODYANY.ROWINACTIVE = 0 AND ANYBODYPAT.NHINO = '[NHID]';",
    "insertAttachmentSQL": "INSERT INTO ATTACHMENTSMGR (ANYBODYID, WHENADDED, DESCRIPTION, NOTE, PATHTOFILE, FILESIZE, ROWINSERTWHEN, ROWINSERTSTAFF, ROWINSERTCOMPUTER, ROWINSERTLOCATION, ROWEDITWHEN, ROWEDITSTAFF, ROWEDITCOMPUTER, ROWEDITLOCATION, ROWINACTIVE, EXTRACONVERSIONDATA) VALUES ('[patientID]','[currentDateTime]','[photoname]','','[fullphotopath]',[filelength],'[currentDateTime]','[staffname]','[computer]','[location]','[currentDateTime]','[staffname]','[computer]','[location]',0,NULL);",
    "host": "localhost",
    "dbname": "C:\\MT32\\data\\MT32.ib",
    "username": "SYSDBA",
    "password": "masterkey",
    "staffname": "#sys",
    "computer": "",
    "location": "M",
    "useResized": false,
    "parentPhotoDir": "C:\\MT32\\Attachments",
    "useODBC": true,
    "dsnHere": "medtech32",
    "logging": true,
    "capitaliseNHID": true,
    "dbCurrentTimeSQL": "CURRENT_TIMESTAMP" 
}
```

The most crucial fields that need to be altered are testConnectionSQL, testConnectionShowField, createUserSQL, getIdSQL, insertAttachmentSQL and dbCurrentTimeSQL.

* __testConnectionSQL__. Connection test query. SQL command to check the connection to the EHR database and get the last photo record added.

* __testConnectionShowField__. Connection test field to highlight. The table field name to show for the last record entered, once there is a successful connection test.

* __createUserSQL__. Give MEDIMAGE user permissions queries. SQL command(s) to give the ‘MEDIMAGE’ user it’s permissions. Separate queries by semi-colons ‘;’. This helps differentiate who should support any associated problems.

* __getIdSQL__. Get identifier query. SQL command to output the internal database patient ID from an incoming [NHID] word.

* __insertAttachmentSQL__. Insert attachment query. SQL command to insert the new photo attachment into the patient record table. Words that are replaced with their correct values are ‘patientID,currentDateTime,photoname,fullphotopath,filelength,staffname,computer,location’

* __dbCurrentTimeSQL__. Database Current time. SQL function representing the current time field. This may be e.g. ‘CURRENT_TIMESTAMP’.

 

An example medimage-installer.json file, which is documented here under the ‘Writing and Add-on installer’ heading.

```
{
  "author": "AtomJump.com",
  "name": "ehr-medtech32",
  "description": "MedTech32 config for EHR Connector Add-on for MedImage",
  "version": "0.0.1",
  "private": false,
  "license": "MIT License",
  "installCommands": {
       "all": [
             "npm install",
              "node install.js first"
        ],
        "win32": [
              "C:\\medimage\\addons\\ehr-medtech32\\odbc\\odbcibinstall.exe /S"
        ],
        "win64": [
              "C:\\medimage\\addons\\ehr-medtech32\\odbc\\odbcibinstall.exe /S"
        ],
        "unix": [
        ],
        "mac": [
             
        ]
  },
   "uninstallCommands": {
       "all": [
              "node uninstall.js"
        ],
        "win32": [
        ],
        "win64": [
        ],
        "unix": [
        ],
        "mac": [
        ]
  }
}
```


