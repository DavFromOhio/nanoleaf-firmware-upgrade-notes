# Nanoleaf controller firmware updates

## 1. First things first: 
Nanoleaf is a trademark of Nanoleaf Energy Technology ShenZhen Limited.

If your Nanoleaf app can pair with your Nanoleaf product, this document is quite possibly of no use to you.
I (author of this text) am not a Nanoleaf employee, associate, investor or in any other way associated with Nanoleaf. Technically, I do not even own Nanoleaf products. Family members do.

What *may* appear as technical advice in this document is merely a description of what *I* would do to bypass certain challenges which may occur when trying to use the current Nanoleaf Android app to connect to controllers with very old firmware. In short: pairing may not work. Maybe you get Error 009. Maybe you are at wits end. Maybe you are about to say foul things about ... products.

**I take no responsibility whatsoever for any breakage, nor loss of money, time, wits or marriage.**


## 2. Understand the mechanism we will employ
A Nanoleaf controller (at least Elements) will, out of the box, behave as a disconnected wireless access point. That is, you can connect to it, but it does not provide access to the Internet. The controller runs a tiny web-server we can talk to. This webserver provides a page to which we can upload a firmware image. If your device has been configured previously, you may have to execute a procedure to reset it to factory defaults. I don't know how. Figure it out.

In short: disregard the Nanoleaf app for a little while.


## 3. Procedure
The procedure is as follows (do *not* *do* this at first read. Just read it. Please.)
- Identify your hardware
- Download **relevant** firmware files. Note "relevant" and the plural form "firmwares".
- Connect the controller to a panel/light
- Connect the power brick to the panel, plug the powerbrick into the wall socket, power up the device. Give it a minute. 
- Find the access point SSID broadcast by the controller in the wireless settings of a PC, MAC, Android or IOS phone. Typically named `Elements ABCD` for an elements controller.
- Connect to this SSID with your PC, MAC, whatever.
- From the web-browser of your wireless client (PC, MAC, whatever), access the address [http://192.168.2.1/](http://192.168.2.1/). Note *http*, not *https*. You should get a simple web-page identifying your current firmware version and some other details. And two buttons, 'Browse...' and 'Upload File'.
- Choose the first firmware in the list below having a version *after* the one currently running on your controller by hitting the 'Browse...' button. Select exactly one firmware file. We will repeat the procedure from this step, one version at a time, until you are at the latest release.
- Press and hold the controller button until the LEDs start flashing/running. Then release the button.
- Hit the 'Upload File' button in the device web-page within 30 seconds of the lights starting to move.
- There is no progress bar. If you are technically inclined, you know what to do. Otherwise, just wait.
- Wait a couple of minutes. You should get a confirmation that the upload was successful. (*I* got a message about wrong file being uploaded when I tried exactly that. I offer no warranties that this works for all combinations of hardware and firmware. Make sure you upload the correct files.)
- Do not touch the controller.
- The controller will reboot with no further action on your part. Wait for the SSID to reappear in your list of possible wifi networks again. This takes additional minutes. Be patient.
- Connect to the SSID again.
- Reload the webpage and confirm that the uploaded image has been installed.
- Repeat steps above for the firmware images in the sequence.


## 4. Identify your hardware
Nanoleaf has multiple product lines:
- Shapes
- Elements
- Lines
- Canvas
- ... and more.

You should take care to know what product you own.
There may be a label on your box or on the device itself. In addition, there may be a product *code*. Make a note of that as well.


## 5. Download relevant firmware images for your specific hardware
You did read everything in the previous sections, right? Right?

Notes: 
- Firmware images of the same revision are named identically across product lines, but are not identical.
 In other words: there is a "7.1.6.firmware"-file for each product line that firmware version was released for. The files are not interchangeable between product lines.

- If your current running image is very old, you will likely have to upgrade in multiple steps. Cannot go straight from 5.3.2 to 12.3.2, for instance.

- I do not know if these images are compatible with your exact hardware revision.

- The URLs for these firmware images are not under my control. I can only assume this is how Nanoleaf distributes their firmware images. 

- And finally, I did not bother to guess the correct URLs for all product lines.


Not all firmware images in existence are listed in the table below. 

See the Nanoleaf Release Notes:

[2025](https://support.nanoleaf.me/hc/en-us/articles/35633948389268-Products-Firmware-Release-Notes-2025)

[2024](https://support.nanoleaf.me/hc/en-us/articles/33006784349076--2024-Archive-9-4-0-Firmware-Release-Notes-Panel-Products)

[older](https://support.nanoleaf.me/hc/en-us/articles/32800486435348--2023-Archive-9-3-4-or-Older-Firmware-Release-Notes-Panel-Products)  

I did not spend any energy guessing the URL for 'Lines' or other products. Feel free to let me know when you figure it out.

Your browser may complain about the links below being served via http (and not https). Figure it out.

Firmware table

| Elements | Shapes | Canvas | Lines |
|-----|------|------|------|
| [12.3.2](http://nl52-firmware.s3.amazonaws.com/12.3.2.firmware) | [12.3.2](http://hexagon-firmware.s3.amazonaws.com/12.3.2.firmware) | [12.3.2](http://canvas-firmware.s3.amazonaws.com/12.3.2.firmware) | |
| | [9.6.6](http://hexagon-firmware.s3.amazonaws.com/9.6.6.firmware) | | |
| | | [9.6.4](http://canvas-firmware.s3.amazonaws.com/9.6.4.firmware) | |
| [9.3.4](http://nl52-firmware.s3.amazonaws.com/9.3.4.firmware) | | | |
| [8.5.2](http://nl52-firmware.s3.amazonaws.com/8.5.2.firmware) | [8.5.2](http://hexagon-firmware.s3.amazonaws.com/8.5.2.firmware) | | |
| [7.1.6](http://nl52-firmware.s3.amazonaws.com/7.1.6.firmware) | [7.1.6](http://hexagon-firmware.s3.amazonaws.com/7.1.6.firmware) | [7.1.6](http://canvas-firmware.s3.amazonaws.com/7.1.6.firmware) | |
| [6.5.1](http://nl52-firmware.s3.amazonaws.com/6.5.1.firmware) | [6.5.1](http://hexagon-firmware.s3.amazonaws.com/6.5.1.firmware) | [6.5.1](http://canvas-firmware.s3.amazonaws.com/6.5.1.firmware) | |



## 6. Some very limited technical details
Nanoleaf controllers appear to run a fork of OpenWRT with linux kernel 4.4.something on a fairly old MIPS microcontroller.

The GPL sourcecode does not appear available. I believe this is a GPL license violation.

Some open source projects aiming to control nanoleaf products are:
- https://github.com/jimmyeao/esp8266-nanoleaf-webserver
- https://github.com/winleafs/Winleafs

These projects are, to my knowledge, not in any way affiliated with Nanoleaf
