# tbs5520 patch

This is a patch for Turbosight TBS5520 USB2 DVB-T/T2/C/S/S2 device (Rafael Micro r848 tuner).
It should be considered Beta quality.
This patch should be applied right after rtl2832 or you may need to adjust Kconfig and Makefile to be able to build it.
It has been applied against kernel version 3.4.103 and armbian legacy kernel 3.4.111.
The driver should work on A10 / A20 / H3 devices.

Applying the patch (diff patch)
==================

* clone this repo
git clone https://github.com/avafinger/tbs5520.git

* move the tbs5520.patch to:
linux-sunxi (a10/a20) or h3-wip (H3)

* run:
patch -p1 < ./tbs5520.patch
patching file drivers/media/common/tuners/r848.c
patching file drivers/media/common/tuners/r848.h
patching file drivers/media/common/tuners/r848_priv.h
patching file drivers/media/dvb/dvb-usb/Kconfig
patching file drivers/media/dvb/dvb-usb/Makefile
patching file drivers/media/dvb/dvb-usb/tbs5520.c
patching file drivers/media/dvb/dvb-usb/tbs5520.h
patching file drivers/media/dvb/frontends/avl6882.c
patching file drivers/media/dvb/frontends/avl6882.h
patching file drivers/media/dvb/frontends/avl6882_priv.h
patching file drivers/media/dvb/frontends/AVL_Demod_Patch_DVBCFw_.h
patching file drivers/media/dvb/frontends/AVL_Demod_Patch_DVBSxFw_.h
patching file drivers/media/dvb/frontends/AVL_Demod_Patch_DVBTxFw_.h


* remove the patch
rm ./tbs5520.patch

* config the kernel
enter menuconfig and set support for DVB_USB_TBS5520 or edit .config and manually add CONFIG_DVB_USB_TBS5520

* rebuild the kernel
If everything is OK and you get a kernel image , this patch did not break anything! :)

* reboot and plug in your device, and check dmesg

* if you build the driver as a module you should load the module:
modprobe dvb_usb_tbs5520
or
add it to /etc/modules

* Firmware
You should copy/move the firmware to the correct location: /lib/firmware/
cp dvb-usb-tbs5520.fw /lib/firmware/

Credits:
@cnxsoft - Firmware for the TBS5520






