---
title: Getting Started
---
# Getting Started
This is the documentation for the ContinuumBridge technology platform. This is the underlying platform used for the ContinuumBridge [Wisp](http://www.wisp.site) and [Spur](http://www.spur.site) services. It is also available for anyone to use as a means of connecting and managing a variety of Internet of Things (IoT) devices. For more general details about ContinuumBridge and our services, please visit [our main website](http://www.continuumbridge.com).

The ContinuumBridge platform enables anyone to connect wireless devices to a Raspberry Pi or similar device and write apps that use them. The key benefits of this are:

* You own and control your devices and decide who else you are going to allow to access them.
* Developers can write apps that work in the same way, regardless of how the devices are connected (eg: Bluetooth, Z-Wave, ZigBee or WiFi).
* Anyone can write an app and put it in the ContinuumBridge app market.

oday, we support devices connected by Z-Wave, Bluetooth and USB. There are a limited number of these at the moment (see [Devices](doc:devices)), but more are being added all the time, and you can easily add your own devices. The app market is in its infancy. As yet, there is no way of you being able to make apps available on the open market, but you can make them available to named ContinuumBridge accounts; for example, an app can be deployed any number of times within your own organisation on a Raspberry Pi or other devices that will run the ContinuumBridge software. We have tested the platform on SolidRun's HummingBoard and PCs running Ubuntu as well as the Raspberry Pi. 

The ContinuumBridge platform consists of software that runs on a Raspberry Pi or other platform (cbridge) and the cloud-based bridge controller, together with a web portal that is used for connecting devices to Raspberry Pies and managing them. We also have a client interface, which can be used to connect to any web API (REST and Websocket are supported).

The ContinuumBridge documentation is extensive, but you don't need to read it all at once. Here's a guide.

If you have a configured Raspberry Pi and have some devices, you'll need to read [The ContinuumBridge Portal](doc:the-continuumbridge-portal) to learn how to connect and manage them. This section is applicable to anyone who just wants to use the ContinuumBridge platform, as well as those who want to develop for it.

[ContinuumBridge Platform Overview](doc:overview) is a description of how the platform works and how the various bits fit together. A developer needs to be familiar with this.

[Configuring a Raspberry Pi](doc:writing-a-bridge-app-on-a-raspberry-pi) takes you through how to use a Raspberry Pi as a bridge. The steps here tell you how to install at the necessary software or, soon, you'll be able to download a pre-configured image.

You'll need some devices to connect to your bridge. [Devices](doc:devices) tells you which devices have been tested and have ContinuumBridge adaptors. We'll be adding to this list.

The other sections are for those who want to develop apps, or add new devices to the platform. We suggest you start with [A Raspberry Pi App Example](doc:writing-an-app-on-the-raspberry-pi). There are a lot of similarities between writing apps and device adaptors.

[Next page ...](doc:overview)
