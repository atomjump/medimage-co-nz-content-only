<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Patches

	
Patches fix known issues in a main version, without affecting other software such as add-ons, or settings. It is usually smaller and faster to install than the original.

 
## MedImage Server Patch to ver 1.8.5

Ver 1.8.5 fixes another issue with multiple quick-succession photos not being copied into the target folder.

Included in this version is the 1.7.8 update.

The 1.7.8 update is useful for users running a Proxy Server, as image uploads are more robust under network dropout conditions.

Included in this is ver 1.7.6, which redirects pairing requests to the new MedImage / AtomJump server infrastructure, which is important if medimage.co.nz is not operational. If medimage.co.nz is operational, this patch is not required, though it is recommended.

The 1.6.2 patch, which is included also, fixes a known issue that could stop new photos from being downloaded, requiring a MedImage Server restart. The problem, while relatively rare, may occur at random, after months or even years of successful operation. You can fix the issue:

* Temporarily, after it has happened, by restarting the ‘MedImage’ Windows service, or
* By reinstalling your MedImage Server and add-ons, with a version of the MedImage Server >= 1.6.2, or
* By installing this patch

This patch will work for all versions of the MedImage Server >= 1.5.3, and <= 1.7.6, and is the easiest option.

It also fixes an issue around sending photos in quick succession (some of which wouldn’t be correctly copied into the target folder).

 

Note: You can check this 32-bit / 64-bit decision guide, first. See 32-bit-or-64-bit-guide.md.

* https://medimage-download.atomjump.com/MedImageServ-PatchInstaller.exe?ver=1.8.5.1
* https://medimage-download.atomjump.com/MedImageServ-Patch32Installer.exe?ver=1.8.5.1
* https://medimage-download.atomjump.com/medimageserv-patch-1.8.5.1.zip



Note: On Windows, you should run this as the Administrator user, on the same machine that the MedImage Server was installed on.

Note: This patch can be run whilst the server is in use and users do not need to log out.

Note: the .zip installer should be installed via the Add-on installer within the MedImage Server > Settings. Right click on the .zip button above, copy the URL link, and paste this into the Add-on installer page form. Then click ‘Download and Install’.

Note: Using the .zip installer you will need to turn off the lockDown mode if it is on, prior to this.



## Rollback Procedure

If there is any issue with the operation of the MedImage Server after this patch is applied, you will find your old ‘server.js’ file, which is the file changed, in the same C:\MedImage\bin folder as ‘archived-server-[DATETIME].js’. You can rename and copy this over the current ‘server.js’, in that folder, to roll back. You will also need to restart the ‘MedImage’ service in Windows Services, or  ‘pm2 restart medimage-server’ on Linux/Mac.


## Older Patch Versions

* https://medimage-download.atomjump.com/previous-stable/MedImageServ-PatchInstaller-1.7.8.exe
* https://medimage-download.atomjump.com/previous-stable/MedImageServ-Patch32Installer-1.7.8.exe
* https://medimage-download.atomjump.com/medimageserv-patch-1.7.8.1.zip