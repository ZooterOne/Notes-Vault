```
dd if=/dev/<device> of=<file>.img
```
generate image file.
```
dd if=/dev/cdrom of=<file>.iso bs=2048
```
generate iso file.
```
dd if=<file> of=/dev/<device>
```
restore image.
```
sudo dd if=<file> of=/dev/sd<X> bs=4M status=progress
```
generate bootable usb drive.
