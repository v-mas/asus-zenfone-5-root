# ASUS Zenfone 5 root

Little script, which will root your ASUS Zenfone 5.

## Tested devices

- ASUS Zenfone 5 (T00F/T00J) with official WW-2.22.40.54 firmware

rooting for other versions has not been tested/completed

## Data safety

This script **will not overwrite any of your data** (files, photos, music, settings etc). It's totally safe.

Script **will overwrite**:
- dnx
- ifwi
- fastboot
- recovery

## Requirements

- adb
- fastboot

## Usage for linux

If you're on linux, run `root.sh` script from propper folder in terminal and follow instructions. Make sure that you have [enabled USB debugging mode](#enabling-usb-debugging-mode) in your phone.

## Usage for non-linux systems (Windows etc.)

I don't have time for develop scripts for other systems, but you can root your phone manually. Your device will be rebooted a few times in whole process.

1. Download [the rooting script](https://github.com/sigo/asus-zenfone-5-root/archive/master.zip) (about 53.4MiB).
2. Extract downloaded package.
3. [Enable USB debugging mode](#enabling-usb-debugging-mode) in your phone.
4. Connect your phone with computer.
5. Open terminal in extracted `asus-zenfone-5-root/{version}` directory (you don't need reboot your phone manually, just execute following commands).
6. Reboot to bootloader.

    ```shell
    adb reboot bootloader
    ```

7. Unlock fastboot.

    ```shell
    fastboot flash fastboot root/fastboot.img
    fastboot reboot-bootloader
    ```

8. Unlock bootloader (**this can take up to 3 minutes**, please be patient).

    ```shell
    fastboot flash dnx vanilla/dnx_fwr_ctp_a500cg.bin
    fastboot flash ifwi root/ifwi_ctp_a500cg.bin
    fastboot reboot-bootloader
    ```

9. Root phone (**an error during this part is normal** - just ignore it).

    ```shell
    fastboot flash recovery root/recovery.img
    fastboot flash update root/dummy.zip
    adb reboot bootloader
    ```

10. Restore vanilla files.

    ```shell
    fastboot flash fastboot vanilla/fastboot.img
    fastboot flash recovery vanilla/recovery.img
    fastboot flash dnx vanilla/dnx_fwr_ctp_a500cg.bin
    fastboot flash ifwi vanilla/ifwi_ctp_a500cg.bin
    fastboot reboot
    ```

All done, enjoy your rooted phone.

## Enabling USB debugging mode

1. Go to system **settings**.
2. Click **about**.
3. Open **software information**.
4. Tap **build number** 7 times - until a pop-up hint informs you that you've entered the developer mode.
5. Return to **settings**.
6. Find and open **developer options**.
7. Select **USB debugging** and click **ok**.

## Authors

- Mateusz Jagiełło (http://sigo.pl)
- Vipin Arumugham (http://www.facebook.com/zenfoneindia)
- shakalaca (http://23pin.logdown.com/)


## Usefull links

[Youtube guide how to root lolipop zenfone 5](https://www.youtube.com/watch?v=x42SEGahCC0)

[rooting scripts mentioned in this video (and also available in their description and here as AsusZenfoneLollipopRootKit.zip)](https://drive.google.com/open?id=0ByzlvYYhluSdY1VSamptMzVfTTQ)

[Official site with updates and drivers](https://www.asus.com/Phone/ZenFone_5_A500CG/HelpDesk_Download/)

[Guide to install TWRP/PhilZ touch recovery](http://www.asuszenfoneblog.com/2015/04/install-twrp-philz-recovery-for-asus.html)
