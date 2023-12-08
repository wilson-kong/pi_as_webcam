# Raspberry Pi as Webcam

This is intended to help you turn your [Raspberry Pi Zero 2 W](https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/) into a webcam via USB, aka a USB gadget. Once setup, you should be able to plug your pi into the computer (or any other devices) through a USB cable.

I made this after following a tutorial but getting the error:
> "USB device not recognized. The Last USB device you connected to this computer malfunctioned and Windows does not recognize it. Windows Explorer"

## Table of contents
1. [TL; DR](#tl;dr)
2. [Step by step](#step_by_step)
3. [References](#references)

## Step by Step <a name="step_by_step"></a>

This was done basing off this tutorial: 
https://www.raspberrypi.com/tutorials/plug-and-play-raspberry-pi-usb-webcam/

Go follow the following tutorial until you get up to the `/etc/rc.local` stage, we'll use `systemd` instead.


Go to this tutorial and then come back when you get up to the part where it tells you to do this:
```bash
$ sudo nano /etc/rc.local
```
Tutorial: https://www.raspberrypi.com/tutorials/plug-and-play-raspberry-pi-usb-webcam/

Don't make changes to the `/etc/rc.local` file.





## TL; DR <a name="tl;dr"></a>
Go follow the following tutorial until you get up to the `/etc/rc.local` stage, we'll use `systemd` instead.

Tutorial: https://www.raspberrypi.com/tutorials/plug-and-play-raspberry-pi-usb-webcam/

Don't touch the `/etc/rc.local` file. Instead go:
```bash
sudo nano /lib/systemd/system/pi_webcam.service
```
```bash
[Unit]
Description=Boot up Pi camera
After=multi-user.target

[Service]
ExecStart=/home/<username>/.rpi-uvc-gadget.sh &

[Install]
WantedBy=multi-user.target
```

replace `<username>` with your username.

```bash
sudo systemctl daemon-reload
sudo systemctl pi_webcam.service
sudo reboot
```

## References <a name="references"></a>
https://www.raspberrypi.com/tutorials/plug-and-play-raspberry-pi-usb-webcam/

https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files