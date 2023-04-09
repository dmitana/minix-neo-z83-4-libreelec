# Minix Neo Z83-4 LibreElec

## WiFi
WiFi is not working by default. Use the following instructions to make it work:

1. Download `4345r6nvram.txt`.

1. Copy `4345r6nvram.txt` to the device via SSH.
   ```
   scp 4345r6nvram.txt root@192.168.X.XXX:~/
   ```

1. File `4345r6nvram.txt` has to placed in `/lib/firmware/brcm` but
   `/lib/firmware` is a volatile directory in a ramdisk and re-created on every
   boot in LibreElec. So you have to crete `/storage/.config/firmware/brcm`
   directory.
   ```
   mkdir -p /storage/.config/firmware/brcm
   ```

1. Copy `4345r6nvram.txt` and rename it.
   ```
   cp 4345r6nvram.txt /storage/.config/firmware/brcm/brcmfmac43455-sdio.tx
   ```

1. Reboot and WiFi should work.

### Sources

* [WiFi
  driver](https://theminixforum.com/index.php?threads/linuxmint-19-and-do-not-detect-wifi-network-card.376/)
* [LibreElec firmware
  directory](https://forum.libreelec.tv/thread/21125-raspberry-pi-4-not-save-the-modifications/)
