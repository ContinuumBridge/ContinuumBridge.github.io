---
title: Configuring a Raspberry Pi
---
# Configuring a Raspberry Pi
This tutorial introduction will focus on on writing an app for a Raspberry Pi using the Raspbian operating system. A basic knowledge of Linux is necessary in order to be able to undertake this tutorial, although more comprehensive information is provided for anything that is specific to the Raspberry Pi. Instructions are given on the assumption that a command-line interface is being used, although many operations can be completed using a graphical user interface if this is preferred. In addition, all bridge apps must currently be written in Python, although APIs for other languages may be provided in future. This means that a reasonable knowledge of Python is necessary. However, anyone with a familiarity of any programming language should be able to follow the example code walk-through and even make changes to the example app.

## Signing-up for a ContinuumBridge account
You can't get very far with developing a bridge-app, or even using a bridge-app, without having a ContinuumBridge account, so we suggest you start by signing up for one. All you need to do is go to http://www.continuumbridge.com and click on the Sign-up/Sign-in button at the top of the screen. You'll see a screen like the one below. Press Sign-Up and fill in your details. You will be sent an email to confirm that the email address you provided is real, and after you have clicked on the link to confirm this, you will be able to log in.

![continuumbridge-platform](/pictures/continuumbridge-platform.jpg)

Once you've logged-in, you can look around, but you won't be able to do anything of use until you have configured a Raspberry Pi, as outlined below. 

## The Raspberry Pi
For hardware, you will need a Raspberry Pi 1 Model-B or Model-B+ or a Raspberry Pi 2 Model B, a power supply and SD Card (minimum 4 Gbytes – see below). In addition, in order to connect to both Bluetooth and WiFi devices, you will need WiFi and Bluetooth 4.0 USB dongles. To connect to Z-wave devices you will need a Razberry Z-wave board. Guidance about hardware is given in the Hardware section, [here](http://continuumbridge.readme.io/v1.0/docs/hardware). Your Raspberry Pi will need to be connected to the Internet via either Ethernet, WiFi or a 3G dongle. Plenty of information about the Raspberry Pi can be found on the web. A good place to start is http://www.raspberrypi.org/. 

As the Raspberry Pi is being used as an embedded platform, you don't need a screen, keyboard and mouse most of the time and most users will connect to it from another computer using secure shell (ssh), but it is possible to connect a keyboard, screen and mouse to the Raspberry Pi and develop without any other computer at all. 

There are now two ways of proceeding. Either you can download out pre-prepared image and copy it onto an SD card, or you can install our cbridge software and the other software that it requires onto an existing Raspberry Pi running Raspbian. To get going quickly and easily, we recommend the former. The instructions for doing this are here:

> **Use this link to download a pre-configured Raspberry Pi SD card image:**
> https://github.com/ContinuumBridge/cbridge_image

If you choose to download this image, please skip the rest of this page. Otherwise, the rest of this page tells you how to configure an existing Raspberry Pi as a ContinuumBridge bridge.

With newer software releases, some devices, notably the Razberry Z-Wave board and Bluetooth USB dongles, have become more sensitive to versions of software. We therefore recommend that you start with a new SD card and download Raspbian Jessie from here:

    https://www.raspberrypi.org/downloads/raspbian/

Follow the instructions for expanding the image to fill your SD card and set the time zone to your local time zone.
 
Next, ensure that your Raspberry Pi is up-to-date with the latest software releases, using the following commands:

    sudo apt-get upgrade
    sudo apt-get update
    sudo reboot
    
> **rpi-update** 
> Do not type "sudo rpi-update" as is suggested in some blogs.

Next, copy and paste the following command into a shell:

    sudo rpi-update 33a6707cf1c96b8a2b5dac2ac9dead590db9fcaa
    
After this you'll need to reboot the Raspberry Pi again.

This downgrades the Linux kernel to release 3.18.16 from the release 4 kernel that is used by Raspbian Jessie. This is a requirement for the Bluez software used by Bluetooth LE. It is hoped that this will not be required in future.

Log in to the Raspberry Pi again.

If you want to use Z-Wave devices, now is the time to install the board and Z-Wave software. Install a Razberry board (see: http://razberry.z-wave.me/) and then install the Razberry software, using the command below. This takes a few minutes and you need to give answers to a couple of yes/no questions during the process. You should install the specific version of the z-wave.me software that has been tested with the latest cbridge software, using this command:

    wget -q -O - razberry.z-wave.me/install/v2.0.1 | sudo bash
    
cbridge has also been tested with older versions of z-wave.me from v2.0.0, although we recommend using v2.0.1 as cbridge can take advantage of some of the newer features.

Now install cbridge by typing the following in your home (login) directory:

    git clone https://github.com/ContinuumBridge/cbridge.git
    sudo cbridge/setup
    
The cbridge install process will also install any software packages that are needed that are not currently installed on your Raspberry Pi and will take up to an hour, depending on the speed of your Internet connection and the model of Raspberry Pi, so we suggest you leave your Raspberry Pi and go and do something else. 

> **Starting again** 
> You shouldn't ever repeat this process on the same Raspberry Pi, but just in case you've done something like copy an SD card and want to configure a new Raspberry Pi, either first delete the cbridge directory (rm -r cbridge) before starting the above process, or go into the cbridge directory (cd cbridge) and type: git pull. This will ensure that you're using the latest version of the setup script. Also, type: sudo rm -r /opt/cbridge to remove any existing copy of the cbridge software.

The cbridge software is installed in the directory /opt/cbridge. The only directory that you should edit files in here is /opt/cbridge/thisbridge. The contents of all other directories is overwritten by software upgrades.

Once the installation process has finished, you can connect your Raspberry Pi bridge to your ContinuumBridge account. If your ContinuumBridge user name (email) is me@myself.com, your password is mypassword (never actually use this as a password!) and you want to call your bridge mybridge, you would type the following:

    cb --bridge post --name mybridge --user me@myself.com --password mypassword
    
If you don't want your password to be visible, leave off the “--password mypassword” part and you will be prompted for the password. You can choose whatever you like as a bridge name, but a good choice is the same as the host name of your Raspberry Pi, which is by default raspberry and can be found by typing:

    cat /etc/hostname
    
> **Helpful names for bridges** 
> As an aside, particularly if you have more than one Raspberry Pi, it can be helpful to change the hostname, which is what will be displayed at the prompt. To do so, edit /etc/hostname and /etc/hosts and change the word “pi” for your preferred hostname.

> **Congratulations** 
> This has now created a standard bridge that is capable of connecting to Bluetooth and Z-Wave devices and running apps.

[Next, The ContinuumBridge portal ...](the-continuumbridge-portal)

[Back to Index](document_list.html)
