theme:appcelerator-training
tableclass:striped
progress:true

# Mapping

Appcelerator SDK Fundamentals

---cover

# Mapping

## Appcelerator SDK Fundamentals

--- 

# In this lesson, you will:

---section

# MAPS & ANNOTATIONS

---

# Native Map Kits

![img](/assets/images/slides/12/image9.png)
![img](/assets/images/slides/12/image10.png)

- Native maps provide zooming, scrolling, and different display types
- Points of interest are added with Annotations (pins)
- Support for drawing routes (iOS and Android)
- Can choose center point and initial display range

--- 

# Annotations

![img](/assets/images/slides/12/image11.png)

- Annotations can be added on or after creation
- Can customize:
  - Pin image/color
  - Title/Subtitle
  - Right/Left Button
- Can individually update pins, all are set at the same time

--- 

# Adding Maps

- Mobile Web, Tizen, BB10 — use built-in Ti.Map component
- iOS & Android — use add-on module
  - Download from Marketplace or [https://github.com/appcelerator-modules/ti.map](https://github.com/appcelerator-modules/ti.map)
  - Module adds new functionality
- iOS: no map key or setup required
- Android: API key and some setup required

--- 

# Android Mapping

![img](/assets/images/slides/12/image12.png)

- Version 2 Google Maps API key required  unless you happen to have an API v1 key already
- Must use API key to see tiles on device / in production
- Either add with the ```<Module>``` tag in the View XML or create in the controller
- Annotations have to be added in the controller

--- 

# iOS/Android Maps Solution

- Add module to ```tiapp.xml```
- Enable module in ```alloy.js```
- Define map in XML
- Style map in TSS
- Add annotations and set platform-specifics in controller

--- 

# Maps Example
![img](/assets/images/slides/12/image13.png)

--- 

# tiapp.xml changes

1. First, download the modules and install
2. Add module support
3. For Android, configure permissions and API key (later slide)

```xml
<modules> 
	     <module platform="iphone">ti.map</module>
 	     <module platform="android">ti.map</module> 
</modules>
```

--- 

# Alloy.js

```javascript
// Require module, and make it available throughout your app 
Alloy.Globals.Map = require('ti.map'); 
```

--- 

# Maps View

```xml
<Alloy> 
     <Window class='container' id="win"> 
	    <View id="map" ns="Alloy.Globals.Map"></View> 
	    <View id="dividerLine"/> 
	    <View id="map1" ns="Alloy.Globals.Map"></View> 
     </Window> 
</Alloy> 
```

--- 

# Associated TSS file

```javascript
"#map": { 
	userLocation: false, 
	animate: true, 
	height: '50%', 
	top: 0, 
	region: { latitude: 37.38, latitudeDelta: 0.2, 
		longitude: -122.05, longitudeDelta: 0.2 		} 
}, 
"#map1": { 
	userLocation: false, 
	animate: true, 
	height: '50%', 
	top: '50%', 
	region: {latitude: -33.87365, longitude: 151.20689, 
		latitudeDelta: 0.1, longitudeDelta: 0.1      } 
} 
```

--- 

# Associated Controller

```javascript
// add some annotations, must be done in code 
var anno1 = Alloy.Globals.Map.createAnnotation({ 
	title:"Mountain View", 
	latitude:37.389569, 
	longitude:-122.050212 
}); 
$.map.addAnnotation(anno1); 
var anno2 = Alloy.Globals.Map.createAnnotation({ 
	title:"Sydney", 
	latitude: -33.87365, 
	longitude: 151.20689 
}); 
$.map1.addAnnotation(anno2); 

$.win.open(); 
```

---section 

# ANDROID SPECIFICS

--- 

# Android Maps: General Procedure
1. Obtain an API key from Google: [https://developers.google.com/maps/documentation/android/start#obtain_a_google_maps_api_key](https://developers.google.com/maps/documentation/android/start#obtain_a_google_maps_api_key)
2. Update tiapp.xml with that key
3. Enable module in tiapp.xml
4. Require the module in JavaScript
5. Instantiate & style your map in JavaScript

--- 

# Obtaining an API key

- Get your app's SHA-1 fingerprint
- Visit Google's API console: [https://code.google.com/apis/console/](https://code.google.com/apis/console/)
- Click Create Project or select project name, click Create
turn on Google Maps Android API v2
- Click API Access, then click Create New Android Key
- Paste your SHA-1 fingerprint, a semicolon, then your app's App ID
- Save the resulting "Key for Android Apps (with certificates)"

![img](/assets/images/slides/12/image14.png)

--- 

# Update tiapp.xml

![img](/assets/images/slides/12/image15.png)

- Download module from Marketplace, and install
- Copy sample XML from the docs into your ```tiapp.xml```
- Edit the three highlighted locations

---section 

# iOS SPECIFICS

--- 

# iOS Notes

- No API key needed
- New 3D perspective
- Panning past 180/-180° longitude now supported
- New overlay rendering and placement options
- Additional properties (e.g. tintColor)

--- 

# Camera View

Add static or animated "camera" to enable 3D perspective

- altitude: meters above surface
- centerCoordinate: camera position
- heading: camera aiming, relative to true north
- pitch: viewing angle (0 straight down)

```javascript
// add the iOS7-specific camera view 
if(OS_IOS && parseInt(Ti.Platform.version, 10)>=7) { 
     var cam = Alloy.Globals.Map.createCamera({ 
	altitude: 300, 
	centerCoordinate: { 
	     latitude:37.389569, 
	     longitude:-122.050212 
	}, 
	heading: -45, 
	pitch: 60, 
	showsBuildings: true 
     }); 
     var animCam = function(){ 
	$.map.removeEventListener('complete', animCam); 
	$.map.animateCamera({ 
	     camera: cam, 
	     curve: Ti.UI.ANIMATION_CURVE_EASE_IN, 
	     duration: 500 
	}); 
     }; 
     $.map.addEventListener('complete', animCam); 
} 
```

--- 

# Maps Demo

--- 

# Summary

In this lesson, you:

- Integrated native maps
- Used custom map annotations

---section

# Questions?