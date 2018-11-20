<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# MedImage EHR Connector Fields

## Resize Options
The Resize Options are available on a separate ‘Resize’ tab inside the MedImage Settings.

__Width__

In pixels, or ‘auto’ to keep aspect ratio of original, based off the height

__Height__

In pixels, or ‘auto’ to keep aspect ratio of original, based off the width

__Quality__

Of the resized image, as a percentage 0 – 100 (Tip: high quality = more storage)

__Photo filename text to replace..__

The part of the filename to rename e.g. ‘.jpg’

__.. with this__

What to rename the above field’s contents to in the filename e.g. ‘-small.jpg’. Note: if you enter this as the same as the field above i.e. ‘.jpg’, then the resize photo will replace the original photo, which is a useful way to save disk space (if you don’t need the original quality photo).

__Resize Photos__

Switch this on to process and include a resized photo in your Windows folder. To actually insert the photo in your EHR system, please check the EHR Connector tab, under Basic Options / Insert Original Photo and Insert Resized Photo.

 

EHR Connector Basic Options
ODBC Database ‘System DSN’ name

E.g. ‘medtech32’. You will find these by searching for ‘ODBC’ in the general Windows search at the bottom of your Windows desktop screen. [Code Field: dsnHere]

Database Host

This is typically ‘localhost’, or e.g. ‘localhost:1234’, but could be any network address. [Code Field: host]

Database Name

The database name for your EHR installation. [Code Field: dbname]

Username

Your system-wide database or connection username. If this is a database connection, after a successful connection you would often create a new MedImage-specific user to avoid invalidating any EHR support warranties. [Code Field: username]

Password

Your database or connection password. [Code Field: password]

Photo Folder

The MedImage server location for your photos. E.g. c:\mt32\attachments. These will be predefined by your MedImage Server target folder settings. [Code Field: parentPhotoDir]

Insert Original Photo

Whether to include a new link/entry into the patient record of your EHR system to the original photo, or not. [Code Field: useOriginal]

Insert Resized Photo

Whether to include a new link/entry into the patient record of your EHR system to the resized photo, or not. If this is ticked, you must also tick ‘Resize Photos’ to ‘On’ in the Resize tab. [Code Field: useResized]

 

Extended Options
Local Map Down Folder 

Folder path that gets replaced when the Drive letter is changed below. E.g. when this is set to ‘C:\mt32\’, a photo at C:\mt32\… would become M:\…  [Code Field: localFolderMapDown]

Maps Down To

Folder that replaces the folder path above when added to the EHR database. Useful if you use a ‘mapped’ network drive. [Code Field: mapDownTo]

Location

Short description of the location. [Code Field: location]

Staff Name

Identifies the staff member who has added the attachment, but will be the same for all MedImage photos. [Code Field: staffname]

Computer

Identifies which computer has added the attachment, but will be the same for all MedImage photos. [Code Field: computer]

Auto-capitalise the Patient ID

Will turn the patient ID entered (actually the last folder created) into a capitalized version. This prevents different users from entering different versions of the ID and the system creating different Windows folders. [Code Field: capitaliseNHID]

 

Advanced Options
Request Style

Use a direct database connection (SQL), a SOAP XML type connection (SOAP XML), or JSON POST request (JSON). Your configuration should have been set automatically if you have a known EHR system. [Code Field: requestType]

Connection Style

Use an ODBC connection, or you can use a ‘native’ SQL Server connection, if that is your database. [Code Field: useODBC]

HTTP Method

Do a GET or POST http(s) request. [Code Field: httpMethod]

Photo file path match

Regular expression that splits a photo path up into components. Use double back-slashes for folder breaks i.e. ‘\\’, and (.*) for each component. [Code Field: photoPathMatch]

Order of components in path

Take each component from the ‘Photo file path match’ expression above, and replace them in this order. Separate with commas. Standard component names are ‘parentphotodir’, ‘NHID’, ‘photoname’. [Code Field: photoVars]

Connection test query

Query command to check the connection to the EHR database and get the last photo record added. SQL or SOAP XML. [Code Field: testConnectionQuery, or < v0.7.10, testConnectionSQL]

Connection test field to highlight

The table field name to show for the last record entered, once there is a successful connection test. [Code Field: testConnectionShowField]

Give MEDIMAGE user permissions queries

Query command(s) to give the ‘MEDIMAGE’ user it’s permissions. SQL or SOAP XML. Separate SQL queries by semi-colons ‘;’. This helps differentiate who should support any associated problems. [Code Field: createUserQuery, or < v0.7.10, createUserSQL]

Get identifier query (Optional)

Query command to output the internal database patient ID from an incoming [ID] word. SQL or SOAP XML. The [ID] is replaced with the first word entered in the app. You should return the patient ID in SQL as PATIENTID e.g. SELECT [your field] AS PATIENTID FROM … [Code Field: getIdQuery]

Insert attachment query

Query command to insert the new photo attachment into the patient record table. SQL or SOAP XML. Words that are replaced with their correct values are ‘patientID,currentDateTime,photoname,fullphotopath,filelength,staffname,computer,location’ [Code Field: insertAttachmentQuery, or < v0.7.10, insertAttachmentSQL]

Database Current time

Query function representing the current time field. SQL or SOAP XML. This may be e.g. ‘CURRENT_TIMESTAMP’. This is useful to tell the database when the entry was added. [Code Field: dbCurrentTimeQuery, or < v0.7.10, dbCurrentTimeSQL]

Error Notification URL

A notification URL that is called when there is an error. For example, the script at the URL may email the practice admin with the error. Include the text [MESSAGE] in the URL to be replaced with the actual error message. [Code Field: errorNotificationURL]

Log Results

Switch on and off logging of each photo taken. You will find the log files at C:\MedImage\addons\ehrconnect\log\ehr_connect.log and C:\MedImage\addons\ehrconnect\log\ehr_connect_full.log. The basic log shows a success/error message, while the full log shows queries run behind the scenes and other processing on each photo. [Code Field: logging]

 

Endpoint SOAP/JSON Options (ver >= 0.7.10)
Check connection endpoint

URL Endpoint to do a check that the connection to the EHR system is working [Code Field: testConnection]

Get identifier endpoint (Optional)

URL Endpoint to get an internal identifier from an external public-facing identifier. E.g. ‘NHI1234’ returns a system-level patient ID of ‘4245467’. Use [ID] in the URL to be replaced with the actual ID entered, e.g. https://localhost/?id=[ID].  [Code Field: getId]

Insert attachment endpoint

URL Endpoint to insert a photo record. Words that are replaced with their correct values are [patientID],[currentDateTime],[photoname],[fullphotopath],[filelength],[staffname],[computer],[location],[sessionID].  [Code Field: insertAttachment]

Include the photo in the insert attachment request

This will do a mult-part POST request, with the photo file attached along with the photo record request. [Code Field: includePhotoInPOST]

SSL Certificate File

Local file path for SSL .pem certificate file. [Code Field: sslCertFile]

Timeout Failure Period

In milliseconds e.g. 2000 = 2 seconds. [Code Field: timeoutFailureMs]

HTTP Headers

HTTP Headers in JSON array format. The text [soapEndpoint] will be replaced with the endpoint used above, and [contentLength] will be replaced with the length of the content being sent. [Code Field: headers]

 

Response SOAP/JSON Options (ver >= 0.7.10)
Test Connection Success

Object to check for success from a SOAP/JSON response e.g. id.success  [Code Field: testConnection.success]

Test Connection Success Value

Value to check for success from the above parameter e.g. true  [Code Field: testConnection.successValue]

Get ID Success (Optional)

Object to check for success from a SOAP/JSON response e.g. id.success  [Code Field: getId.success]

Get ID Success Value (Optional)

Value to check for success from the above parameter e.g. true [Code Field: getId.successValue]

Get ID Returned Value (Optional)

Returned object that holds the ID itself e.g. id.value [Code Field: getId.returnedValue]

Get ID Session Value (Optional)

Returned object that holds an optional session ID, valid for the following requests in this session e.g. id.session  [Code Field: getId.sessionValue]

Get ID Determine a Duplicate (Optional)

Object to check to determine there is a duplicate of this input ID, from a SOAP/JSON response e.g. id.duplicate  [Code Field: getId.duplicate]

Get ID Duplicate Value (Optional)

Value to check for from the above object parameter e.g. ‘true’, to determine a duplicate.  [Code Field: getId.duplicateValue]

Insert Attachment Success

Object to check for success from a SOAP/JSON response e.g. id.success  [Code Field: insertAttachment.success]

Insert Attachment Success Value

Value to check for success from the above parameter e.g. true  [Code Field: insertAttachment.successValue]

 

SOAP/XML Sample
The following example can be found in full at https://github.com/atomjump/medimage-addon-ehr-soaptest.

An example SOAP XML connection:
```
{
	"photoPathMatch": "(.*)\\\\(.*)\\\\(.*).jpg",
	"photoVars": ["parentphotodir", "NHID", "photoname"],
	"testConnectionQuery": "10",
	"testConnectionShowField": "",
	"createUserQuery": "",	
	"getIdQuery": "",
	"insertAttachmentQuery": "10",
	"host": "localhost",
	"dbname": "C:\\MT32\\data\\MT32.ib",
	"username": "SYSDBA",
	"password": "masterkey",
	"staffname": "#sys",
	"computer": "",
	"localFolderMapDown": "C:\\mt32\\",
	"mapDownTo": "M:\\",
	"location": "M",
	"useResized": false,
	"useOriginal": true,
	"parentPhotoDir": "C:\\MT32\\Attachments",
	"useODBC": true,
	"requestType": "soap",
	"endPoints": {
		"testConnection": "http://www.dataaccess.com/webservicesserver/NumberConversion.wso",
		"getId": "",
		"insertAttachment": "http://www.dataaccess.com/webservicesserver/NumberConversion.wso",
		"includePhotoInPOST": false,
		"httpMethod": "POST",
		"ssl": true,
		"sslCertFile": "",
		"timeoutFailureMs": 2000,
		"headers": [ "Content-type: text/xml;charset=\"utf-8\"",
                       "Accept: text/xml",
                        "Cache-Control: no-cache",
                        "Pragma: no-cache",
                        "SOAPAction:", 
                        "Content-length: [contentLength]" ]
	},
	"responseObjects": {
		"testConnection": {
			"success" :	"Body.NumberToWordsResponse.NumberToWordsResult",
			"successValue": "ten "	
		},
		"getId": {
			"success" :	"",
			"successValue": "",
			"returnedValue" : "",
			"duplicate" : "",
			"duplicateValue": ""
		},
		"insertAttachment" :{
			"success" :	"Body.NumberToWordsResponse.NumberToWordsResult",
			"successValue": "ten "
		}
	},		
	"dsnHere": "medtech32",
	"logging": true,
	"capitaliseNHID": true,
	"dbCurrentTimeQuery": "",
	"constraints": {
		"patientID": 7,
		"photoName": 100,
		"staffname": 4,
		"computer": 15,
		"location": 1,
		"fullphotopath": 255	
	},
	"createUserHelp": "",
	"createUserHelpFull": "",
	"odbcUserHelp": ""
	
	 
}
```
