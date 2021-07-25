# Realtek USB Wireless Adapter Drivers [JETSON PLATFORM]

> Added Jetson Nano Support (kernel 4.9.x) - 24/07/2021

> Tested also in Jetson TK1 (kernel 3.10.x) - 25/07/2021


### Realtek USB Wireless Adapter Drivers [rtl8188fu] [0bda:f179]

------------------

![Alt text](/realtek-usb-wireless-adapter.jpg?raw=true "Realtek USB Wireless Adapter")

------------------
## [For Jetson TK 1 Only] Run this following command
`cd /usr/src/linux-headers-$(uname -r)`

`sudo make modules_prepare`


## How to install
`cd ~`

`sudo apt-get install build-essential git dkms`

`git clone -b ARM-driver https://github.com/Muhammad-Yunus/Realtek-USB-Wireless-Adapter-Drivers.git`

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

