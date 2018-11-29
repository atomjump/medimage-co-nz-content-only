

<img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only

This guide is a copy of the important content from http://medimage.co.nz/addon-wound-analysis-guide/,  in case the servers should be down.



## Installation

If you are a nurse, please go down to the ‘Taking a Photo’ section, below.

For system administrators, continue with this section:

You will need to install the MedImage Server version ( > 1.5.3).

Once the MedImage Server is installed, you should download and install the MedTech add-on from

http://medimage.co.nz/addon-wound-analysis/

To download this, register to purchase from that page – it will give you a 30-day free trial, and take you to the download section.

You can download both the Server software and the Wound Mapp add-on as many times as you need to run it on your system. If you don’t find it works in with your set-up, you can cancel the Paypal ‘subscription’  at any time within the 30 day period. MedImage support is available if you need on-site or remote assistance in installing this. Please remember that the license is per hardware server, so you will need to purchase a new copy if you plan on running the software on a new site, and consider an enterprise version if your single server handles multiple practices.

Note: This software will require a version of your photos in your MedImage/photos folder, as well as a version in your target destination folder, if they are different. If you require a different target folder, your storage requirements will be doubled. 

 

## Post Installation Set-up



To calculate the area of the wounds, you will need to place a known sized sticker within the photo, next to the wound. This gives a measurable guide within the photo that can be extrapolated to calculate the size of the wounds in the photo.

You will need to choose a standard sticker type to use across your organisation. This should be a circular shaped single-colour sticker, of a known and fixed size.

The default colour and size configuration is for a light yellow 14mm diameter sticker from the manufacturer Esselte (See https://www.warehousestationery.co.nz/product/W2216138.html), although there may be better options, and it will vary from country to country. When choosing a sticker try to select one that has:

* A bright, bold colour that is not likely to appear on a body, or near a wound (or, for that matter, in a typical natural background shot). While bright blue seems to work better than green or yellow in our experience, if you are using blue hypoallergenic gloves, a bright yellow or green may be a better option. It should create a fairly consistent colour within a photo.

* A matt surface, so that reflections or folds in the sticker don’t affect the colour in the photo, when light is shone directly against the sticker

* Easily detachable from the skin, whilst leaving behind very little residue. The residue should not be able to infect a wound.

To calculate the standard size of your sticker in square centimeters (and if you’ve forgotten your high school maths!), you can search Google for ‘area of circle’. There is a quick sizing calculator there, but please use the ‘more details’ options to get at least 3 decimal places, and remember that your figure should be in square cm, not square mm. Enter this in the Settings ‘Standard Area of Sticker’ option.

In our live tests, automatically detecting the boundary of the wound based on the colour was a challenging task for the computer to do, and we have therefore switched this option off. Instead, the preferred approach is for the nurse to trace around the photo immediately after it has been taken. 

Typically, if you are the administrator, you will need to take a few photos of your chosen sticker under different lighting conditions, and make your sticker’s colour ranges global, before nurses begin using the package. This process is described below under the ‘Adjusting the colour matching’ section, but take particular note of the ‘Making a colour range global’ section, so that your users will find it pre-configured to auto-detect the stickers you have chosen.

Once you have configured these options, you may choose to set the option 'lockDown' to 'true' in your C:\MedImage\config.json file, to prevent users changing these settings from their own browsers. See the Technical Guide at http://medimage.co.nz/technical-guide/ for further details.
 

## Taking a photo

Install the ‘medimage‘ app to your phone or tablet. This costs US$10 per phone, but is a one-off payment.

1. Connect your app to your MedImage Server using the standard instructions here.

2. We would recommend entering an NHID or similar health identifier for the patient in the text box before taking the photo. Many users would also choose to have the ‘ID writes a folder’ option set on; see here for instructions. This saves having to enter ‘#’ at the start of each ID to create a folder on the server for the patient’s photos, which allows the photos to be searched for by the patient identifier, later on.

Here are some examples of what you might want to enter:

```
#NHI1234 arm
```

This would write a photo called ‘arm-[date/time].jpg’ into the folder NHI1234

```
#NHI1234 #arm
```

This would write a photo called ‘[date/time].jpg’ into a subfolder NHI1234\arm, which would allow you to see all of the ‘arm’ photos alongside each other, on the server.

Or with ‘ID writes a folder’ option set on, this would be

```
NHI1234 arm
and
NHI1234 #arm
```

3. Place the sticker on the patient near the wound. Your camera should be placed at right angles to the surface of the wound, and the wound should cover a reasonable proportion of the whole photo. If the wound wraps around the body, the area measurements will not be accurate – and our tool will not handle this case properly, but you can still take a photo to document the wound over time.

4. Click the large purple ‘Camera to PC’ button to take the photo, as described here. Once the photo has been shown as ‘Image Transferred. Success!’ you should switch across to your installation of MedImage Server, which could either be found from a desktop button, or at a particular address in your browser that your system admin will give you e.g. ‘http://localhost:5566’, which should be copied into a web browser address bar such as Chrome, Firefox, Edge or Internet Explorer.

 

## Analysing the Photo



* Within your PC or installation of MedImage Server, click ‘See Photos’ on the left hand menu. Start typing the patient ID or photo name, and after a few moments potential options will pop down:



* Select a folder or a specific photo. If you select a folder, you will see all of the photos taken within that folder e.g.


* From here you can compare the sizes of wound in the different photos, or select them for closer analysis. The file names will give both a date and a time. If you are looking for the photo you have just taken, you will probably not have an ‘area’ value at this stage. Click the photo you have taken.

* If you selected a particular photo from the search box, it will take you through to that photo’s analysis screen, e.g.





* If the sticker has not been automatically detected, it will have a message '[Please draw around the sticker]', and you will be taken into the sticker drawing page initially. With your mouse, trace around the sticker and fine-tune. You can switch between drawing the sticker and drawing the wound using the icons above the photo, and once you are done, you should switch to the wound. Alternatively you can adjust the colours by clicking 'Adjust Colour Matching' at the bottom of the page (see the 'Adjusting the colour matching' section below) to try to match the sticker automatically.

* With your mouse, pen or finger, trace a circle around the wound - the area you wish to measure. Click 'Save' to save the shape, and recalculate the area, or 'Undo' if you make a mistake. You can delete all drawings with 'Clear', or adjust their boundaries by moving the border points. If you click in the middle of an area, that area will be removed.

* You can make multiple drawings, and the wound area calculated will be a sum of all areas. Each individual area should ideally be a closed shape, without overlaps, although it is not always necessary to fully close the line when you draw it.

* If there are multiple wounds that you wish to track the area of, we currently recommend that you take multiple photos - one photo for each wound.

* Once you are happy with the area selected, or if there are some automatically generated wound areas, you will see an area in square centimeters at the top of the screen. 

* Note for IE users: to draw several areas over the wound, draw one area, click the left mouse button within the zoomable area, and then you can draw a second area.

* You can also view the original full-scale image in your browser by clicking ‘Original Image’, or adjust the colour matching by clicking ‘Adjust Colour Matching’.

 

## Adjusting the colour matching

The automatic colour matching is always used for detecting the sticker, but can also be used for wound detection if the option is set.

Note: If you are not the system administrator, we recommending asking before changing either the global colour ranges, or the wound detection option in the settings, because it affects all users of the system moving forward.



There are ‘local’ colour ranges, which are specific to this photo, and ‘global’ colour ranges, which are detected in all future photos, by all users of the system. You can edit the colour ranges for this photo first, and choose whether other users want this colour range too, if they are generic.

## To adjust the colour ranges:

1. Select which method of colour you want to adjust, either ‘Auto Range’, ‘Lower end of Range’, or ‘Upper end of Range’. The ‘Auto Range’ is the easiest option, and it will take an automatic range around the colour that you click on the photo (from darker to lighter with your chosen colour in the middle of the range).  If you choose ‘Lower end of Range’ you can manually define the specific range, but you will need to click on the photo a second time – first to set a dark colour, and then second to set a light colour from the photo (‘Upper end of Range’ will be automatically selected after the first click).
2. Select whether this colour applies to the sticker or the wound.
3. Click the colour from within the photo itself, and after a page refresh, the new range will appear on the right hand side, for this photo. Click a second time to finish the range, if this is not an ‘Auto Range’. If you wish to delete the range you have entered, click the button next to it ‘…’, and click on the ‘rubbish bin’ button.
4. Once you are happy, click the green ‘Refresh Analysis’ button to re-analyse the photo with these new colour ranges. If this detects the item correctly, you may want other users to have access to this colour range, although we would recommend asking your adminstrator first before doing this. Each new colour range slows down the analysis slightly. You can see the global set of colours used by clicking the light blue ‘Globe Colours’ button.
 

## Making a colour range global

Global colour ranges are used by all new photos. If you add a new global colour range, past photos will not be affected, unless the ranges are copied down for each photo, and then re-analysed, manually.

To transfer a colour range to the global colour range lists, click the small button next to the range, and then click the small globe button.

To go the other way, click the light blue ‘Globe Colours’ button to reveal the global colour ranges. You can remove colour ranges from the global ranges by selecting the range and clicking the ‘rubbish bin’.

Or, if you want to copy a global colour range down to your local photo, click the ‘…’ button next to the range, followed by the ‘copy’ button. You would usually only need to do this if there are new global colour ranges that have been added since you took the photo.


## Grouping colour ranges

You can group ‘local’ or ‘global’ colour ranges by tapping the group button underneath them. This will create a single new colour range that covers the extremes of all the current colour ranges. You have the option of adding this new range to the list, or replacing all the current colour ranges.

This is a useful way of speeding up the colour matching (each range will take a small amount of time, so generally the fewer the better), and make it more consistent. The button will only affect either the ‘local’ photo, or future ‘global’ photos, depending on the heading it is under.


# Exporting and Reporting

## Wound Improvement Messages

These messages will appear at the bottom of a search results page for a particular folder, to give you a quick warning if the wound is not getting better.

The rules used are:
By default, use a yellow box.
If improvement < 30% after 14 days, make the box red.
If improvement < 0% from start to finish, make the box red.
If improvement > 97% from start to finish, make the box green.


## Photos

Your photos are available in your selected target folder (or C:\MedImage\photos) on the server machine that is running MedImage Server. You can also access the main photo by clicking 'Original Image' in a photo edit screen. Then, depending on your browser, right clicking and selecting 'Save Image' or similar, will download the original photo to your desktop.


## Meta-Data

Within the settings/Wound tab, you will find an 'Export' button. This will export all photo meta-data in .csv format, for import into a spreadsheet. This spreadsheet will not include the photo's .jpg files themselves. You can use e.g. Microsoft Excel or Google Sheets to import this data, or any software that reads csv files.

Included fields are:

Filename, Id, Subfolder, WoundName, AreaSqCm, ExternalSqCm, UnderminingSqCm, ImprovePerc, Period, Status, ExternalImprovePerc, UnderminingImprovePerc, ServerDateTime


## Meta-Data Fields

__Filename__ is the full image path away from the photos folder (without the .jpg extension).

__Id__ is the first word entered by users of the app, which is often an NHID (within New Zealand) or some other identifier.

__Subfolder__ is a second folder name for subcategorizations e.g. leg or arm. In the app you would enter e.g. 'id #subfolder' to get this.

__WoundName__ is the name of the wound. In the app you would enter e.g. 'id woundname', or 'id #subfolder woundname' to get this.

__AreaSqCm__ is the area in square centimeters, if known, of the wound. Other messages, such as '[Please draw around the sticker]' can appear in here. If there is any wound undermining (i.e. under the skin wounds), then this is the combined external and undermining area.

__ExternalSqCm__ is the area in square centimeters, if known, of the external wound (as opposed to the undermining, internal wound). If this is not applicable, because there is no undermining wound, it will be '[NA]'.

__UnderminingSqCm__ is the area in square centimeters, if known, of the undermining wound. (i.e. under the skin).  If this is not applicable, because there is no undermining wound, it will be '[NA]'.

__ImprovePerc__ is the percentage improvement of the area of the wound. It is calculated from the photos in this folder, since the time of the first photo in the folder. If some areas of the photos are not known, they are not included in this calculation. If there is any wound undermining (i.e. under the skin wounds), then this is the combined external and undermining improvement.

__Period__ is the period since the wound was first photographed. This is calculated from the ServerDateTime field, and is in English e.g. '1 day' or '2 months and 10 days'. Technical Note: be careful if you copy your photos to a different server, that you retain their 'date-created' information, at the operating system level. E.g. in Linux, use the '-p' option when copying a folder i.e.

```
cd oldphotosfolder
cp -Rp * newphotosfolder
```

__Status__ can be 'recovering', 'recovered', or 'warning'. Recovering means the wound is getting better. Recovered means they have fully recovered ( > 97% improvement). Warning means the wound is getting worse, or has not improved by more than 30% after two weeks.

__ExternalImprovePerc__ is the percentage improvement of the area of the external wound, by itself (as opposed to the undermining wound). It is calculated from the photos in this folder, since the time of the first photo in the folder. If some areas of the photos are not known, they are not included in this calculation. If this is not applicable, because there is no undermining wound, it will be '[NA]'.

__ImproveUnderminingPerc__ is the percentage improvement of the area of the undermining wound (i.e. under the skin), by itself. It is calculated from the photos in this folder, since the time of the first photo in the folder. If some areas of the photos are not known, they are not included in this calculation. If this is not applicable, because there is no undermining wound, it will be '[NA]'.

__ServerDateTime__ is the time in GMT (Greenwich Mean Time) that the server recorded the photograph. This could be offset from the time-stamp in the file name itself by up to a day due to different time-zones, or a few seconds due to the delay between the photo transferring from the phone to the server.




