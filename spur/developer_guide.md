---
title: Spur Developer Guide - RESTful API
---
# Spur Developer Guide
## Introduction
This guide describes some more advanced features of Spur, that will principally be of interest to developers who are integrating Spur with other back-end systems. It contains the following:

[Overview of API Calls Using the Email Alert](#overview-of-api-calls-using-the-email-alert) - A descritpion of the general-purpose RESTful API.

[Specific APIs](#specific-apis) - APIs to specific applications, such as the IBM Watson IoT Platform and InfluxDB.

[Dynamic Screen Updating](#dynamic-screen-updating) - How to update update the screen of the button from an API.

## Overview of API Calls Using the Email Alert
In a future release of the Spur portal, there will be more types of alert boxes. Currently all advanced functions are accessed by using key words (prefixed by a #) in the email alert box, as in the example below:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/RoadRunner.jpg">

</p>

This is a generic RESTful API call. Each of the email address boxes contains the following:

    #api rest={"method": "post", "url": "http://api.acme.com/buttons"}
    
and the message boxes contain:

    {"road_runner_once": 1}
    {"road_runner_twice": 1}
    
Spur recognises this as a request to make a RESTful API call. Both the text following the "rest=" in the email address and the message field must be legal JSON. In this particular example, an HTTP POST is done to the URL "http://api.acme.com/buttons" (which can be HTTP or HTTPS). The header is set to:

    {"Content-Type": "application/json"}
    
and the content from the called generated from the first alert box will be the following JSON:

    {
        "uid": "unique_string",
        "DeviceId": "list_name-button_name",
        "DeviceType": "screen_set_name",
        "road_runner_once": 1
    }
     
 where:
 
 * unique_string uniquely identifies a button and will be something like: "2xTwSyQ29mcb5x6M8".
 * list_name-button_name is the name of the list that the button is in, with any spaces replaced by underscores, followed by a hyphen, followed by the button name, with any spaces replaced by underscores.
 * screen_set_name is the name of the screen set that the button uses, with any spaces replaced by underscores.
 
If someone changes the screen set name, the list name or the button name, the fields that use them will change. The uid of a button will not change. It is worthwhile thinking about your application in determining which fields are used. In our experience, using the DeviceId field as the master reference is the most helpful, as it is likely to retain essential information about the button. For example, if you are implementing a workforce management system and you enforce list names and button names that identify the location uniquely, then the deviceId will enable you to propagate the location into your application. Eg:

    List name: "Building 1"
    Button name: "Male Second Floor"
    
 gives a DeviceId of: "Building_1-Male_First_Floor", which you could use to tell a cleaner to go to that washroom. 
 
 In most cases the message field will be some simple key-value pair, as in the above examples. There is one case that is treated by Spur as being special, which is of the form:
 
     {"key": "+1"}
 
 This causes the value that is actually sent over the API to start at zero, when the button is first created, and then incremented by one each time thereafter. This is most useful during testing or for a quick demo.
 
[Return to top of screen](#spur-developer-guide)
 
## Specific APIs
The RESTful API, described above, is fairly general-purpose, particularly if you have control of the server side. ContinuumBridge and its partners have developed a number of specific APIs. Although some of these are proprietary and not listed here, there are a number of APIs to popular back-end applications.
 
### The IBM Watson IoT Platform
Spur is fully-integrated with the Watson IoT platform. This is described fully is an [IBM developerWorks Recipe](https://developer.ibm.com/recipes/tutorials/using-continuumbridge-spur-buttons-with-the-ibm-watson-iot-platform/).
 
### InfluxDB
[InfluxDB](https://www.influxdata.com/) is a power and easy-to-use time-series database that is closely coupled with a number of useful tools, such as [Grafana](https://grafana.com/), a powerful visualisation and analytics tool. It works in much the same way as the RESTful API. In the email address box, put:
 
     #api influxdb={"method": "post", "url": "host_name/db/db_name/series?u=user&p=password"}
     
where:

* host_name is your InfluxDB host name.
* db_name is the database name.
* user is the InfluxDB user name.
* password is the InfluxDB password.

The message box will generally contain something like:
 
     {"value": 1}
     
To indicate that the button has been pushed, but you could use different words in place of "value" or multiple values, such as 1 for pushed and 0 for cleared. 

The values that you specify will be posted to:

     list_name-button_name
     
where list_name-button_name is the name of the list that the button is in, with any spaces replaced by underscores, followed by a hyphen, followed by the button name, with any spaces replaced by underscores.
 
*ContinuumBridge can provide access to a database within our own hosted InfluxDB, hosted in [InfluxCloud](https://cloud.influxdata.com/).* Please contact ContiuumBridge for details.

[Return to top of screen](#spur-developer-guide)

### IoT Stream
This is an API to the [Iot Stream](http://www.iotstream.io/) platform. It works in the same way as the RESTful API, but with IoT Stream-specific changes. Here is an example:

    #api iotstream={"method": "post", "url": "https://demo.iotstream.io/v2/json/updateSwitchValue"} 
    
and the message:

    {"user_key_api":"api_key","stream_key_api":"stream_key","key":0}
    
To use this API, you will need to have an IoT Stream account. ContinuumBridge can provide an introduction to IoT Stream, or you can contact IoT Stream directly [here](http://www.iotstream.io/contact/).

[Return to top of screen](#spur-developer-guide)

## Dynamic Screen Updating
In some applications you may want to update the screen of a Spur button dynamically. For example, if a button is used to report a fault, you may want to change the display as follows:

* Push here to report a fault with this appliance.
* Fault reported. Notifying maintenance.
* Fault reported. This appliance is scheduled for repair by 10:30.

The first two messages are programmed into the screenset, but the third is an update to the second. Here is an example of how to do this. In the email address box in an email alert, put the following:

    #api rest={"method": "get", "url": "http://api.acme.com/buttons"}
    
In the message box, put the following:

    {"message": ""}
    
and in the following screen, put the following:

    {{message}}
    Fault reported
    Notifying maintenance
    
Here's how it looks in the screenset:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/Dynamic.jpg">

</p>

The top email alert above the second screen contains a post to an API to register the fault. The email alert below the second screen contains the text from above.

Note that the word "message" can be any string that you like, but the string in the alert box message must match the string between the {{ and }} in the screen. 

In order to prolong battery life, Spur buttons usually only wake up when they are pushed or every 12 hours, to check for updates and notify their bridge and the Spur server that they are still alive. This behaviour is changed when a dynamic update is used. In this case, after the button is pushed, the button will wake up:

* 30 seconds after the push.
* After a further 30 seconds.
* After a further 60 seconds.
* After a further 120 seconds.
* After a furhter 120 seconds. 
* After a further 300 seconds.
* After a further 600 seconds.
* After a further 1200 seconds.
* After a further 1200 seconds.
* Thereafter, every 3600 seconds (1 hour).

Throughout this time, the Spur server will poll the API every 30 seconds, so that when the message is updated it will appear on the screen after the next wwakeup. The message can be updated multiple times while the button remains on the dynamic screen, with the wakeup interval being reset to the start of the above sequence after each update. For example, if the first update is made 220 seconds after the button is pushed, if the button screen will be changed 30 + 60 + 120 + 120 = 330 seconds after the button is pushed. The button could then be updated again 30 seconds after that, as if the button had been pushed again.

The above sequence of wakeups is considered a fair compromise between battery life and the ability to update the display in a timely manner for applications such as fault reporting and it is recommended that the delays are not shortened significantly. However, it is possible to override this behaviour by using an email alert, as shown below:

<p align="center">

  <img src="https://continuumbridge.github.io/spur/pictures/Dynamic2.jpg">

</p>

[Return to top of screen](#spur-developer-guide)

[Return to Spur documentation home](index.md)
