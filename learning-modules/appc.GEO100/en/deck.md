theme:appcelerator-training

# Geolocation

Appcelerator Certified Developer (ACD) Training

---cover

# Geolocation

## Appcelerator Certified Developer (ACD) Training

--- 

# In this lesson, you will:

- Learn to use GPS positioning in your applications
- Use forward and reverse geo-coding

---section 

# GEOLOCATION

--- 

# Overview

Location APIs can be used for everything from device positioning to augmented reality applications. Taking location into account is mobile's killer feature.

![img](/assets/images/slides/12/image6.png)

--- 

# Geolocation Support in Appcelerator

- Detect if geolocation support is available
- Obtain once or continually monitor the user's location
- Device Compass (if available)
- Forward and reverse geo-coding

--- 

# iOS Geolocation

![img](/assets/images/slides/12/image7.png)

- Requires ```NSLocationAlwaysUsageDescription``` or ```NSLocationWhenInUseUsageDescription``` key
- Edit ```tiapp.xml``` ```ios/plist/dict```
- Check for authorization before using
- Primary configuration: Ti.Geolocation.accuracy property (e.g. ACCURACY_BEST)
- Also Ti.Geolocation.distanceFilter
- Based on those, iOS chooses provider and tunings

--- 

# iOS Geolocation –iOS 8

![img](/assets/images/slides/12/image8.png)

- Must ```Ti.Geolocation.requestAuthorization()`````
- ```Ti.Geolocation.AUTHORIZATION_ALWAYS```
- ```Ti.Geolocation.AUTHORIZATION_WHEN_IN_USE```

--- 

# Android Geolocation

- Three location modes:
  - Simple, Manual and Legacy (pre-Ti2.0)
- Simple: enable with accuracy = ACCURACY_HIGH or ACCURACY_LOW
- Manual: More control, more precision, more provider options

--- 

# Mobile Web Geolocation

- Browser must support W3C Geolocation spec
- Implementation & accuracy varies
- User must grant permission
- But, you can't change the message

--- 

# Geolocation Gotchas

- Continually monitoring GPS drains battery faster
- Android emulator: GPS might not be enabledEdit the AVD to add GPS support
- Android emulator: no default location
- Use monitor to send location
- Genymotion: enable GPS widget 

--- 

# iOS / Mobile Web Geo Demo

- iOS: Kitchen Sink — Phone > Geolocation
- Mobile Web: Kitchen Sink — Phone > Geolocation

--- 

# Android Geo Demo

Project: [https://github.com/appcelerator-training/AndroidGeo](https://github.com/appcelerator-training/AndroidGeo)
Runs on device (not emulator)
Shows Legacy, Simple & Manual modes

--- 

# Summary

- Learned to use GPS positioning in your applications
- Used forward and reverse geo-coding

---section

# Questions?