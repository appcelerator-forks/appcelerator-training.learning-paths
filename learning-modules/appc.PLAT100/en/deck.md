theme:appcelerator-training
tableclass:striped
progress:true

# Platform Overview

Appcelerator SDK Fundamentals

---cover

# Platform Overview

## Appcelerator SDK Fundamentals

---section

# Getting Started

--- 

# In this lesson, you will:

- Explore the market, features, and typical use-cases for Appcelerator  Studio
- Examine the basic Appcelerator Titanium architecture
- Appcelerator Studio
- List the steps in the app development process
- List the resources available to help developers

--- 

# Appcelerator Platform Overview

![](assets/image6.jpeg)

--- 

# Appcelerator vs Titanium

- Build & Develop, Debug, Alloy, & Publish to Public App Stores
- Pre-Built Cloud Services 
- Custom Cloud Services

Enterprise Features:

- Enterprise Connectors
- Performance Profiler
- Dynamic Code Analyzer
- LiveView (Visualize UI Changes)
- Publish to Enterprise App Stores
- Automated Functional Testing
- Real-Time Performance Management
- Real-Time Analytics
- Virtual Private Deployment Option

--- 

# Dashboard.appcelerator.com

![](assets/image7.png)

--- 

# Appcelerator Cloud Services

![](assets/image8.png)

--- 

# Appcelerator Test

![](assets/image9.png)

--- 

# Appcelerator Performance Management

![](assets/image10.png)

--- 

# Appcelerator Analytics

![](assets/image11.png)

--- 

# Appcelerator Executive Insights

![](assets/image12.png)

--- 

# Supported Mobile Platforms

- iOS - iPhone, iPad, iPod Touch
- Android - handsets and tablets
- Mobile Web (HTML5)
- BlackBerry 10
- Windows Phone SDK (Using Mobile Web)

--- 

# Powered By Appcelerator

![](assets/apps-1.png)

---section

# Titanium SDK - ARCHITECTURE

---

# How Titanium SDK Works

![right](assets/image29.png)

- You write Javascript
- Appcelerator maps your JavaScript code to native components
- Communication is two-way across the bridge

--- 

# Appcelerator Key Points

- You write in JavaScript
- There's a platform-specific bridge and set of native components(so your source code can run on multiple platforms)
- Your JavaScript is still there and running on the user's device
- Your app is compiled (so your code is secure)

--- 

# Cross-Platform in Appcelerator

- Cross-platform !== 'Write Once, Run Everywhere‘
- Titanium is 'Write Once, Adapt Everywhere‘
- Goal is to build 'Best of Breed' apps
- Non-visual code up to 100% portable
- Accept and embrace platform differences

--- 

# Appcelerator Provides APIs For:

- UI components — add native buttons, pickers, tables and more to your apps
- Networking — HTTP/HTTPS, sockets, Bonjour
- Local storage — file, database, app properties
- Camera, GPS, accelerometer
- Social APIs — Facebook, YQL, more
- Extensible & modular to add on custom functionality

--- 

# Try It

If you haven’t done this yet:

- Go to [http://dashboard.appcelerator.com](http://dashboard.appcelerator.com)
- Review all services available for you in the Dashboard
- Download Appcelerator Studio

---section

# DEVELOPMENT PROCESS
--- 

# App Dev Process

- Write your source in JavaScript
- Build for simulator/emulator/test device
- Debug/test
- Publish

--- 

# Build Process

- Node.js scripts analyze your JavaScript and interact with native tools
- Your code is packaged into native project
- Platform-specific interpreter included
  - iOS: JavaScriptCore
  - Android: V8
- Native project is compiled using platform-specific tools
- If building to device, project is code-signed using native tools

--- 

# Debugging/Testing Overview

- Syntax checking in Studio
- Logging messages
- Breakpoint debugging in simulator/emulator and device
- Native tools for memory inspection
- Appcelerator Performance Management service
- Appcelerator Test for automated functional testing

--- 

# Publishing Overview

- Your code is minified and further compiled than with development builds
- Images are optimized with a pngCrush style optimizer
- App is signed with your publication certificates
- Stored on the file system (Android) or synced to Xcode Organizer (iOS) for native publishing process(AdHoc & Enterprise publishing a bit different)

---section

# DOCS & RESOURCES

--- 

# Documentation is Your Friend

![](assets/image32.png)

[https://docs.appcelerator.com](https://docs.appcelerator.com)

--- 

# Documentation - More Details

![](assets/image33.png)

--- 

# Example Code

![](assets/image34.png)

[https://github.com/appcelerator](https://github.com/appcelerator)

![](assets/image35.png)

[https://github.com/appcelerator-developer-relations](https://github.com/appcelerator-developer-relations)

--- 

# Getting Help

![left](assets/image36.png)

![right](assets/image37.png)

- [https://support.appcelerator.com](https://support.appcelerator.com)
- [https://developer.appcelerator.com/questions/newest](https://developer.appcelerator.com/questions/newest)

--- 

# Try It

- Go to http://docs.appcelerator.com
- Find information about the Titanium SDK
- Find information about any API: TableViews

--- 

# Summary

- Explored the market, features, and typical use-cases for Appcelerator
- Examined the basic Titanium architecture
- Examined the steps in the app development process
- Discovered the resources available to help developers

---section

# Questions?