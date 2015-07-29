theme:appcelerator-training
tableclass:striped
progress:true

# Alloy Overview

Appcelerator SDK Fundamentals

---cover

# Alloy Overview

## Appcelerator SDK Fundamentals

--- 

# In this lesson, you will:

- Explore the components used to create your UI
- Learn your options for UI layout and component positioning
- Handle user and non-user generated events
- Learn how to set your app's icon & splash screens, and internationalize your app

---section

# UI COMPONENTS

---

# Controls

- Windows and Views
- Labels
- ImageViews
- Buttons, Text Fields, Text Areas
- Navigation controls -- tabs, split windows, etc.
- Media-related (video or audio players)

--- 

# Windows & Views

- 'Containers' to hold other components
- Windows = full screen (usually)
- Views = portion of the screen (like a ```<div>```)
- Every app has at least one window

--- 

# View Hierarchy - Window-based apps

- Single window (no tabs)
- Views inside window or other views

```xml
<Alloy>
     <Window borderColor=“green”> 
            <View borderColor=“blue” />
	    <View borderColor=“blue”>
		<Button borderColor=“red” />
	    </View>  
     </Window> 
</Alloy> 
```

![img](/assets/images/slides/6/image6.png)

--- 

# View Hierarchy - Tab-based apps

- Tab group with 1+ tabs
- Each tab has one window
- Views inside window or other views

```xml
<Alloy>
      <TabGroup>
           <Tab> 
                <Window>
		  <TableView />
	       </Window>
           </Tab>   
      </TabGroup>
 </Alloy> 

```

![img](/assets/images/slides/6/image7.png)

--- 

#	 iOS 7 UI Components

![img](/assets/images/slides/6/image9.png)

--- 

# Android 4.x User Interface Components

![img](/assets/images/slides/6/image11.png)
![img](/assets/images/slides/6/image12.png)

---

# Android 5.x – Lollipop / Material Design 

todo

--- 

# Try It

- In Studio, create a new Titanium Mobile project or use a previous project
- Examine the view hierarchy in app/views/index.xml
- Identify the containers in the view hierarchy of this app

---section 

# UNITS, POSITIONING, & MORE

--- 

# Positioning

- top and left
- bottom and right
- center

![img](/assets/images/slides/6/image15.png)

```xml
<View id=“red” />
<View id=“blue” />
<View id=“yellow” />
```

```javascript
“#red”:{
	top: 10, left: 10, 
	width: 10, height: 10 
}, 
“#blue”:{
	center:{x:50%,y:50%},	 	width: 50, height: 50
},
“#yellow”:{
	bottom:70, right: 70, 
	width: 10, height: 10
}
```

--- 

# Units

- Absolute measurements: px (pixels), dp/dip, mm, cm, in
- Relative measurements: % = percent of the parent's height or width

```javascript
var view = Ti.UI.createView({ 
     /* You would not normally mix units like this */ 
     top: '10mm', 
     left: '5px', 
     width: '30%', 
     height: 50 /* default system units are used here */
 }); 
```

Default units:

- Android = pixels
- iOS = dip

--- 

# Auto' Behaviors

- You can use Ti.UI.SIZE or Ti.UI.FILL instead of actual height/width value
  - SIZE: fits to contents
  - FILL: fills relative to parent

- Defaults (if you don't set a height/width)
  - Buttons, Labels, ImageView, TextFields and TextAreas = Ti.UI.SIZE
  - Window, View, TableView, WebView = Ti.UI.FILL
  - TableViewRow = FILL for width and SIZE for height

--- 

# Coordinates Grid

- iPhone 3/4 - 320 x 480 points (4:3)
- iPhone 5 - 320 x 568 points (16:9)
- iPhone 6 - 375 x 667 points (16:9)
- iPhone 6 Plus - 414 x 736 points (16:9)
- iPad 1/2/3 - 1024 x 768 points (4:3)

![img](/assets/images/slides/6/image16.png)

- Android sizes vary (examples):
- HVGA = 320 by 480 px (4:3)
- WVGA800 = 480 by 800 px (5:3)
- WVGA854 = 480 by 854 px (16:9)

--- 

# Layout modes

- Absolute
- Vertical
- Horizontal

![img](/assets/images/slides/6/image17.png)

--- 

# Absolute Layout

![img](/assets/images/slides/6/image18.png)

```xml
<Button id=“SaveBtn”>Save my Information</Button>
```

```javascript
“#SaveBtn”:{
	top: 170
	right: 20,
	width: 280
}
```

--- 

# Vertical Layout

![img](/assets/images/slides/6/image19.png)

```javascript
“Window”:{
	layout: “vertical”
},
“#green”:{
	top: 50,
	backgroundColor: ‘green’
	height: 120
},
“#red”:{
	top: 50,
	backgroundColor: ‘red’
	height: 120
}
```

--- 

# Try It

- To the sample project you began earlier, change the Window to vertical layout.
- Create a view and add it to the window. Make the view 120 units tall and 50 units from the top. Set its background to be green.
- Create a second view with the same properties, though with a red background. Add it to the window.

---section

# EVENTS

--- 

# Event Handling

- Events are things that happen that you can monitor and react to
- User-generated: clicks, swipes, shakes, etc.
- Custom: non-user events that you use to signal within your app
- System-generated: battery low, phone call or SMS received

--- 

# Event Handling, cont'd

- Event listener - code you 'attach' to something to run when an event occurs
- Firing event - causing an event so that listeners are engaged
- You can add a listener on any UI component
- You can add custom listeners to nearly any object in your app
- You can fire any user-generated or custom type event (not the system events though)

--- 

# Example

```xml
// let's start with a UI component, a button 
<Button id=“btn”>I am a button</Button>
```

```javascript
// let's define our function first 
function ouch() { 
     alert('Ouch! You clicked me!'); 
} 

// then use it in the listener -- without the () !! 
$.btn.addEventListener('click', ouch); 
```

--- 

# Removing Event Listeners

```xml
<Button id=“btn”>I am a button</Button>
```

```javascript
function ouch() { 
     alert('Ouch! You clicked me!'); 
     $.btn.removeEventListener('click', ouch); 
     $.btn.title = "You can't click me"; 
} 

$.btn.addEventListener('click', ouch); 
```

--- 

# Event Object Properties

```xml
<TextField id=“textField”>
<TextField id=“anotherField”>
```

```javascript
$.textField.addEventListener('change', function(e) { 
     // e represents the 'event' object        
     $.anotherField.value = e.value; // it has various properties 
});
```

--- 

# Events Documentation

![img](/assets/images/slides/6/image20.png)

![img](/assets/images/slides/6/image21.png)

--- 

# Application-Level Events

- Not associated with a UI component
- Used for signaling within the application
- Can be fired from and listened for from anywhere within your app
- ```Ti.App.addEventListener```
- ```Ti.App.removeEventListener```

--- 

# App Events Example

```javascript
$.textField.addEventListener('change', function(e) { 
     // e represents the 'event' object        
     $.anotherField.value = e.value; // it has various properties 
});
```

```xml
<TableView id=“myTable” />
```

```javascript
Ti.App.addEventListener('databaseUpdated', function() { 
     $.myTable.data = db.getInfoAsTableRows(); 
});
```

--- 

# Try It

- Add a click event listener to the first view.
- When the user clicks on the view, display an alert message using alert()
- Build your project to test your work.

---section 

# ICONS, LAUNCH SCREENS, & I18N

--- 

# App icons - iOS

|iPhone 6 Plus(@3x)| iPhone 6 and iPhone 5 (@2x) | iPhone 4s(@2x) | iPad and iPad mini(@2x) | iPad 2 and iPad mini(@1x) |
|-|-|-|-|
| Non-retina | | | appicon-60.png(60x60px) | | appicon-76.png(76x76px)|
| Retina | appicon@3x.png(180x180px) | appicon-60@2x.png(120x120px) | appicon-60@2x.png(120x120px) | appicon-76@2x.png(152x152px) | |

Alloy: ```app/assets``` or ```app/assets/iphone```

--- 

# App icons - Android

Simple solution: place a single ```appicon.png``` in ```app/assets```, or ```app/assets/android```. Or:

|Class|Dimensions and DPI|File name and path|
|-|-|
|ldpi|120 dpi, 36x36 px|/platform/android/res/drawable-ldpi/appicon.png|
|mdpi|160 dpi, 48x48 px|/platform/android/res/drawable-mdpi/appicon.png|
|hdpi|240 dpi, 72x72 px|/platform/android/res/drawable-hdpi/appicon.png|
|xhdpi320 dpi, 96x96 px|/platform/android/res/drawable-xdpi/appicon.png|
|xxhdpi|480 dpi, 144x144 px|/platform/android/res/drawable-xxdpi/appicon.png|

--- 

# Launch Screens - iOS

| | | |
|-|-|-|
|Default.png|Non-retina iPhone/iPod|320x480|
|Default@2x.png|Retina iPhone/iPod|640x960|
|Default-568h@2x.png|iPhone 5/iPod 5|640x1136|
|Default@2x.png|iPhone 6|750x1334|
|Default@2x.png|iPhone 6 Plus|1242x2208|
|Default-Landscape.png & Default-Portrait.png|Non-retina iPad|1024x768|
|Default-Landscape@2x.png & Default-Portrait@2x.png|Retina iPad|Retina iPad|2048x1536|

--- 

# Launch Screens - Android

- **Option 1**: Use a single default.png in app/assets/android*Will be stretched to fit screen size and proportions
- **Option 2**: Put size/resolution-specific versions of default.png in res directories*No tablet sizes supported
- **Option 3**: Use a 9-patch image*Use android 9patch tool

![img](/assets/images/slides/6/image22.png)

![img](/assets/images/slides/6/image23.png)

--- 

# Internationalization

- multiple languages
- Localized app name
- Localizaed Images and file resources
- Test by changing your settings to use a different language

![img](/assets/images/slides/6/image24.png)

![img](/assets/images/slides/6/image25.png)

![img](/assets/images/slides/6/image26.png)

--- 

# i18n Notes

- i18n directory goes in project root, not inside app or Resources!
- Language directories named with ISO-639 two-letter country codes
- You have to create those directories yourself
- Which strings are shown depends on device's language setting  *not for user-switchable language selection within your app
- The XML structure matches Android's string resources file, mapped to plist on iOS at build time

--- 

# Using the strings

```L()```  = ```Ti.Locale.getString()```;

```xml
/i18n/en/strings.xml
<?xml version="1.0" encoding="UTF-8"?>
<resources>
<string name="greeting">hello</string>
<string name="signoff">goodbye</string>
</resouces>
```

```xml
/i18n/es/strings.xml
<?xml version="1.0" encoding="UTF-8"?>
<resources>
<string name="greeting">hola</string>
<string name="signoff">adios</string>
</resources>
```

```xml
/app/views/index.xml
<Alloy>
	<Window>
		<Label id=‘title’ />
		<Button id=‘btn’>
	</Window>
</Alloy>
```

```javascript
/app/styles/index.tss
‘#title’:{
	text : L(‘greeting’)
}
```

```javascript
/app/controllers/index.js
$.title.text = Ti.Locale.getString(‘title’);
```

--- 

# Try It

- Work on the previous project
- Create 2 strings.xml files for English and Spanish
- Change the code to use different languages
- Test your app by changing the settings in your simulator/emulator

--- 

# Extracting Strings

```bash
// Shows a before and after of your i18n file, does NOT write the changes 
$ alloy extract-i18n 

// Writes the changes to "i18n/en/strings.xml" 
$ alloy extract-i18n --apply 

// Specify a different language with another parameter ("en" is the default) 
$ alloy extract-i18n es 

// Specify "es" as the language and write the changes to "i18n/es/strings.xml" 
$ alloy extract-i18n es --apply 
```

--- 

# Summary

In this lesson, you:

- Learned the roles of UX and UI design
- Explored the components used to create your UI
- Learned your options for UI layout and component positioning
- Learned how to set your app's icon & splash screens, and internationalize your app

---section

# Questions?
