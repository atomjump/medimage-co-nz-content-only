<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.



# Connecting to other medical systems

MedImage will connect to any medical system, but the level of integration depends on how closely you want the systems to link. There are four main options

1. Use the MedImage Server software as-is. Provided that the medical system has one particular folder that handles photos, you can enter this folder when you are installing MedImage Server. This is a file-level integration, and the photos will appear as .jpg files within that target folder, accessible to Windows Explorer or any other file management tool.

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/download-links.md

2. Use a commercially available MedImage Add-on, that appends the new photos directly into the external system’s database. For example, see the MedTech32 Add-on.

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/medtech32-addon.md

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/other-addons.md

Please contact atomjumpcom AT gmail.com for further details of Add-ons.

3. Use the commercially available general purpose EHR Connector Add-on, which is available below, that connects directly to a number of EHR databases and inserts the photos. If your chosen system is not already supported: provided you have some integration or DBA experience, and your system has an accessible API or database, you can customize this package relatively quickly to suit your own systems.

https://src.atomjump.com/atomjump/medimage-co-nz-content-only/blob/master/ehrconnect-addon.md

4. Build you own connection software, using the MedImage Developers API. This can connect to any system you choose, including your own custom systems. MedImage/AtomJump are available to help write these add-ons if you are not development-inclined, but each development is considered on a case-by-case basis commercially and an agreement will need to be discussed with yourselves. You can also choose to develop and sell these add-ons independently of MedImage.

Please contact atomjumpcom AT gmail.com for further details.
