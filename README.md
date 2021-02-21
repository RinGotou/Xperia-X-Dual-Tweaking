# Xperia X Dual (F5122/suzu) Tweaking

## Celluar/Calling
Sony introduced VoLTE support for this device in Android 7.0 firmware, but this device doesn't sell this device in China mainland, so I can't use VoLTE on this phone for a long time.
### Android 7.0/7.1
I try to enable VoLTE in Android 7.1 firmware by:

- copying *.mbn file into /system/etc/customization/modem 
- adding config and layout APK in /oem for China Mobile

but I failed; the VoLTE option doesn't show anymore.(If I succeed in the future I will add info about this)

### Android 8.0
Flash these contents from Xperia XZs(CT_v1_xzs.zip) from [_this thread_](https://forum.xda-developers.com/t/trying-to-figure-out-how-to-enable-volte-wifi-calling-on-x-compact.3877692/) can easily enable VoLTE feature for China Mobile and China Unicom. The config in this package indicate software to use two existing mbn file inside /system/etc/customization/modem, so we don't need to add files into /system.

But this package will modify your device boot animation into Xperia XZs version, and change some system prop value (e.g. ro.product.*). For restoring, we need to backup two files and copy them into original location after flashing:
- /oem/media/bootanimation.zip
- /oem/system-properties/cust.prop

NOTICE:Do not restore /oem/system-properties/config.prop, my device cannot pass CTS profile checking (with magisk hide enabled) because of broken value of ro.product.name / ro.product.device / ro.product.fingerprint
(maybe).

## Debloating
Yes, Sony puts MANY BLOATWARE into their smartphone product.

But don't use [_this tool from XDA_](https://forum.xda-developers.com/t/mm-n-o-ub-combined-system-oem-debloat-script-v1-8-03-dec-2017.3527866/) to debloat your device in any version of firmware. It deletes too many stuffs and causes some error from remain applications.(I met sudden exitings and "stop working" message many times)

This repo contains a "debloat.sh". It just deletes some well-known bloatware(such as what's new, facebook and AVG Protection) and EOL application. Copy this script into device, boot into TWRP, mount /system, and run it.

## Non-stock Firmware/ROM

