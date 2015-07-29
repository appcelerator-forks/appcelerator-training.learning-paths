theme:appcelerator-training

# Appcelerator Arrow

Appcelerator Certified Developer (ACD) Training

---cover

# Appcelerator Arrow

## Appcelerator Certified Developer (ACD) Training

--- 

# In this lesson, you will:

- Configure orientation support and react to orientation changes
- Respond to gestures other than 'click'

--- 

# ORIENTATION
--- 

# Orientation Support

![img](/assets/images/slides/20/image6.png)

- Fixing orientation for the whole app
- Setting supported orientation for each window
- Reacting to orientation changes dynamically

--- 

# App-level Orientation

- App-level settings either fix orientation for the entire app
- Or specify the possible orientations that the app supports
- Controls splash screen orientation (on tablets)
- Techniques differ for iOS & Android

--- 

# App-level Orientation Support - iOS

`tiapp.xml`

```javascript
<ios> 
<plist> 
<dict> 
     <key>UISupportedInterfaceOrientations</key> 
     <array> 
	     <string>UIInterfaceOrientationPortrait</string> 
     </array> 
     <key>UISupportedInterfaceOrientations~ipad</key> 
     <array> 
  	   <string>UIInterfaceOrientationPortrait</string> 
  	   <string>UIInterfaceOrientationPortraitUpsideDown</string> 
  	   <string>UIInterfaceOrientationLandscapeLeft</string> 
  	   <string>UIInterfaceOrientationLandscapeRight</string> 
     </array> 
</dict> 
</plist> 
</ios>
```

--- 

# Try It

- Create a new project
- Check sections you will need to change for app level orientation support

--- 

# Android Orientation Support

- By default, supports Portrait and Landscape
- No notion of upside-down or landscape-left/right
- Configure manifest to remove orientation-change support

--- 

# Locking Orientation on Android

>![image001.png](../assets/../assets/tips.gif) **TIP:** By default, Android supports all orientations.

- Copy `<application>` node & all its `<activity>` tags from `build/android/AndroidManifest.xml`
- Paste into `tiapp.xml`, between `<android><manifest></manifest></android>` tags
- Specify desired app orientation by adding `screenOrientation` attribute

```xml
<android xmlns:android="http://schemas.android.com/apk/res/android"> 
  <manifest> 
	   <application> 
        <activity 
          android:name="org.appcelerator.titanium.TiActivity" 
          android:configChanges="keyboardHidden|orientation" 
          android:screenOrientation="portrait" 
        /> 
        <activity android:name="ti.modules.titanium.ui.TiTabActivity" 
          android:configChanges="keyboardHidden" 
        /> 
	   </application> 
  </manifest> 
</android>
```

--- 

# Try It

From last project:

- Build once
- Copy android manifest sections to `tiapp.xml`

--- 

# Setting Orientation per Window

--- 

## Window Orientation Modes 

Supported values include:

- PORTRAIT / UPSIDE_PORTRAIT
- LANDSCAPE_LEFT / LANDSCAPE_RIGHT

```javascript
/* With Alloy, can define in the TSS file */ 
"#window": { 
	orientationModes: [Ti.UI.PORTRAIT, Ti.UI.LANDSCAPE_LEFT] 
}
```

--- 

# Orientation Events

- `orientationchange` event in the `Ti.Gesture` namespace
  - This is an app-level / global event
  - Event properties and methods:

```javascript
Ti.Gesture.addEventListener('orientationchange', function(e) { 
  // current device orientation 
  // Ti.Gesture.orientation 

  // or, get orientation from event object 
  // e.orientation 

  // also, there are two helpers: 
  // e.source.isPortrait() 
  // e.source.isLandscape() 
});
```

--- 

# Example

```javascript
Ti.Gesture.addEventListener('orientationchange', function(e) { 
     if(e.source.isPortrait()) { 
	  $.someView.applyProperties({ 
		top: 10, left: 10 
	   }); 
     } else if(e.source.isLandscape()) { 
	   // explicitly test to avoid spurious orientation changes on iOS 
     } 
}); 
```

--- 

# Try It

- Open your previous project
- Write to console the different orientation modes

---section 

# Gestures

--- 

# Gestures

![img](/assets/images/slides/20/image9.png)

- Shake
- Swipe
- Touch start, end, move, & cancel
- Pinch
- Long press

--- 

# Shake

![img](/assets/images/slides/20/image10.png)

```javascript

Ti.Gesture.addEventListener('shake', function(e) { 
     // e.timestamp is only property 
     alert('it worked'); 
}); 
```

```xml
<!-- how hard a shake is needed --> 
<property name="ti.android.shake.factor">1.3</property>
<!-- how long must it continue --> 
<property name="ti.android.shake.active.milliseconds">1000</property> 
<!-- how long between shakes --> 
<property name="ti.android.shake.quiet.milliseconds">500</property> 
```

--- 

# Try It

From last project
Add an event listener for shake

--- 

# Swipes

![img](/assets/images/slides/20/image11.png)

- Built-in event on most Ti.UI elements
- Event object properties:
  - direction
  - source
  - x/y coords

```javascript
$.someView.addEventListener('swipe', function(e) { 
     alert('You swiped ' + e.direction); 
}); 
```

--- 

# Touches

- Built-in event on most Ti.UI elements
- Subtypes: `touchstart`, `touchmove`, `touchend`, `touchcancel`
- `touchmove` fires continuously during event
- Event object properties: `source`, `x`/`y` coords

```javascript
$.someView.addEventListener('touchstart', function(e) { 
     alert('You touched at coordinates ' + e.x + '/' + e.y); 
}); 
```

--- 

# Pinch

![img](/assets/images/slides/20/image12.png)

iOS & Android
Zoom only (no rotation)

```javascript
// $.image is some large image, shown at 400w x 300h 
// $.view is a view, also shown at 400w x 300h 
// $.image is inside the $.view 
var maxWidth = 1600, 
     maxHeight = 1200, 
     origWidth = 400, 
     origHeight = 300; 

$.view.addEventListener('pinch', function(e){ 
     var newWidth = $.image.width * e.scale; 
	newWidth = (newWidth < origWidth) ? origWidth : newWidth; 
	newWidth = (newWidth > maxWidth) ? maxWidth : newWidth; 
     var newHeight = $.image.height * e.scale; 
	newHeight = (newHeight < origHeight) ? origHeight : newHeight; 
	newHeight = (newHeight > maxHeight) ? maxHeight : newHeight; 
     $.image.applyProperties({ 
	width: Math.round(newWidth), 
	height: Math.round(newHeight) 
     }); 
}) 
```

--- 

# Long press

- Supported by most UI elements
- Keep in mind native UI conventions for long presses

```javascript
$.someView.addEventListener('longpress', function(e) { 
     alert('You pressed me'); 
}); 
```

--- 

# Summary

In this lesson, you:

- Configured orientation support and react to orientation changes
- Responded to gestures other than 'click'

---section 

# Questions?