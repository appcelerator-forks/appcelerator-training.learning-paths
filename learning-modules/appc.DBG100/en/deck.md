theme:appcelerator-training

# Debugging

Appcelerator Certified Developer (ACD) Training

---cover

# Debugging

## Appcelerator Certified Developer (ACD) Training

--- 

# In this lesson, you will:

- Debug the JavaScript of a Titanium app using Studio tools
- Debug Android apps using API tools
- Debug iOS apps using API and operating system tools
- Debug Mobile Web apps

---section 

# STUDIO TOOLS & TECHNIQUES

--- 

# Debugging

![img](/assets/images/slides/15/image6.png)

- Breakpoints, stepping through code, conditional breakpoints
- Variables - examining variable state and affecting run-time variable values

--- 

# Setting Breakpoints

![img](/assets/images/slides/15/image7.png)
![img](/assets/images/slides/15/image8.png)

- Margin-click method:
  - Double-click margin
  - Do debug build
Debugger statement
  - Add debugger statement
  - Do debug build

--- 

# Step-through Debugging

![img](/assets/images/slides/15/image9.png)

- Step Into, Over, & Return buttons
- Resume & Terminate buttons

More info: [http://docs.appcelerator.com/titanium/latest/#!/guide/Debugging_in_Titanium_Studio](http://docs.appcelerator.com/titanium/latest/#!/guide/Debugging_in_Titanium_Studio)

--- 

# Debugging on Device

- iOS: must have proper provisioning profiles set up
- iOS: must be on same WiFi network
- Android: must be USB tethered
- See Titanium Studio docs for additional details

--- 

# Try It

Debugging AlloyHunter

- Add a breakpoint to the Fugitives.js controller as the first statement in the table event listener.
- Do a debug build of the app to the simulator/emulator.
- Click a row in the fugitives table.
- Examine the variables in memory, then step through a few lines of code.

---section 

# LIVEVIEW

--- 

# Using LiveView

![img](/assets/images/slides/15/image12.png)

- Appcelerator Studio allows you to quickly preview UI changes in Android and iOS using LiveView
- Enable LiveView in Explorer using the icon, then Run LiveView from the Launch Mode drop-down

--- 

# Trigger LiveView Updates

![img](/assets/images/slides/15/image13.png)

- Once launched LiveView waits for you to commit changes to your project before updating
- Trigger update by modifying or adding files in the Resources directory
- May require you to rebuild your application before loading correctly

--- 

# LiveView also Displays Coding Errors

If there are coding errors, LiveView will display a message in the simulator, device, and Console view

![img](/assets/images/slides/15/image14.png)

---section 

# CODE ANALYZER

--- 

# Using Code Analyzer

![img](/assets/images/slides/15/image15.png)

- Code Analyzer will analyze your code to identify errors and areas for improvement
- Works with both Alloy and traditional apps
- Start by right clicking on project, selecting code analysis, and choosing the platform you wish to analyze

--- 

# Displaying Code Analyzer Results

Several ways to access results:

- Click on pop-up at bottom right of page indicating analysis is done
- In project Explorer, right click, Code Analysis > View current Results shows last run
- Save results by right-clicking on editor and select Export.  Can select format and destination

![img](/assets/images/slides/15/image16.png)

--- 

# Interpreting Code Analyzer Results

- Code Analyzer displays icons in your code to indicate errors or warnings
- Hovering over icons will provide more information
- Can also see aggregated list in the Problems view, under Window > Show View > Other

![img](/assets/images/slides/15/image17.png)

--- 

# Interpreting Code Analyzer Results

HTML page will display with different tabs of results, including Summary, API Usage Finder, Project Score, Analysis Coverage, Platform Validator, and API Deprecation Finder

![img](/assets/images/slides/15/image18.png)

![img](/assets/images/slides/15/image19.png)

---section 

# CODE PROFILER

--- 

# Using Code Profiler

- Appcelerator Studio Code Profiler collects detailed data, recording calls and time to execute as you interact with your app
- Very useful to break down trouble spots in code to improve app performance
- Must record “snapshots” of activity to save data

# Using the Profiler View

![img](/assets/images/slides/15/image20.png)

- Profile View is used to control the profiler, selecting active applications and starting and stop recordings
- Performance Profile View displays data from the profiling section, displaying by call hierarchy or hotspots

# Getting Started with Code Profiler

- Start by selecting Profile  from Launch Mode, then opening Profile view
- Capture a snapshot by clicking Capture Performance Profile button, complete you interaction, then click the Capture Performance Profile button to stop
- Snapshots may be saved

![img](/assets/images/slides/15/image23.png)

# Using Code Profiler Results

Performance Profile View allows you to see app profile data
Call Hierarchy – Displays method calls in hierarchical form, to make it easy to see flow. Can see and sort by call time
Hotspots – Shows all methods used, and cumulative time for all instances of each method used
Double clicking a row will bring up relevant code

![img](/assets/images/slides/15/image24.png)

# Code Profiler Tips

- Name Anonymous Functions – Many methods default to being labeled “anonymous function.”  Declare a function in JavaScript to make it easier to track errors
- Missing Method Calls on Android – Profiler samples every 5 ms for Android, so calls taking less time may not be saved.  CPU intensive calls will be displayed

---section 

# APPCELERATOR PLATFORM TOOLS

--- 

# Appcelerator Test

![img](/assets/images/slides/15/image25.png)

--- 

# Appcelerator Performance Management

![img](/assets/images/slides/15/image26.png)

--- 

# Appcelerator Performance Management Summary

- Appcelerator cloud services includes tracking for app performance, using crittercism. 
- Enable by selecting “Enable Appcelerator Services”
- Use leaveBreadcrumb method in code to make crash identification easier
- Can enable user opt-out and metadata tracking

---section 

# ANDROID TOOLS & TECHNIQUES

--- 

# Android SDK Files

![img](/assets/images/slides/15/image27.png)

- Install by unzipping
- Directories:
  - platforms
  - add-ons
  - platform-tools
  - tools

--- 

# Android Platforms

![img](/assets/images/slides/15/image28.png)

- ```android``` script
- SDK v8 required
- Must use Google APIs version
- Current mix at:http://developer.android.com/   about/dashboards

--- 

# Android logging

![img](/assets/images/slides/15/image29.png)

--- 

# Android Monitor

![img](/assets/images/slides/15/image30.png)

--- 

# Dalvik Debug Monitor

![img](/assets/images/slides/15/image31.png)

---section 

# iOS TOOLS AND TECHNIQUES

--- 

# What's in the box?

![img](/assets/images/slides/15/image32.png)

--- 

# Xcode Device Logs

![img](/assets/images/slides/15/image33.png)

--- 

# OS X Console

![img](/assets/images/slides/15/image34.png)

--- 

# Instruments

![img](/assets/images/slides/15/image35.png)

--- 

# Network Link Conditioner

![img](/assets/images/slides/15/image36.png)

- In Xcode, choose Xcode > Open Developer Tool > More Developer Tools
- Log into the Apple Developer Center
- Download the Hardware IO Tools for Xcode
- Double-click Network Link Conditioner.prefpane

---section 

# MOBILE WEB TOOLS & TECHNIQUES

--- 

# Mobile Web Tips & Techniques

**weinre** is a debugger for web pages, like FireBug (for FireFox) and Web Inspector (for WebKit-based browsers), except it's designed to work remotely, and in particular, to allow you debug web pages on a mobile device such as a phone.

[http://people.apache.org/~pmuellr/weinre-docs/latest/](http://people.apache.org/~pmuellr/weinre-docs/latest/)

![img](/assets/images/slides/15/image37.png)

---section 

# TIPS & NOTES

--- 

# Android Tips

- Much more sensitive to data types (text.value=var will throw error if var != 'string')
- Less than forgiving than iOS with syntax errors
- Use Monitor/ddms to view logs. Studio sometimes doesn't show all
- Check out ```adb``` features: remote shell, push/pull files, launch sqlite to access an app's database

--- 

# Simulator vs. Emulator

||iOS Simulator|Android Emulator|
|-|-|
|Description:|App runs as OS X process|App runs in real OS inside virtual computer|
|Good:|Fast, no code signing steps, use native tools (Console, Instruments) for debugging|Emulate many types of hardware, screen sizes and densities, higher-fidelity representation of device environment|
|Bad:|Unrealistically fast, fewer memory constraints, not case sensitive (unlike device)|Slow, slow, did we say slow? Debugging tools have limited view of Ti objects|

--- 

# Summary

In this lesson, you:

- Debugged the JavaScript of a Appcelerator app using Studio tools
- Debugged Android apps using API tools
- Debugged iOS apps using API and operating system tools
- Debugged Mobile Web apps

---section

# Questions?