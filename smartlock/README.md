# Smartlock example on Raspberry Pi Zero W

1. Configure the Raspberry Pi Zero W
Let's start from the Raspberry Pi Zero W that will directly drive the smart-lock through the integrated digital I/O: we will install the Raspberry OS Lite Image and configure the I/O pins.

1. Insert your Micro-SD card into the slot of your computer

2. Use the Raspberry Imager tool and select Raspberry Pi OS (Other) > Raspberry Pi OS Lite (32bit) and flash it to your card
https://www.raspberrypi.org/software/

3. Extract and insert again your micro-sd card, open the folder /boot on the card, create and save an empty file named ssh to enable ssh connection to your Raspberry

4. Create a wpa_supplicant.conf file and paste the following code, replacing the placeholders with your wifi network name and password:


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
