theme:appcelerator-training
tableclass:striped
progress:true

# Custom UI Components

Appcelerator SDK Fundamentals

---cover

# Custom UI Components

## Appcelerator SDK Fundamentals

---

# In this lesson, you will:

- Identify the building blocks of custom UI components
- Implement a custom component built with traditional API techniques
- Implement an Alloy widget

---

# Examples

![img](/assets/image6.png)
![img](/assets/image7.png)
![img](/assets/image8.png)
![img](/assets/image9.png)

---

# Why Custom Components?

- Create unified UI/UX across platforms
- Apply brand styling to your UI components
- Simplify reusability
- Invent your own UX/UI component
- Cons: More work, more maintenance

---

# Creating Custom Components

![img](/assets/image10.png)

- Building blocks: Views, ImageViews, Buttons, Labels
- Which? The one that's closest to your needs
- Set styles, add eventListeners
- Generalize them as much as possible and DESIGN THE API
- Navigation components (e.g. custom tab controllers) are extra work

---section

# TRADITIONAL API-BASED COMPONENTS

---

# Traditional API

- CommonJS module
- Use in either traditional or Alloy project
- Many community-contributed components
- `require()` in and then use like built-in components

---

# Creating a Traditional Component

- Use the 'factory' pattern with your CommonJS module
- Don't extend the Titanium proxies
- Instantiate with new

```javascript
var foo = 'common to all instances'; 
function MyComponent() { 
     var bar = 'redefined w/each instance'; 
     var self = {}; 
     self.view = Ti.UI.createView(); 
     self.doSomething = function(args) { 
	     // some method of your custom component 
     } 
     return self; 
} 
module.exports = MyComponent; 
```

---section

# ALLOY WIDGETS

---

# Alloy Widgets

- Self-contained components
- Can be easily dropped into an Alloy project
- Write your own, or use the ones published by Appcelerator
- Can't use in traditional projects
- Many listed at [http://github.com/AppceleratorSolutions/AlloyWidgets](http://github.com/AppceleratorSolutions/AlloyWidgets)
- 100’s of community built widgetshttp://gitt.io

---

# Using Widgets

1. Configure dependency in app/config.json
2. Download code to app/widgets folder*
3. Add tag to appropriate view
4. Call widget's init() method in controller (except those distributed with Alloy)

`config.json`

```javascript
{ 
	"global": {}, 
	"env:development": {}, 
	"env:test": {},
	"env:production": {}, 
	"os:ios": {}, 
	"os:android": {}, 
	"dependencies": { 
		"com.appcelerator.buttongrid":"1.0" 
	} 
} 
// index.xml 
<Widget id="buttongrid” src="com.appcelerator.buttongrid"/> 
```

---

# Widget Creation Process

1. Create a standard mobile project
2. **Right-click** app, choose **New Widget**
3. Edit `widget.json` as needed
4. Implement your functionality in the widget's views, styles, and controllers
5. Test by building your mobile project
6. Distribute by sharing your widget's folder

![img](/assets/image11.png)

---

# Differences with Widgets

- Main controller is `widget.js/widget.xml` rather than `index.js/index.xml`
- Instantiate "sub-views" with `Alloy.createWidget('myWidget', 'myButton')`
- Controller methods are private unless you prefix with exports
- You must use `WPATH('images/foo.png') `to reference assets

---

# Try It

- Check widgets folders
- Review structure and config files

---

# Summary

In this lesson, you:

- Identified the building blocks of custom UI components
- Implemented a custom component built with traditional API techniques
- Implemented an Alloy widget

---section

# Questions?