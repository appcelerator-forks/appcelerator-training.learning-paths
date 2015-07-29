theme:appcelerator-training
tableclass:striped
progress:true

# Alloy Overview

SDK Fundamentals

---cover

# Alloy Overview

## SDK Fundamentals

--- 

# In this lesson, you will:

- Identify the role of the Alloy MVC components
- Implement a UI control using Views and Styles
- Enable interactivity with a Controller
- Identify options for handling platform differences in Alloy

--- 

# Overview & Goals

- MVC separates form and function
	- Speed and simplify development
	- Improves maintainability
- Alloy is Appcelerator's MVC-like framework for Titanium

--- 

# Alloy MVC

![right](../images/image6.png)

- Views
- Styles
- Controllers
- Models
- Extras

---code

# View - index.xml

The view file declares the structure of the GUI. For example, the file below defines a window with an image and label.


```xml
<Alloy>
     <Window class="container">
          <ImageView id="myImageView" onClick="clickImage"/>
		<Label id="myLabel">Click Image of Apple Logo</Label>
     </Window>
</Alloy>
```

---code 

# Styles -- `<file>.tss`

The style file formats and styles the components in the view file.

For example, the style on the right defines the background color of the window; position, dimensions and color of the label; and position, dimensions and location of the image.

```css
"Window": {
	backgroundColor:"white"
},
"#myLabel":{
	bottom:20,
	width: Ti.UI.SIZE,
	height: Ti.UI.SIZE,
	color:'#999'
},
"#myImageView":{
	image:"/images/apple_logo.jpg",
	width:24,
	height:24,
	top:100
}
```


---code 

# Controllers

The controller file contains the presentation logic, which responds to input from the user.

For example, the controller code below creates an alert dialog when the user clicks on the image and opens the window when the application starts.

```javascript
function clickImage(e) {
	Titanium.UI.createAlertDialog({title:'Image View', message:'You clicked me!'}).show();
}

$.index.open();
```

--- 

# Models

- Alloy uses Backbone.js to provide support for its models and collections
- In Alloy, models contain the interactive data and logic used to control and access it.
- Models are specified with JavaScript files, which provide a table schema, adapter configuration and logic to extend the Backbone.Model class.

--- 

# Convention over Configuration

| File / Directory | Contents & Purpose|
| -- | -- |
| ```/app/config.json``` | Specify global values, conditional environment and operating system values, and widget dependencies. |
| ```/app/views``` | XML View files |
| ```/app/styles``` | TSS Style files |
| ```/app/controllers``` | JavaScript Controller files |
| ```/app/models``` | JavaScript Model files |
| ```/app/migrations``` | JSON files that describe incremental changes in your database; in the formatDATETIME_modelname.json |
| ```/app/assets``` | Graphic, data file, and other app assets; not created by default. |
| ```/app/lib``` | App-specific library files; not created by default. |
| ```/app/themes``` | Theme files and assets to customize your UI; not created by default. |
| ```/app/widgets``` | Files and assets associated with widgets (self-contained app components) |

---section

# Alloy Views and Styles in Detail

---

# View tag

XML View

```xml
<Alloy>
     <ImageView id='foo' image='foo.png'/>
</Alloy>
```

TSS Stylesheet

```css
"#foo": {
     height:Ti.UI.SIZE,
     width: Ti.UI.SIZE
}
```

--- 

# Namespaces

Create elements not in the ```Ti.UI``` namespace:

For objects not in ```Ti.UI``` namespace, such as ```Ti.Map.View```:

```xml
<View ns="Ti.Map" id="map"/>
```

For objects in sub-namespaces, such as ```Ti.UI.iOS.NavigationGroup```:

```xml
 <NavigationGroup platform="ios,mobileweb"/>
```

--- 

# Style Files

- Component, class, and ID
- Global app.tss
- Constants
- i18n functions
- Alloy globals

```css
".activeButton": {
  backgroundColor:"blue"
},
"Button": {
  width: Ti.UI.SIZE,
  height: Ti.UI.SIZE,
  color: "#000"
},
"#iosBtn": {
  color: "#999",
  systemButton: Titanium.UI.iPhone.SystemButton.DISCLOSURE,
  title: L('iosbutton'),
  left: Alloy.Globals.computedWidth
}
```

--- 

# Styles Generation

Using the ```alloy``` command…

```bash
## Create or update the TSS for a controller:
$ alloy generate style controller_name

## Generate TSS for all controllers
$ alloy generate style --all
```

--- 

# Dynamic Styling

- Add/remove classes to components
- Create style objects at run-time
- Dynamic styling is not enabled by default
- Enable with ```autoStyle``` property

```xml
<!-- for individual component -->
<View autoStyle="true">

<!-- for all components in controller -->
<Alloy autoStyle="true">
```

For whole project, set in ```app/config.json```:

```javascript
{
    "autoStyle": false
}
```

--- 

# Dynamic Styles - Add/remove Classes

```javascript
// $.myButton is a Ti.UI.Button in this controller

// now add classes to the button
$.addClass($.myButton, 'my_TSS_class another_class some_other_class');

// remove a class
$.removeClass($.myButton, 'some_other_class');

// reset styles, then apply a class
$.resetClass($.myButton, 'my_TSS_class');

$.myWindow.open();
```

--- 

# Dynamic Styles - Create a Style object

```javascript
// $.myButton is a Ti.UI.Button in this controller
var style = $.createStyle({
     classes: 'my_TSS_class',
     apiName: 'Button', /* or Ti.UI.Button */
     color: 'blue' /* optional, explicit property to set */
});
$.myButton.applyProperties(style);
```

--- 

# Organize your code - Require

Break up views into multiple files

```xml
<Alloy>
     <TabGroup id='tabGroup'>
          <!-- Tab included via <Require> tag -->
          <Require type="view" src="fugitives" id="fugitivetab"/>
          <!-- Tab included via <Require> tag -->
          <Require type="view" src="captured" id="capturedtab" customVar="foo"/>
     </TabGroup>
</Alloy>
```

--- 

# Try It

- Try to break the index.xml into different XML and use Require
- Use different styles for elements in your XML file


---section 

# Controllers in Depth

--- 

# Controllers

- Contain the application logic
- Communicate between Views and Models
- Handle user interaction and dynamic UI updates
- Access components via their id attribute: ```$.<idstring>```

--- 

# Views without IDs

index.xml

```xml
<Alloy>
     <Window class="container">
          <Label id="label" onClick="doClick">Hello, World</Label>
     </Window>
</Alloy>
```

index.js

```javascript
// Window tag has no id, so access by file name
$.index.open();
```

--- 

# Event Handling

```javascript
/* listening for an event on a Ti object with id of 'button' */
$.button.addEventListener('click', function(e){
     // do something
});
// firing an event
$.button.fireEvent('click', {foo: 'bar'});

// adding and removing an event
var listener = function() {
     Ti.API.info("Event listener called.");
}
$.win.addEventListener('click', listener);
$.win.removeEventListener('click', listener);
```

--- 

# Dynamically Creating Views

- ```Alloy.createController```: factory method for instantiating a controller

- ```Controller.getView()```: return the view associated with this controller

Example:

```javascript
var foo = Alloy.createController('foo').getView();
foo.open();
```

--- 

# Dynamic Views Example

Using custom rows in a tableview:

Controller

```javascript
var rows = [];
// arr is some array of data to show in a table
for (var i = 0; i < arr.length; i++) {
     var row = Alloy.createController('CustomRow',arr[i].toJSON()).getView();
     rows.push(row);
}

// set the table
$.table.setData(rows);
```

--- 

# Passing Arguments

Pass arguments when initializing a controller:

```javascript
var data[];
for (var i=0; i < source.length; i++) {
     var arg = {
          title: source[i].postTitle,
          url: source[i].postLink
     };
     var row = Alloy.createController('row', arg).getView();
     data.push(row);
}
$.tableView.setData(data);
```

**Row** view:

```xml
<Alloy>
     <TableViewRow id="rowView">
<Alloy>
```

**Row** controller:

```javascript
var args = arguments[0] || {};
$.rowView.title = args.title || '';
$.rowView.url = args.url || '';
```

--- 

# Dynamically Styling Views from Controllers

**app/views/profile.xml**

```xml
<Alloy>
    <View id="container">
        <ImageView id="picture"/>
        <Label id="name"/>
    </View>
</Alloy>
```

**app/controllers/index.js**

```javascript
var profile = Alloy.createController('profile');
profile.updateViews({
	"#container" : {
        layout : "vertical"
	},
	"#picture" : {
        image : "/appicon.png"
	},
	"#name" : {
        text : "Mr. Man"
	}
});
$.index.add(profile.getView());

$.index.open();
```

--- 

# Try It

- Create dynamically 6 labels (boxes) and assign click events
- Change their styles when creating them to have different background colors

---

# Summary

In this lesson, you:

- Learned the roles of UX and UI design
- Explored the components used to create your UI
- Learned your options for UI layout and component positioning
- Learned how to set your app's icon & splash screens, and internationalize your app

---section

# Questions?