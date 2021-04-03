# Smartlock example on Raspberry Pi Zero W (April 2021)

A. Configure the Raspberry Pi Zero W

Let's start from the Raspberry Pi Zero W that will directly drive the smart-lock through the integrated digital I/O: we will install the Raspberry OS Lite Image and configure the I/O pins.

1. Insert your Micro-SD card into the slot of your computer

2. Use the Raspberry Imager tool and select Raspberry Pi OS (Other) > Raspberry Pi OS Lite (32bit) and flash it to your card
https://www.raspberrypi.org/software/

3. Extract and insert again your micro-sd card, open the folder /boot on the card, create and save an empty file named ssh to enable ssh connection to your Raspberry

4. Create a wpa_supplicant.conf file and paste the following code, replacing the placeholders with your wifi network name and password:

```
# Replace with your ISO country code, e.g. US, IT, GB, AU, etc... 
country=YOUR_2_CHARACTERS_COUNTRY_CODE

network={
       # Set your wifi network name - 5Ghz network are not supported!
       ssid="YOUR_NETWORK_NAME"
       # Set your wifi password here
       psk="YOUR_NETWORK_PASSWORD"

       key_mgmt=WPA-PSK
    }

ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
```
5. Save the file and put the micro-sd card into the Raspberry card slot, connect the power to the Raspberry and turn it on

6. Login into the Raspberry with:

```
ssh pi@raspberry.local # use "raspberry" as a password!
```
if this doesn't work, then you will be required to access your router web interface and look for the list of connect wifi clients, locate "raspberrypi" in the list, take note of it's IP address and replace raspberry.local with the IP address in the ssh command above (also you should make sure that it will be always assigned the same ip by the router - check out this video as an example).

7. Before going on it's recommended to run sudo apt-get update and sudo apt-get upgrade to ensure your Pi system is up to date.

Install required packages and clone the iotexlab/iotex-arm GitHub repository from IoTeXLab Delegate:

```
sudo apt install git python3-gpiozero -y
git clone https://github.com/iotexlab/iotex-arm.git
```






```
sudo apt install golang-go
go get github.com/fullstorydev/grpcurl
go install github.com/fullstorydev/grpcurl/cmd/grpcurl
export PATH=$PATH:$HOME:/go/bin:$HOME/iotex-arm/smartlock/bin
sudo iotex-arm/smartlock/bin/configGpio
switchlock 1
switchlock 0
check
```
