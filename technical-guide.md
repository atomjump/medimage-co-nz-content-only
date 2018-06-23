<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Technical Guide



## The Proxy Server [Optional]

Note: this section requires technical and system administration knowledge.

<img src="https://github.com/atomjump/medimage-co-nz-content-only/blob/master/medimage-proxy.png">

What you will need: a linux (or Windows) web server with an incoming and outgoing internet connection. Any number of client Windows PCs potentially in different physical premises.

The setup: your server will receive photos over 3G or 4G wireless from your doctor’s mobile phones. The client Windows PCs are associated uniquely with each different mobile phone (via a code generated for each PC). A photo will stay on the proxy server for a few seconds before being downloaded to the doctor’s unique Windows machine, and then being removed from the proxy server.


## Proxy Setup

On your internet server, first install NodeJS and npm. See these install scripts, under the section ‘Node.js v4.x’, but there are multiple ways to do this depending on your platform e.g. MacOSX specific instructions are here https://github.com/atomjump/medimage-co-nz-content-only/blob/master/mac-installation.md. Note, Windows server users can install the same Windows 64-bit installer that client PCs use and do not need to follow the steps in this section below, however there are some configuration options which are slightly different (see Windows Binary Proxy Setup below).

Then

```
eval "$(curl -fsSL -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/atomjump/medimageserv-linstaller/master/install)"
```

Then open the firewall to port 5566 for reading and writing eg.

```
sudo ufw allow 5566/tcp
```

See more details on a Ubuntu firewall setup in this article: https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server

To track logs:

```
pm2 logs
```


For further details about starting and stopping the server see PM2 and the MedImage technical README.

## Windows client machine setup

Download and run the installable MedImageInstaller.exe on each client. Note: you will likely need to do this as an Administrator.

If you have installed your own proxy, enter the URL of your proxy server eg. ‘http://myproxy.mycompany.com:5566’

## Phone setup

Run the app and click the large circle. After 5 seconds it will mention that you can enter you 4 digit pairing code.

Enter the patient id in the box at the top, specific to each photo. Note: #tags will allocate a folder (this will create another folder inside your photos folder). eg.

```
#moles John123
```

Click the large icon to start taking photos, and they will appear after a few seconds on your PC. The default folder is C:\MedImage\photos, but it will also be copied to the folder you specify when you installed the MedImage server (or particularly for MedTech users, C:\mt32\attachments).

## Further options

You can back-up the photos as they arrive on any MedImage server to other drives or folders on the same drive. Edit the config.json file in the server’s directory.

```
"backupTo": [
                    "C:/your/folder",
                    "D:/your/second/drive",
                    "/linux/directory
              ],
```

Note the forward-slashes are needed on Windows and linux, rather than back-slashes

You can use a secure https server with

```
"httpsKey": "path/to/key/pem/file"
"httpsCert": "path/to/certificate/perm/file"
```

You can edit the ‘onStartBackupDriveDetect’ parameter to be true. This will auto-detect other drives on starting the script, and start backing up to a MedImage/photos folder at the top of the drive.
```
"onStartBackupDriveDetect": true,
```

Tip: JSONLint is a great tool for confirming you have a valid .json file.
Web Proxy. If your browsers usually require a proxy server (i.e. for normal web requests), then use the option

```
"webProxy": "http://yourUser:yourPassword@webProxyIPaddress:webProxyPort"
```

You can switch a server into 'lock down' mode, where the interface cannot change any settings, add-ons, or see any technical logs, by setting
```
"lockDown": true
```

Some add-ons need a human readable password for light security. This is a global password visible only within the config file (but anyone with file level access to the server can see this), and you should change the default ‘changeme’ password if you intend to use these add-ons. Server Ver >= 1.3.8
```
"basicAuthent": "changeme"
```

Provide the ability to upload additional file types other than basic .jpg photos, e.g. PDF.  You need to specify the allowed extension and MIME type in a new array element e.g. { “extension”: “.pdf”, “mime”: “application/pdf” }. Server Ver >= 1.5.0. Note: This feature is not currently supported via the ‘AJ Proxy Servers’, but will be once the feature is out of Beta.

```
 "allowedTypes" : [ { "extension": ".jpg", "mime": "image/jpeg" },
                    { "extension": ".pdf", "mime": "application/pdf" },
                    { "extension": ".mp4", "mime": "video/mp4" },
                    { "extension": ".mp3", "mime": "audio/mpeg" } ]
```


## Windows Binary Proxy Setup

After the  installation of the MedImage Server on your internet-connected Windows Server, edit the config.json file in the server’s directory (usually C:\MedImage\config.json), and set these values:

```
"allowPhotosLeaving": true,
"allowGettingRemotePhotos": false,
"lockDown": true
```
(note: no web server is required)

Then restart the MedImage service in the ‘services’, or restart your machine.

## Multiple MedImage servers installed on the same Wifi Network

Currently, this configuration is not fully supported with fast WiFi scanning/sending. The app will choose the first MedImage server that it finds, which could result in photos being sent to the wrong PC.

Instead, each phone should be paired with the corresponding PC manually, and you should select ‘no’ when asked ‘Do you want to connect via WiFi, if it is available, also?’ during the pairing. The phone will still potentially use a Wifi network to upload, but it will go via the internet before coming down to the PC.


## Multiple MedImage servers installed on a single physical server

This is possible in both Windows and Linux. You should install the server software to another, non-standard folder on the drive (on Windows, copy the files in C:\medimage to another folder), edit the config.json file in the new folder’s root directory, change the port number to something other than 5566, e.g. 5567, and change the target folder, if necessary.

On Windows, you will likely want to install a new service to run the new server in parallel to the first. E.g. for an installation called ‘medimage2’, run in an administrator’s ‘cmd’ window:

```
C:\medimage2\nssm.exe install medimage2 "C:\Program Files\nodejs\node.exe" "C:\medimage2\bin\server.js" "5567"
C:\windows\system32\net.exe start medimage2
```

and to uninstall

```
C:\windows\system32\net.exe stop medimage2
C:\medimage2\nssm.exe remove medimage2 confirm
```


## Migrating from one MedImage installation to another

If you are testing out a new installation, while keeping an old installation in live operation, you should use a new global ID on the new installation during the testing phase – this will happen naturally when you install it.

If you wish to keep all existing phones synced correctly when you take the new installation live, you will need to transfer the ID from the old installation to the new one. You can expect a few minutes of down-time for this procedure:

1. Stop the MedImage service on both the old installation and the new installation, in Windows Services. This prevents any installation conflicts.

2. Copy across the following ID fields from the old C:\MedImage\config.json into the new C:\MedImage\config.json.

```
globalId: "bS6FpXvwagUbeMIXnM"  
readProxy: "https://medimage-nz1.atomjump.com/read/bS6FpXvwagUbeMIXnM"
transfer: 45652482
```

Note: The green values should be the same within any one config file.

3. Restart the MedImage service on the new installation. You should be live now.

4. You might wish to rename the old installation’s C:\MedImage\config.json to C:\MedImage\config-old.json, to completely prevent an accidental reboot from causing the old server to conflict with the new installation, while you are testing the new live installation.

5. Once you are happy with the new live installation, uninstall the old installation’s MedImage Server through the regular Windows ‘Add or Remove Programs’.


## System Overview Options

Here are some possible configurations for integration with your existing medical systems:

* MedImage server on each PC
https://github.com/atomjump/medimage-co-nz-content-only/blob/master/medImageInstallOption1.pdf

* MedImage Server on each PC, with your own proxy server
https://github.com/atomjump/medimage-co-nz-content-only/blob/master/medImageInstallOption2.pdf

* MedImage Proxy server on your application server
https://github.com/atomjump/medimage-co-nz-content-only/blob/master/medImageInstallOption3.pdf

* MedImage Server on Windows Servers with shared drives (e.g. Primary Health organisations)
https://github.com/atomjump/medimage-co-nz-content-only/blob/master/MedImagePrimaryHealth.pdf



## Troubleshooting


If you are having issues with photos not appearing or being transferred to a target folder, particularly on a Windows server, firstly check that the photos are arriving in the C:\MedImage\photos folder. If they are, but they haven’t moved into the target folder, the most common problem is a permissions issue. On Windows, check that the user that installed the MedImage Server had administrative privileges, and is able to read and write to the target folder.  Any network drive mappings should be available to the user that installed MedImage Server, when run as a background service, but if not, you can also try the network path e.g. \\server\folder format.

## Common problems with Windows network drives:

a) The Local System user (that may have installed the server software) often won’t know about the network drive letter. In this case you can try the raw network path e.g. ‘\\server\path’

b) An admin user (or in particular the local system user) may not have permissions on that path. You can read more about this here. The admin user should have read and write permissions. You can enable this by setting up a folder or drive share with read and write access for the computer name itself. A MedImage Server holding computer called e.g. MANGO should be shared using the title MANGO$ in the share options on the target folder.

c) You can use this as a test from an administrator command prompt, to see if you have access rights. Create a file called text.txt in Notepad. Then e.g.

```
copy test.txt M:\targetfolder\
```

If this returns an error, you know you do not have permissions.


## Checking logs

The logs are available on a new installation from the MedImage Server web interface home-page (typically http://localhost:5566), and this is a good first place to check.

You can also get a live log operating by using the command line version, rather than the Windows service version. To do this, stop the Windows MedImage service temporarily, and run the server from the command-line to watch for errors. Please note: if this is a busy, live service, any delay between stopping the service and running the script could result in missed data.

1. Stop the ‘MedImage’ service through the normal Windows services

2. Run a command prompt (cmd), and enter

```
cd c:\MedImage
node bin\server.js
```

3. Take a photo from the app, and see the response logged on-screen on your PC.

Once you’re done, steps to re-enable are

4. ‘Ctrl-C’ to break the current server from within the prompt.

5. Restart the MedImage service through the normal Windows services.



## Administrator rights

Remember that you should be logged in as an ‘Administrator’ user before installing MedImage server. If your machine does not already have an Admin user (which is the case with e.g. client-based Windows 10), you can run ‘cmd’ from the start bar. Right click on the black cmd icon, and click ‘Run as Administrator’.

Then enter the following line:

```
net user administrator /active:yes
```

to activate the Administrator user. Once you have logged in, choose a password, and you can then install MedImage Server.



## Add-ons

Add-ons provide additional features to MedImage, and are generally installed in the server’s /addons folder.
If you are a developer, you can develop your own add-ons to MedImage.


### MedTech32

If the MedImage add-on settings for ‘Show Extended Options/Maps Down To’ are set to ‘M:\’, and the M drive is not visible on the server (since the file reference will be from M:\Attachments\…), you can use this work around:


1. You can switch the ‘Show Extended Options/Maps Down To’ setting in MedImage to ‘C:\mt32\’ on a single machine installation of MedTech32
2. Or, on the server you can create a mapping in a cmd prompt: ‘subst M: C:\mt32’ which maps the \mt32 folder to the M: drive.

