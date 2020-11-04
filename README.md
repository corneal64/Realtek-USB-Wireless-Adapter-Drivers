# Realtek USB Wireless Adapter Drivers

### Realtek USB Wireless Adapter Drivers [rtl8188fu] [0bda:f179]

### For Kernel 4.15.x ~ 5.3.x (Linux Mint or Ubuntu Derivatives)

------------------

![Alt text](/realtek-usb-wireless-adapter.jpg?raw=true "Realtek USB Wireless Adapter")

------------------
For ARM architecture, use [this branch](https://github.com/corneal64/Realtek-USB-Wireless-Adapter-Drivers/tree/ARM-driver)
------------------



## How to install

`sudo apt-get install build-essential git dkms linux-headers-$(uname -r)`

`git clone https://github.com/corneal64/Realtek-USB-Wireless-Adapter-Drivers.git`

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

## How to uninstall

`sudo dkms remove rtl8188fu/1.0 --all`

`sudo rm -f /lib/firmware/rtlwifi/rtl8188fufw.bin`

`sudo rm -f /etc/modprobe.d/rtl8188fu.conf`

