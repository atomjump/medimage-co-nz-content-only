<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# MedImage Connection to MedTech Status


We submitted our MedTech32 add-on software for full code review on 12 Feb 2018, and our Evolution version on 2 March 2018, and are awaiting feedback. MedTech themselves have not yet formally authorised our software as a ‘certified’ add-on to MedTech, but we are both working towards that goal.

 

__Q. How does the MedImage MedTech Add-on connection to MedTech32 work?__

Each time a photo is sent to the PC, two queries are run against the MedTech database:

1. A single ‘SELECT’ query to convert the NHID entered into a Patient ID

2. A single ‘INSERT’ query to add one record to the attachments table (attachmentsmgr), with a file level pointer to the photo, and a text description.

All of our queries against the MedTech databases are available for public peer review for both MedTech32 and MedTech Evolution versions. We welcome suggestions and improvements to these from anyone.

https://src.atomjump.com/atomjump/medimage-addon-ehr-medtech32/blob/master/ehrconnect.json
https://src.atomjump.com/atomjump/medimage-addon-ehr-medtech-evolution/blob/master/ehrconnect.json 
 

__Q. Do you have any working installations of your add-on?__

A. Yes, we have multiple installations of the MedTech32 and MedTech Evolution Add-ons working smoothly across New Zealand.

 

__Q. Can I see or change the queries against the MedTech32 database?__

A. Yes, all queries that we run against MedTech are available within the software under the ‘Advanced’ options. All source code is also available for your review.

 

__Q. Does this affect my MedTech service warranty?__

A. If you change the queries in the ‘Advanced’ section, then it may do. For an installation using the queries found during installation, that is question for MedTech, and we are both working towards their review process decision on that matter.  From the MedImage side, we provide full support for your MedTech Add-on software, and we do not expect any adverse effects to MedTech software, or other connecting software.

We also recommend that you ensure any queries run against your database by the MedImage Add-on are run as a different database user (i.e. ‘MEDIMAGE’ rather than ‘SYSDBA’), which should also help to ensure you keep your service warranty. This is explained during installation.

Before installing the MedImage MedTech Add-on, we also recommend backing up your database, which is more for good practice measures, to ensure that there are no unexpected effects on your system.


