img src="https://atomjump.com/images/logo80.png">



# medimage-co-nz-content-only
This repository is a public copy of the important content on http://medimage.co.nz,  in case the servers should be down.

# Mac Installation


Note: This installation takes a little technical ability.

Open a terminal window as an Admin user from Launchpad->Other

1. Install MedImage Server, by running the following command:

```
eval "$(curl -fsSL -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/atomjump/medimageserv-macstaller/master/install)"
```

2. Safari should open with the settings page for your output photo folder, with the default location. You can click the ‘Mac’ link for tips on how to get your own path.

3. Once this is saved, click ‘return’ and pair with your app by clicking one of the 3 large buttons.

4. To return to your server at a later date, you can enter into the Safari address bar at the top:

```
localhost:5566
```

## To update the MedImage software

From an Admin user’s terminal, enter:

```
eval "$(curl -fsSL -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/atomjump/medimageserv-macstaller/master/update)"
```


## To uninstall the MedImage software

From an Admin user’s terminal, enter:

```
eval "$(curl -fsSL -H 'Cache-Control: no-cache' https://raw.githubusercontent.com/atomjump/medimageserv-macstaller/master/uninstall)"
```