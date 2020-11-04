# Realtek USB Wireless Adapter Drivers

### Realtek USB Wireless Adapter Drivers [rtl8188fu] [0bda:f179]

### For Kernel 4.15.x ~ 5.9.x (ARM devices)

------------------

![Alt text](/realtek-usb-wireless-adapter.jpg?raw=true "Realtek USB Wireless Adapter")

------------------
## How to install

`sudo apt-get install build-essential git dkms linux-headers-$(uname -r)`

`git clone -b ARM-driver https://github.com/corneal64/Realtek-USB-Wireless-Adapter-Drivers.git`

`cd Realtek-USB-Wireless-Adapter-Drivers`

`sudo dkms add ./rtl8188fu`

`sudo dkms build rtl8188fu/1.0`

`sudo dkms install rtl8188fu/1.0`

`sudo cp ./rtl8188fu/firmware/rtl8188fufw.bin /lib/firmware/rtlwifi/`

------------------

## Disable power management and solve plugging/replugging issues

`sudo mkdir -p /etc/modprobe.d/`

`sudo touch /etc/modprobe.d/rtl8188fu.conf`

`echo "options rtl8188fu rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/rtl8188fu.conf`

------------------

## Disable MAC address spoofing

`sudo mkdir -p /etc/NetworkManager/conf.d/`

`sudo touch /etc/NetworkManager/conf.d/disable-random-mac.conf`

`echo -e "[device]\nwifi.scan-rand-mac-address=no" | sudo tee /etc/NetworkManager/conf.d/disable-random-mac.conf`

---------------

## How to uninstall

`sudo dkms remove rtl8188fu/1.0 --all`

`sudo rm -f /lib/firmware/rtlwifi/rtl8188fufw.bin`

`sudo rm -f /etc/modprobe.d/rtl8188fu.conf`

