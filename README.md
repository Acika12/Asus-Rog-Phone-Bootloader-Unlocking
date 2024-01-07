# Asus-Rog-Phone-Bootloader-Unlocking
This is the only way to unlock bootloader on Asus Rog Phone all version 

The author is not responsible for any damage that occurs while using my repository. This method is the only way to unlock the bootloader on ASUS ROG models

Note: I suggest first of all patching the boot.img using magisk, you can extract the update here, payload.bin and patch it on the device itself and send it to the computer

Required program:
* mitmproxy
* Unlock Asus App
* Adb and Fastboot

UNLOCKING BOOTLOADER
Steps:
1 - Install the mimproxy program and use a text editor to create a file called unlock.py
2 - In the file you must insert the following code:

Python:
from mitmproxy import http
def request(flow):
    if flow.request.host == "dm.asus.com":
        if "dm.asus.com/unlock/register" in flow.request.url:
            flow.request.urlencoded_form["apkVersion"] = "2.0"
            flow.request.urlencoded_form["swVer"] = "99.999.999.999"
3 - Save the file and start the program using:
Code:
mitmproxy -s unlock.py

4 - A port 8080 will open on your computer and now with your cell phone connected to the same network as your computer you must go to the wifi settings and then open the wifi and configure a proxy pointing to your PC's IP with port 8080
Note: use the ipconfig command if you don't know your computer's local IP on the network ex: 192.168.0.X or 10.0.0.X

5 - After configuring the proxy via wifi, you must install the Asus Unlock App and carry out the unlocking process. If everything goes well, the error message will not appear and your phone will be restarted and FORMATTED



ROOTING
Steps:
1 - After successfully unlocking the bootloader, you need to restart the phone in fastboot mode
2 - Now select the option restart in recovery mode via fastboot (note this part is important as you will not be able to install anything via fastboot)
3 - When you enter recovery you will see the option to enter fastbootd mode, select it and you will be ready to flash.
4 - If you followed the process from the beginning and already corrected the boot at the beginning of the tutorial, here you will just check which slot your system is in using the command:
Code:
fastboot getvar current-slot
5 - After knowing whether your system is in slot a or b, you must flash the boot according to slot boot_a or boot_b
Code:
fastboot flash boot_a magisk_patched_boot.img

Enjoy root and your unlocked cell phone.
