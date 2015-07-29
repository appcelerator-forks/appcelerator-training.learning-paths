theme:appcelerator-training
tableclass:striped
progress:true

# Appcelerator Arrow

Appcelerator SDK Fundamentals

---cover

# Appcelerator Arrow

## Appcelerator SDK Fundamentals

---

# In this lesson, you will:

- Set TextField and TextArea options
- Handle keyboard and layout issues
- Explore the available UI components

---section

# TEXTFIELD & TEXTAREA OPTIONS

---

# Autocorrection and Autocapitalization

```javascript
"#someField": { 
     autocorrection: false, 
     autocapitalization: Ti.UI.TEXT_AUTOCAPITALIZATION_WORDS 
} 
```

Others include: 

- `Ti.UI.TEXT_AUTOCAPITALIZATION_DEFAULT` 
- `Ti.UI.TEXT_AUTOCAPITALIZATION_ALL`
- `Ti.UI.TEXT_AUTOCAPITALIZATION_SENTENCES` 
- `Ti.UI.TEXT_AUTOCAPITALIZATION_NONE` 

---

# Keyboard Customization

- Keyboard Type — `field.keyboardType`
- Assigning the Return key — `field.returnKeyType`
- Keyboard Toolbars

---

# Keyboard Types - iPhone

Ti.UI.KEYBOARD_

DEFAULT

![img](/assets/image6.png)

NUMBERS_PUNCTUATION

![img](/assets/image7.png)

URL

![img](/assets/image8.png)

NUMBER_PAD

![img](/assets/image9.png)

PHONE_PAD

![img](/assets/image10.png)

- ASCII
- DECIMAL_PAD
- EMAIL
- NAMEPHONE_PAD

---

# Return Key Options

![img](/assets/image11.png)

---

# Keyboard Toolbars

![img](/assets/image12.png)

```xml
<Alloy>
    <Window id="win">
        <Toolbar platform="ios”>
            <!-- The Items tag sets the Toolbar.items property. -->
            <Items>
	    <Button systemButton="Ti.UI.iPhone.SystemButton.CAMERA" />
                <FlexSpace/>
	    <TextField />
                <Button title=“send” />
            </Items>
            <!-- Place additional views for the Toolbar here. -->
        </Toolbar>
    </Window>
</Alloy>
```

---section

# SOFT KEYBOARD HANDLING

---

# Hiding the Soft Keyboard

```javascript
$.someField.blur(); // cross-platform method 
if(OS_ANDROID) { 
     // android only method 
     Ti.UI.Android.hideSoftKeyboard(); 
} 

if(OS_IOS) { 
     Ti.App.addEventListener('keyboardframechanged', function(){ 
	   Ti.API.info('Soft keyboard shown'); 
     }); 
} 
``` 

---

# Prevent Soft Keyboard from Covering Input

- Put field in a scrolling view (i.e. ScrollView)
- On Android, set:

```javascript
$.win.windowSoftInputMode = Ti.UI.Android.SOFT_INPUT_ADJUST_PAN;
```

---

# Try It

- Create a new project or add a view to last project
- Add a textfield to the bottom of the screen
- Try adding a scrollview to move the textfield to the top

---section

# UI COMPONENTS

---

# Alert Dialog

![img](/assets/image13.png)
![img](/assets/image13a.png)

```xml
<AlertDialog id='alert'/> 
```

```javascript
"#alert": { 
     cancel: 1, buttonNames: ['Yes', 'No'], 
     message: 'Delete the file?', 
     title: 'Delete' 
} 
```

```javascript
"#alert": { 
     cancel: 1, buttonNames: ['Yes', 'No'], 
     message: 'Delete the file?', 
     title: 'Delete' 
} 

// in the controller 
$.alert.addEventListener('click', function(e) 
     { 
     if (e.index === e .source.cancel){ 
	   Ti.API.info('Cancel was clicked'); 
     } 
}); 
$.alert.show();
```

![img](/assets/image14.png)

---

# UI: Switch

![img](/assets/image15.png)

- Presents two mutually exclusive choices
- On iOS, user can turn on indicators: | (on) and 0 (off)

```xml
<Switch id='theSwitch'/> 
```

```javascript
/* in the TSS */ 
'#theSwitch[platform=android]': { 
     style: Ti.UI.Android.SWITCH_STYLE_CHECKBOX 
     /* or Ti.UI.Android.SWITCH_STYLE_TOGGLEBUTTON */ 
} 
```

```javascript
// in the controller 
$.theSwitch.addEventListener('change', function(e){ 
     if(e.value === true) { 
	// switch is on ... 
     } 
}); 
```

---

# UI: Slider

![img](/assets/image16.png)
![img](/assets/image17.png)
![img](/assets/image18.png)


```xml
<Label id='customLabel'/> 
<Slider id='theSlider'/> 
```

```javascript
/* in the TSS */ 
'#theSlider': { 
     min: 0, 
     max: 100, 
     value: 3, 
     thumbImage: 'images/skull.png' 
}
```

---

# Picker

![img](/assets/image19.png)
![img](/assets/image20.png)

```xml
<Alloy> 
  <Window backgroundColor="white"> 
  	<Picker id="picker" selectionIndicator="true" useSpinner="true"> 
       <PickerColumn id="column1"> 
    		<PickerRow title="Bananas"/> 
    		<PickerRow title="Strawberries"/> 
    		<PickerRow title="Mangos"/> 
    		<PickerRow title="Grapes"/> 
       </PickerColumn> 
       <!-- Picker shorthand notation --> 
       <Column id="column2"> 
    		<Row title="red"/> 
    		<Row title="green"/> 
    		<Row title="blue"/> 
    		<Row title="orange"/> 
       </Column> 
  	</Picker> 
  </Window> 
</Alloy> 
```

---

# Picker Events

- Listen on 'change'
- e.selectedValue
- e.row
- e.value

```javascript
$.picker.addEventListener('change',function(e){ 
	Ti.API.info(e.selectedValue); 
}); 
```

---

# Date Picker

![img](/assets/image21.png)
![img](/assets/image22.png)

```xml
<Alloy> 
  <Window backgroundColor="white"> 
    <Picker id="picker" selectionIndicator="true" type="Ti.UI.PICKER_TYPE_DATE" /> 
  </Window> 
</Alloy>
```

```javscript
// in controller 
$.picker.value = new Date(); 

$.picker.addEventListener('change',function(e){ 
     Ti.API.info(e.value.toLocaleString()) 
}); 
```

---

# Option Dialog

```xml
<Alloy> 
     <Window backgroundColor="white" layout="vertical" exitOnClose="true"> 
    	<OptionDialog id="dialog" title="Delete File?"> 	     
    	     <Options> 
        		<Option>Confirm</Option> 
        		<Option platform="ios">Help</Option>
        		<Option>Cancel</Option>
    	     </Options> 
    	     <!-- The ButtonNames tag sets the Android-only buttonNames property. --> 
    	     <ButtonNames> 
    		     <ButtonName>Confirm</ButtonName>
    	     </ButtonNames> 
    	</OptionDialog> 
     </Window> 
</Alloy> 
```

```javascript
// in controller 
$.dialog.show();
```

---

# Shadows

- Add shadows to Labels are cross-platform
- Add Shadows to buttons only on Android

![img](/assets/image23.png)

```xml
<Alloy>
	<Window id='win'>
		<Label>Hello I have a Shadow</Label>
	</Window>
</Alloy>
```

```javascript
"Label":{
  color: '#900',
  font: { fontSize:48 },
  shadowColor: '#aaa',
  shadowOffset: {x:5, y:5},
  shadowRadius: 3
}
```

---

# Summary

In this lesson, you:

- Set TextField and TextArea options
- Handled keyboard and layout issues
- Explored the available UI components

---section

# Questions?