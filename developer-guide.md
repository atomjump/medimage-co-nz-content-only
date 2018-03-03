
<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Developer's Guide



## Introduction

The MedImage tool now includes a developer interface to build new add-ons.  Add-ons are useful for acting on the photos that appear on the PC or server, by adding them to a wide variety of systems, or your own system.

For example, our first add-on is a ‘Wound Analysis’ tool, that auto-detects wound area sizes, and a ‘MedTech’ add-on has been released that will append photos directly into the MedTech interface.  Similar tools can be built (and independently sold) for different medical database systems, provided you have the development skills.

 
There is no cost in building or publishing an add-on, although we cannot guarantee that we will highlight your add-on on medimage.co.nz.

Since MedImage is an open-source platform, we believe it will have a stable future.

 

## Getting Started

At the current time, i.e. 2 Dec 2017, download the MedImage Server 1.3.3. Or for non-Windows installations, use the ‘git clone’ approach to get the latest server. i.e

```
git clone https://github.com/atomjump/medimageserv.git
cd medimageserv
npm install
node bin/server.js
```

The ‘master’ branch has the latest server that includes the add-on capability.

Server add-ons can be written in any language, and are run off the command-line as an external process.  These are run after certain events within the main server. Note: NodeJS is the only guaranteed language to exist on all installations of MedImage Server, so this is the preferred language for add-ons, but it is not a requirement. With NodeJS, you can also embed your add-on modules directly into the main MedImage server (>= ver 1.3.3), so this gives a large performance improvement. On Windows, the server has version 4.2.6 of NodeJS.

An add-on exists in the /addons/ folder in a MedImage Server installation ( >= ver 0.8.1). In this folder is a config.json file, which should be written to as your add-on’s installation occurs, with your add-on’s new event entries. A customer may have other add-ons already installed, so it is best not to overwrite this file.  Here is a sample add-ons config.json:

```
{
	"events": {
		"photoWritten": [
				{
					"addon": "Wound Analysis",
					"runProcess": "node parentdir/addons/wound/wound-size.js param1",
					"active": true
				},
							{
					"addon": "MedTech",
					"runProcess": "",
					"active": false
				}			
		],
		"urlRequest": [	
		
			   {
					"addon": "change-folder",
					"scriptURLName": "change-folder-set",
					"runProcess": "node parentdir/addons/change-folder/set-folder.js param1",
					"priority": "medium",
					"waitForRequestFinish":  "addon-settings.html",
					"active": true
				},
				{
					"addon": "change-folder",
					"scriptURLName": "change-folder-view-settings",
					"runProcess": "node parentdir/addons/change-folder/view-settings.js",
					"priority": "medium",
					"waitForRequestFinish":  "change-folder-settings.html",
					"active": true
				},
				{
					"addon": "install-addon",
					"scriptURLName": "install-addon",
					"runProcess": "node parentdir/addons/addon-installer/install-addon.js param1",
					"priority": "glacial",
					"waitForRequestFinish":  "addon-settings.html",
					"active": true
				},
				{
					"addon": "install-addon",
					"scriptURLName": "addon-installer-view-settings",
					"runProcess": "node parentdir/addons/addon-installer/view-settings.js",
					"priority": "medium",
					"waitForRequestFinish":  "install-addon-settings.html",
					"active": true
				},
				{
					"addon": "current-log",
					"scriptURLName": "current-log",
					"runProcess": "node parentdir/addons/log-viewer/view-log.js",
					"priority": "medium",
					"waitForRequestFinish":  "view-log.html",
					"active": true
				}
		
		]
	}
}
```

 

## Events

__photoWritten:__ this occurs as soon as a new photo has been written. ‘param1’ will have the absolute path of the new photo written in the /photos folder (note: not the backed up file).

__urlRequest:__ this occurs when there is a particular URL requested from the MedImage server’s web server.

 

## Event sub-parameters

__scriptURLName__ is the path. E.g. ‘grab-colour’ will be activated when the url ‘/addons/grab-colour/’ is called.

__runProcess__ is a unix or Windows command-line that runs a process. Make sure it will run on whichever platform(s) your add-on supports. You can safely assume that NodeJS will be installed on all target installations. The parameters will come inwardly as ‘param1’, which is exactly what comes after e.g. ‘/addons/grab-colour/’ in the URL line. Typically this would be a urlencoded array of GET parameters e.g. ‘?test1=value&test2=value2’, although it could also be a single string e.g. for the URL ‘/addons/grab-colour/a-nice-file.jpg’, param1 would be set to ‘a-nice-file.jpg’.  The constant ‘parentdir’ should be used at the start of a path to represent the MedImage parent folder.

__priority__ determines how urgent the request is. Options are ‘high’,’medium’, ‘low’, ‘glacial’.

‘high’ will embed the command in the main server code itself for maximum running speed, so it should start with ‘node’ e.g.

node parentdir/addons/change-folder/set-folder.js param1
See the ‘Embedding’ section below for tips for embedding code within the package.

‘medium’ priority will run the script as a process on your operating system, without a shell in the background. It should be in the format ‘command param1 param2’.

‘low’ priority will run the script inside a shell of the operating system, which adds overhead, but you can include a more complete list of operating system commands e.g. piping, etc, although be careful to make this work across all your target Add-on platforms.

‘glacial’ priority will run the script in the same manner as ‘medium’ but runs the process in the background in a non-resource hungry way. Use this for background installers or long processes.

__waitForRequestFinish__ is the HTML page to call after this script has finished. This HTML page should be installed in the MedImage server’s ‘/public/pages/’ during your add-on’s installation process.

Your script can pass back return parameters to the ‘waitForRequestFinish’ HTML file, for string inclusion in the HTML pages, by writing to standard output. In NodeJS you would console.log() something like:

```
console.log("returnParams:?your-param=data&your-param2=data2");
```

You can print out other messages before this in your script, so this line should be at the end of the script.  In this case, the string ‘your-param’ and ‘your-param2’ would be replaced with data and data2 within the HTML file that was run afterwards. Note: as of ver 0.8.1, you must include a ‘returnParams’ message, for the ‘standardheader’ to be inserted in this HTML page. This requirement may no longer be there in future versions.

__active__ can be switched on or off with ‘true’ or ‘false’ depending on whether you want the functionality working currently.

__afterRequest__: Alternatively to ‘waitForRequestFinish’, if it is a blind script which doesn’t need to pass other parameters back, in your config file, you can use

```
"afterRequest":"your.html.page.here.html"
```

to forward the browser to the HTML page immediately.

__useTargetFolderFile__: (>= v1.4.1) If you include this parameter in a ‘photoWritten’ event, set to ‘true’, your script will be passed the file in the target folder file (i.e. the 1st entry in the backupTo array within C:\medimage\config.json), after it has already been copied there, instead of the transition folder. This is useful when chaining multiple add-ons together, and processing the last photo after it has been copied to the final output folder.

 

## Getting a photo file

You can also get URL access to the photo files with your add-ons, but please be cautious about the security of this. You should provide a login facility, or restrict access to the server through network firewalls. Put this at the end of your script:

```
console.log("returnPhotoFile:../../photos/NHI3443/blister-12-Aug-2017-16-49-30.jpg");
```

to return the photo file as uploaded via the MedImage app, in the folder NHI3443 and named blister. Keep your “waitForRequestFinish” in the add-on’s config file as a blank string in this case (include it, but don’t fill the contents).

 

## Including JSON and/or small snippets of AJAX code

To return a small snippet of JSON from your add-on’s scripts, set the ‘waitForRequestFinish’ to be ‘snippet.html’, and pass the parameter CUSTOMJSON into it with e.g.

```
console.log("returnParams:CUSTOMJSON=" + encodeURIComponent(JSON.stringify(resp)));
``` 

 

## Changing the menu

During installation you should append to the file within the MedImage Server installation called

components/header.html

and add another ‘li’ element to the ‘side-menu’ entry e.g.

```
 <li>
     <a href="http://myurl.com"><i class="fa fa-check-square-o fa-fw"></i> My Menu Item</a>
 </li>
 ```

Including your own HTML layouts

You will find all of the Bootstrap code for a nice visual appearance to your add-on in the /public/pages/buttons.html collection of files. Run these in your browser and investigate the code behind them i.e.

```
http://localhost:5566/public/pages/buttons.html
```

You can insert your own code snippets by creating a ‘run-process’ entry in your addons/config.json, which passes back code in the parameters to the ‘waitForRequestFinish’ HTML page entry.

Note: the standard header is available to any HTML page, and is embedded with ‘STANDARDHEADER’.  This includes jQuery, jQuery UI interface, and Bootstrap.

 

## Backing up any created files

Most user’s installations will store the photo files in two places, the original MedImage /photos folder, and a target folder of their choice. To include any files or photos that your add-on has created within the /photos folder, you can write the following command to STDOUT:

```
backupFiles:/absolute/path/file1.ext;/absolute/path/file2.jpg
```

Note: this line should come before any final ‘returnParams:’ line. You can back up multiple files by separating the filenames with semi-colons i.e. ‘;’. The path should be absolute, but the file should be in the MedImage /photos folder.

If you have renamed your file in your add-on, you should pass back (Only supported in ver >= 1.0.7)

```
backupFileRenamed:/absolute/path/file1.ext
``` 


## Reloading the configuration file (ver >= 1.0.7)

After your script ends you can request a reload of the configuration file by the master server. Include the line

```
reloadConfig:true
```

in the output of the script (before the ‘returnParams:’ line.

 

## Writing an Add-on Installer (ver >= 1.3.4)

You have two options – writing a custom Windows (or other) operating system-level installer, or, packaging your content in a .zip file package and using the Add-on Installer from within the MedImage Server.

Within a .zip package (which is easier to develop and test), you should include the ‘medimage-installer.json’ file.

```
{
  "author": "AtomJump.com",
  "name": "resize",
  "description": "An add-on to MedImage Server that automatically resizes images after they appear on the PC",
  "version": "0.2.3",
  "private": false,
  "license": "Commercial",
  "successMessages": {
      "all": {
          "main": "Your installation was successful. You should now configure your settings. Click the 'Resize' tab to get started.",
          "extended": ""
      },
      "win32": {
          "main": "Some specific Win32 message in here, will override the 'all' message"
      }
  },
  "installCommands": {
  	 "all": [
  	 	  "npm install",
  	  	  "node install.js first"
  	  ],
  	  "win32": [
              { 
  	      	"attempt": "..\\somefile.exe \/S",
  	      	"timeoutAfterSeconds": 10,
  	      	"warnOnTimeout": "Sorry, we could not run your file automatically. If it is not already installed, please open File Manager and double click etc."
  	      }
  	  ],
  	  "win64": [
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

* __name__: the globally unique name for this add-on, which will be displayed within the Add-ons page, and will be the directory created within the medimage\addons folder. Use lower-case and do not include spaces.

* __installCommands__ are the commands to run after the .zip file has been unpacked to carry out an installation.

* __all__ are commands that are run on all platforms (Win32/Win64/Unix/Linux/Mac)

* __win32/win64/unix/mac__ are platform specific commands. Unix is synonymous with Linux, here.

* __successMessages__ (ver >= 1.4.3) are messages the user will see on success, for a particular platform.

* __attempt object__ (ver >= 1.4.3) is an item that is attempted to be run, but if there is a failure, it will not stop the whole installation being a success. timeoutAfterSeconds (optional) refers to how long the attempt will run until it’s process is deleted, and the warnOnTimeout (optional) option is the warning that is shown in yellow if this event occurs.

 

## Embedding NodeJS add-ons (ver >= 1.3.4)

You should write your scripts to be compatible with NodeJS 4.2.6.

You must include a function called ‘medImage’ in your NodeJS module, that can be called by the main server e.g. in this pattern below:

```
module.exports = { 
	medImage : function(argv, callback) {

                        //Your code in here, which sets 'resp'. The output is up to you.

			var output =  "returnParams:?CUSTOMJSON=" + encodeURIComponent(JSON.stringify(resp));  

			var ret = {};
			ret.err = "";
			ret.stdout = output;
			ret.stderr = "";
			
                        //Always return { err, stdout, stderr }. Include an error in the first param if necessary.
			callback(null, ret);	

	}	
}
```
 
 
 
## Basic Authentication (ver >= 1.3.8)

Basic authentication is available for add-ons written in NodeJS via a global password and session ID mechanism. The global password is set by an administrator in the main config.json file e.g. C:\medimage\config.json.

```
"basicAuthent": "changeme"
```

Note: this password is readable in plain text if you have access to the file-system, although it is never shown within the interface. Therefore, it should be considered basic level security, rather than high level security. The password is shared by all users.

__To include basic authentication__ in your client-side HTML pages, add this snippet to the bottom of your page before the body tag:

```
<!-- MedImage session client script -->
<script src="../js/session-client.js"></script>
```

__To check the password__ that has just been entered by a user is valid, from within your add-on’s client-side Javascript: (where the element ‘pass’ is your password text input element)

```
var uri = "/addon/get-session";
                    
jQuery.ajax({
	url: uri,
	data: { pass: jQuery("#pass").val() },
	success: function(data) {
		var myobj = JSON.parse(data);
		if(myobj.success == true) {
			setCookie(myobj.sessionId);
			//And display any logged in details here
		} else {
			alert("Sorry, please enter the correct password");
		}
	}
}); 
```

Once this cookie has been set, you can refer to it again with

```
var sessionId = getCookie("sessionId");
```

and pass it as a URL parameter, such as ‘sessionId’, to your server-side NodeJS scripts.

Eg. to create a URL string, you could use:

```
var url ="/addon/show-analysis?photo=test&sessionId=' + sessionId;
```

__Then, from your server-side NodeJS script__ include this at the top of your script:

```
var session = require('../basic-authentication/session.js');
```

and check the passed-in ‘sessionId’ parameter is valid, which indicates the user has already entered a correct password, with:

```
var queryString = require('querystring');

var opts = queryString.parse(param);
if((opts.sessionId) && (session.checkSessionValid(opts.sessionId) > -1)) {
   //Yes, the session ID is valid
} else {
   //No such session ID
}
```

Note: one session entry is stored in RAM indefinitely for each user’s browser that visits the site,  on the server-side. If you are expecting hundreds of thousands of users, this is likely not a good solution, and we would recommend creating your own login and session system, with expiry times; probably using a database or memcaching system. 
 
 
 

## Example Project

The MedImage Add-on for resizing photos is a good starter framework for those wanting to develop in NodeJS. The source code is available from:

https://github.com/atomjump/medimage-addon-resize

You’re welcome to include the same code in your own project, and modify it to suit your needs.