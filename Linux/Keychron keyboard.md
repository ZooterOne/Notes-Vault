# Enable connection for Keychron Launcher

```
lsusb
```

list the usb device and note the ID for the **Keychron** keyboard (`ID <vendor>:<product>`).

```
sudo touch /etc/udev/rules.d/99-vial.rules
echo 'KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="<vendor>", ATTRS{idProduct}=="<product>", MODE="0660", GROUP="users", TAG+="uaccess", TAG+="udev-acl"' | sudo tee -a /etc/udev/rules.d/99-vial.rules > /dev/null
```

create a new **UDEV** rule, using vendor and product ID.

```
sudo udevadm control --reload-rules && sudo udevadm trigger
```

load the **UDEV** rules.


echo 'KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="3434", ATTRS{idProduct}=="0521", MODE="0660", GROUP="users", TAG+="uaccess", TAG+="udev-acl"' | sudo tee -a /etc/udev/rules.d/99-vial.rules > /dev/null

# Revert changes once Keychron Launcher done

```
sudo rm /etc/udev/rules.d/99-vial.rules
sudo udevadm control --reload-rules && sudo udevadm trigger
```
