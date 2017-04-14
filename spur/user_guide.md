---
title: Spur User Guide
---
# Spur User Guide
## Introduction
The basics of connecting a Spur button and selecting an application (screenset) for it are covered in the [Quick Start Guide](spur_overview.md). It is assumed that if you are reading this document you will already be familiar with this. The things that are covered in this document are:

* [Overview of the Spur Portal](#overview-of-the-spur-portal)
* [Creating Screensets](#creating-screensets)
* [Spur Button Operation](#spur-button-operation)

## Overview of the Spur Portal
### Terminology

The Spur Portal, [portal.spur.site](http:www.portal.spur.site) enabled configuration and montoring of Spur buttons. The essential ingredients of the Spur portal are:

* Screensets. A screenset is essentially a flow chart that defines what text appears of the display of a button, how the button moves from one display to another (eg: by pushing on the left side) and what actions are triggered by these changes. Here is an example of a screenset which causes a text message to be sent when someone pushes the button. 

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ToiletScreenset.jpg">

</p>

* Buttons. Each physical button is registed on the Spur portal and assigned a screenset.
* Lists. Buttons are grouped together in lists. List normally contain buttons of a similar function, usually in the same location. The example below shows bays in a warehouse. 

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/WarehouseList.jpg">

</p>

### Using the Spur Portal
#### The Lists Screen
When you first sign in to the Spur portal, the screen will look like this:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/LoginScreen.jpg">

</p>

This shows a blank list, with the navigation menu on the left-hand side. From here you can:

* Add buttons, as described in the [Quick Start Guide](portal_setup.md).
* Change the name of the list by clicking on its name ("List A", at the top left) and deleting/typing.
* Set the defaults for the list, by clicking on "DEFAULTS". The defaults consist of a screenset name, a default email address and a default phone number (for SMS).
* Create new lists, by clicking on "+ ADD LIST".
* Go to the users screen, the screensets screen or sign out, by clicking on the relevant buttons in the navigation menu.

#### The Users Screen
This screen enables you to add an remove additional users for your organisation. Currently, all users within an organisation have the same privileges. The main resons for adding other users are so that each can have their own password and because some can be give read-only access. Read-only access is particularly useful if you want to be able to display a list of buttons on a tablet computer, for example, so that lots of people can see it, but not make changes. 

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/AddUsers.jpg">

</p>

In this screen, click on ADD USER to add a new user. You can select whether a user is read-only either when they are added, or by clicking the check box afterwards. You can also change passwords and delete users.

### The Screensets Screen
This contains a list of your screensets. You can add new screensets, edit screensets and delete them. If you want to change the name of a screenset, just click on the name and type.

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ScreensetsScreen.jpg">

</p>

[Return to top of screen](#introduction)

## Creating Screensets
A good way to learn about creating screensets is to watch this [YouTube video](https://www.youtube.com/watch?v=Sum0OgJBZU8&t=222s). The process is fairly intuitive. This section contains some information that is not in the video.

When you add a new screenset, you can choose to create it from an existing template, or select "None" on the pull-down menu if you want to start with a blank screen. Templates consist of those provided by ContinuumBridge, as well as all your own existing screensets. Once you have added the screenset, edit it (it will appear at the bottom of the list). If you didn't use a template, the editor screen will initially look like this:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ScreensetEditor1.jpg">

</p>

The box with the word "Start" in it is called the start marker. This will be used to indicate your starting screen. For example, if you wanted the screen to normall say: "Please push here for attention", and then when the button was pushed send a text message and change the screen to say: "Someone will be with you soon", then the "Please push here" screen would be your start screen.

The start marker, like all other icons in a screenset, has two symbols on it:

* The move symbol, "+". Click on this and hold it an you will be able to move the icon around the screen.
* The delete symbol, "x". This deletes the icon. It's a bad idea to delete the start marker (and there's currently nothing from preventing you from doing so).

A screenset is built from screens and alerts. You can add these by click on the relevant buttons at the top-right of the screen. 

### Screens
There are currently three types of screen: normal, with delay and with LED, as shown below:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ScreensetEditorScreens.jpg">

</p>

In each case, you type what you want to appear on the button's screen in the box, as described below. 

The delay screen allows you to instruct the button to display that screen for a time period, specifed in seconds, before moving on to the next screen. Type to delay in the delay box. Delays are in increments of two seconds (they will be rounded down if you use an odd number) and the maximum delay is 508 seconds. Typically, you may use this feature to say something like: "Thank you for your feedback", before going on to another screen.

The "with LED" screen displays status indicators, which look like LEDs, in a button list, as shown in the list of bays in the warehouse further up this page. Click on the "LED" to change its colour between green, amber and red. The number of "LEDs" displayed on a list next to the button corresponds to the number of colours that you have used. If you have only used one colour, say green, then only one "LED" will be displayed and it will be green when the button is showing a screen with an "LED" on it. 

### Alerts
There are two types of alert: email and SMS, as shown below:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ScreensetEditorAlerts.jpg">

</p>

An email alert will cause an email to be sent to the email addresses in the "Email address" box, with the message in the message box. You can have up to 8 email addresses, separated by commas. 

#### Note. 
You do not need to include the button name in the message. If the message in the email alert box says: "Cleaing requested", for example, and the button is called "First floor washroom", then an email will be sent from "Bridges <bridges@continuumbridge.com>" to be email addresses in the list with the subject "First floor washroom: Cleaning requested - 21:26:44, 11-04-2017". The time and date are appended as some email clients group all emails with the same subject together, which some users found lead to them being overlooked.

### Joining it all Together
A screenset is made by joining together screens and alerts. Screens has four hollow circular connectors, two on the left side and two on the right. These represent pushing the left or right side of the button (top connectors) and double-pushing the left or right side (bottom connectors). Alerts have a similar connector on their lower side. Also, both screens and alerts have a solid circular connector on their top side. If you want a single left push on a screen to cause an email to be sent, for example, click on the top-left connector of the screen, drag your cursor to the top connector of the email alert and release, this will create the connection shown below:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ScreensetEditorFirstConnection.jpg">

</p>

In most cases, it doesn't matter if someone pushed the left or right side of the button, so connect them both, as shown below. Here, we've also added a delay, which causes the Spur button to display a message for ten seconds before going back to the start screen.

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/ScreensetEditorFirstScreenset.jpg">

</p>

### Creating More Complex Screens
#### Fonts
There are two font sizes. The default is the "small" font, which uses a 14x20 box for the largest characters. To use the "large" font (18x26), put a * character at the start of the line that you want to use it. Eg:

    *Push here if
    *this washroom
    *needs cleaning
    
 will be displayed using the large font. The * is not displayed, as shown below:
 
 <p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/PushHereIfWashroomNeedsCleaning.jpg">

</p>
 
Each font has the same character set. For those who are interested in such things, this corresponds to characters that are stored in a single byte in utf-8. This basically means Western European characters.

The number of characters that can be displayed on a line depends on which characters they are. The fonts are proportionately spaced, so, for example, an "m" is wider than an "i". The screenset editor will not allow you to type more characters on a line than can be displayed on the button screen. Once you've overrun the screen width, you'll notice that characters start being deleted.

#### Left and Right
If left and right button pushes are used for different purposes, you can display text in boxes on the left and right sides of the screen, as in this example:

    Does this washroom
    need cleaning?
    Push left | Push right
    for NO| for YES
    
This produces the following display on a button:

 <p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/DoesThisWashroomNeedCleaning.jpg">

</p>

There are rules as to where boxes can be placed:

* There are a maximum of four lines of text on the screen.
* All four can be full width.
* The first line can be full width, with boxes around left and right on the second, third and fourth.
* The first and second lines can be full width, with boxes on the third and fourth.
* The first three lines can be full width, with a box on the fourth.

### "Reconvergent" Screensets
For reasons to do with the internal workings of Spur, the screenset on the left, below, will not function as you expect (two emails will always be sent). Instead, use the form on the right.
    
<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/Reconvergent.jpg">

</p>

[Return to top of screen](#introduction)

## Spur Button Operation
This section describes the operation of the Spur button itself. Most of the time, the button just does what it is told by the Spur portal. However, there are certain features that can be accessed by pushing the button for more than three seconds.

### Communication with the Bridge
In order to achieve a long battery life, a Spur button is in standby mode most of the time. In theory, a battery would last over 40 years when a battery is in standby mode. Of course, energy is drained from the battery every time the display changes or the button communicates over the wireless network with a bridge. For this reason, button normally only wake up either:

1. When they are pushed.
2. Every 12 hours, so that the bridge knows the button is still alive.

Thus, if you make a change on the portal, for example changing the text on a screenset, it may take up to 12 hours for the button to change, unless you go and push the button. (Actually, in some circumstances the button can wake up a lot more often. The main reason is if it is expecting to receive an update message. This is covered in the Developers' Manual). 

If a button tries to communicate with its associated bridge (either because it's been pushed or its' woken up by itself) and doesn't get a response, it will try again several times over a 10 minute period and then start trying to reconnect to the bridge. It tries to connect quite often at first (after 10 minutes, 30 minutes, 1 hour), but eventually only tries every 12 hours. A button will always connect to a bridge when it next sees one. What sometimes happens, though, is that when people are experiementing with buttons, they may turn bridges off and on to move them around or move buttons from the coverage area of one bridge to another. If you do this, you can generally force it to try to connect again by pushing it, but if this is within 10 minutes of when it was last in contact with a bridge and you are in a hurry, you may need to reset it (see below).

### The Information Screen
In normal operation, if you hold the button down for more than three seconds, it will display the message: "Working ... Please wait" for a few seconds and then show the following screen:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/InfoScreen.jpg">

</p>

This shows:

* The node ID, which is the number that you enter into the portal.
* Ver, the software version of the button. This could be useful if you are experiencing problems.
* Battery, the battery voltage. This should be above 3.0 Volts in normal operation.
* Bridge, the ID of the bridge that the button has used to measure its signal strength. Note that buttons don't necessarily connect to the bridge with the strongest signal strength. They use the first one that they can see.
* The Received Signal Strength Indicator (RSSI). This is the value that is used to set the number of bars on the signal strength indicator on the portal. Anything greater than -100 dBm is OK. Note that it's a negative number, so -60 dBm is a strong signal, -100 dBm is quite weak.

### Resetting
The information screen, described above, is displayed for about five seconds and then the button goes back to its start screen. If during this five seconds you double-push on the right hand side of the button it will reset to its factory default settings. 

There is another way of resetting, which is to hold the button for 10 seconds or longer, release and then double-push on the right hand side. 

If a button is not in contact with a bridge, after a while it will display the message: "Communication problem. Button not in use". In this state, you will probably need to use the 10 second push method. If the button has recently become disconnected, as may happen if you are experimenting, we advise using a 20 second push (because when you push down it is likely to start trying to send a message to the bridge, which takes about 15 seconds, during which time it will not notice if you release the button).

[Return to top of screen](#introduction)

[Go to Spur main page](spur_overview.md)
