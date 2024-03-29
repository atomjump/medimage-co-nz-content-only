<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.


# Patches

	
Patches fix known issues in a main version, without affecting other software such as add-ons, or settings. It is usually smaller and faster to install than the original.

 
## MedImage Server Patch to ver 1.8.5.3

Ver 1.8.5.3 and 1.9.0.1 (Cloud) allows a larger maximum file size (and a flexible option in the config file) – it defaults to the larger 16MB rather than 10MB – this is important if you are to allow particularly detailed iPhone images on modern iPhones.

Note: You can check this 32-bit / 64-bit decision guide, first. See 32-bit-or-64-bit-guide.md.

* https://medimage-download.atomjump.com/MedImageServ-PatchInstaller.exe?ver=1.8.5.3
* https://medimage-download.atomjump.com/MedImageServ-Patch32Installer.exe?ver=1.8.5.3
* https://medimage-download.atomjump.com/MedImageServ-PatchInstaller-cloud.exe?ver=1.9.0.1
* https://medimage-download.atomjump.com/MedImageServ-Patch32Installer-cloud.exe?ver=1.9.0.1
* https://medimage-download.atomjump.com/medimageserv-patch-1.9.0.1.zip



Note: On Windows, you should run this as the Administrator user, on the same machine that the MedImage Server was installed on.

Note: This patch can be run whilst the server is in use and users do not need to log out.

Note: the .zip installer should be installed via the Add-on installer within the MedImage Server > Settings. Right click on the .zip button above, copy the URL link, and paste this into the Add-on installer page form. Then click ‘Download and Install’.

Note: Using the .zip installer you will need to turn off the lockDown mode if it is on, prior to this.



## Rollback Procedure

If there is any issue with the operation of the MedImage Server after this patch is applied, you will find your old ‘server.js’ file, which is the file changed, in the same C:\MedImage\bin folder as ‘archived-server-[DATETIME].js’. You can rename and copy this over the current ‘server.js’, in that folder, to roll back. You will also need to restart the ‘MedImage’ service in Windows Services, or  ‘pm2 restart medimage-server’ on Linux/Mac.


## Also included in this Patch

The following updates are also included, if your version of the MedImage Server is older:

Ver 1.8.5.2 and 1.8.8.1 (Cloud) fixed a temporary file build-up if a connecting app is misbehaving.

Ver 1.8.5 update fixed an issue with multiple quick-succession photos not being copied into the target folder.

The 1.7.8 update was for users running a Proxy Server, as image uploads were more robust under network dropout conditions.

Ver 1.7.6 redirected pairing requests to the new MedImage / AtomJump server infrastructure, which is important if medimage.co.nz is not operational. If medimage.co.nz is operational, this patch is not required, though it is recommended.

Ver 1.6.2 fixed a known issue that could stop new photos from being downloaded, requiring a MedImage Server restart. The problem, while relatively rare, could occur at random, after months or even years of successful operation. You can fix the issue:

* Temporarily, after it has happened, by restarting the ‘MedImage’ Windows service, or
* By reinstalling your MedImage Server and add-ons, with a version of the MedImage Server >= 1.6.2, or
* By installing this patch

This patch will work for all versions of the MedImage Server >= 1.5.3, and <= 1.7.6, and is the easiest option.

It also fixes an issue around sending photos in quick succession (some of which wouldn’t be correctly copied into the target folder).


## Older Patch Versions

* https://medimage-download.atomjump.com/previous-stable/MedImageServ-PatchInstaller-1.8.5.2.exe
* https://medimage-download.atomjump.com/previous-stable/MedImageServ-Patch32Installer-1.8.5.2.exe
* https://medimage-download.atomjump.com/medimageserv-patch-1.8.5.2.zip


## Beta Patch Versions

Ver 1.8.5.2 and 1.8.8.1 (Cloud) fixes a temporary file build-up if a connecting app is misbehaving.

* https://medimage-download.atomjump.com/MedImageServ-PatchInstaller-beta.exe
* https://medimage-download.atomjump.com/MedImageServ-Patch32Installer-beta.exe
* https://medimage-download.atomjump.com/MedImageServ-PatchInstaller-cloud-beta.exe
* https://medimage-download.atomjump.com/MedImageServ-Patch32Installer-cloud-beta.exe
* https://medimage-download.atomjump.com/medimageserv-patch-1.8.5.2.zip

