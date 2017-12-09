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

On your internet server, first install NodeJS and npm. See these install scripts, under the section ‘Node.js v4.x’, but there are multiple ways to do this depending on your platform e.g. MacOSX specific instructions are here. Note, Windows server users can install the same Windows 64-bit installer that client PCs use and do not need to follow the steps in this section below, however there are some configuration options which are slightly different (see Windows Binary Proxy Setup below).

Then

```
sudo npm install pm2@latest -g
sudo npm install medimage -g
cd "$(npm prefix -global)/lib/node_modules/medimage/"
cp addons/configORIGINAL.json addons/config.json 
pm2 start npm --name "medimage-server" -- start
./medimage-server.sh; cd ~
pm2 save
pm2 startup     	#and run the command it outputs, to get autostart at boot-up.
```

Then open the firewall to port 5566 for reading and writing eg.

```
sudo ufw allow 5566/tcp
```

See more details on a Ubuntu firewall setup in this article.

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


## Windows Binary Proxy Setup

After the  installation of the MedImage Server on your internet-connected Windows Server, edit the config.json file in the server’s directory (usually C:\MedImage\config.json), and set these values:

```
"allowPhotosLeaving": true,
"allowGettingRemotePhotos": false
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

If you are having issues with photos not appearing or being transferred to a backup folder, particularly on a Windows server, you can stop the Windows MedImage service temporarily, and run the server from the command-line to watch for errors. Please note: if this is a busy, live service, any delay between stopping the service and running the script could result in missed data.

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

 

## Common problems with Windows network drives:

a) The Administrator user (that runs the server software) does not know about the network drive letter. If this is the case, you can either add a drive mapping for that admin user, or use the raw network path.

b) The admin user may not have permissions on that path. You can read more about this here. The admin user should have read and write permissions.

c) You can use this as a test from an administrator command prompt, to see if you have access rights:

```
icacls "D:\somefolder\inhere" /grant Everyone:(OI)(CI)F
```

If this returns an error, you know you do not have permissions.

 

## Add-ons

Add-ons provide additional features to MedImage, and are generally installed in the server’s /addons folder.
If you are a developer, you can develop your own add-ons to MedImage.


### MedTech32

If the MedImage add-on settings for ‘Show Identifier Options/Location’ are set to ‘M’, by default, the photos will only be visible when you click the link within MedTech32 on client PCs, not the server itself (since the file reference will be from M:\Attachments\…). However you can work around this:

You can switch the ‘Location’ setting in MedImage to ‘C’ on a single machine installation of MedTech32
Or, on the server you can run in a cmd prompt: ‘subst M: C:\mt32’