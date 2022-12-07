# SignalRGB-iOS-Control
This tool takes advantage of iOS "Shortcuts" to allow control of [SignalRGB](https://signalrgb.com/) from iOS devices (and Macs as well, if desired)

## Requirements
 - An iOS device or Mac with the Shortcuts app.
 - A Windows Computer with [SignalRGB](https://signalrgb.com/)
   - Having a local Static IP Address set up for this computer is recommended.

## Setup
This tool utizes SSH to control SignalRGB on your computer. Before you can use this, you must enable/download the Windows OpenSSH Server feature. 

 1) Download the `.shortcut` file from this repo onto the iOS device or Mac you want to control SignalRGB from.
 2) Scroll to the bottom to the `Run script over SSH` block, and fill in the following information:
     - Your computer's IP address
     - Your windows username
     - Authentication method:
        - If you are simply doing this over the local network, Password authenticaiton is fine, so simply fill in your windows password
        - If you wish to control your RGB over the internet or simply wish to have more security, select `SSH Key`, then copy the public key of your device over to the appropriate file(s) on your computer, and restart the SSH server.
              
            >  I definitely recommend using SSH key authentication for greater security. If you want to run this over the internet, you ABSOLUTELY need to use SSH key authentication and disable password authentication for SSH connections to your computer, as there are bots actively searching for SSH servers that will brute force their way into password authenticated servers.

     - The `Input` section of the `Run script over SSH` block should be left blank.
   

#### Optional: Add shortcut to Home Screen

1) Open the Shortcuts app
2) Hit the 3 Dots at the top right of the `SignalRGB iOS Control` shortcut
3) Tap on the name at the top of the screen
4) Select "Add to Home Screen"
    - You can optionally then change the name it will use on your home screen, or you can set your own photo for the icon (such as the SignalRGB Logo).
 
## Usage
Shortcuts can be triggered multiple ways:
 - Via Siri
 - Directly, in the shortcuts app
 - From the Home Screen, after adding it to the home screen (see above)
 
 Once triggered, you will be presented with a list of lighting modes to choose from. Simply select one from the list, then if everything is working correctly, the lighting effect used in SignalRGB will be changed.

## Adding More Effects
To add additional effects:
 1) Add a new item to the menu
 
 Then, in the section of code for that selection:
 
 2) Add a text item containing the name of the effect as it appears in SignalRGB, replacing any spaces with `%20`
 3) Add a Set Variable item below the Text item, with Variable Title set to `Effect Name`, and Input to `Text` (should be referencing the text box directly above it)
