theme:appcelerator-training

# JavaScript

Appcelerator Certified Developer (ACD) Training

---cover

# JavaScript

## Appcelerator Certified Developer (ACD) Training

--- 

## In this lesson, you will:

- Examine JavaScript language basics
- Understand variables and scope
- Create and use functions
- Create and use objects
- Write CommonJS modules
- Write code that implements JavaScript best practices

## Try it as we go

- Use your browser's console, or
- Visit jsbin.com (turn off HTML pane, turn on JavaScript, Console, & Output)

# JAVASCRIPT BASICS

## JavaScript Building Blocks

- Data
- Variables
- Statements ("commands")
- Conditionals & Control Statements
- Functions
- Objects

## Data Types

- 1 // integer (whole numbers) 
- 1.23456 // float (fractions) 
- 'this is a string' 
- "and so is this" 
- true // or false == boolean 
- ['one', 'two', 'three'] // array 
- { color: 'blue', size: 10 } // object 
- null, undefined, NaN, Infinity // special types 

## Variables

>![image001.png](/assets/images/info/tips.gif) **TIP:** Always declare using var keyword.

```javascript
var x = 1; 
var y = 'foo'; // enclose strings in quotes 

// declare multiple w/single statement 
var i = 0, j = 1, k = true; 

y = 4; // reassigns y's value 
x = y; // put y's value into x, both x & y hold same value
```

## Statements

```javascript
var x = 100 * 2; 
var y = Math.round(22/7);
```

- Expressions that create a result
- End with a semicolon

## Comments

```javascript
// this is a comment 
var foo = 'bar'; // this is a comment too

 /* 
This is a 
multi-line comment 
*/
```

## Conditionals & Control Statements

- if/else
- For loops
- While loops
- Switch statements

## if/else

```javascript
if(somecondition) { 
     // do something 
} else if(someOtherCondition) { 
     // do stuff if someOtherCondition is met 
} else { 
     // do this if others aren't true 
}
```

## Comparison Operators

|Operators|Description|
|-|-|
|==, ===|Equals, strict-equals ('equivalent')|
|!=, !==|Not-equals, not-equivalent|
|<, <=, <==|Less-than, less-than or equal, less-than or equivalent|
|>, >=, >==|Less-than, less-than or equal, less-than or equivalent|

## == vs. ===

```javascript
var x = 1, y = '1'; 

if(x == y) { 
     // will this run? 
} 

if(x === y) { 
     // how about this one? 
}
```

```javascript
var x = 1, y = true; 

if(x == y) { 
     // will this run? 
} 

if(x === y) { 
     // how about this one? 
} 
```

- == operands converted so data types match, then equality is tested
- === must have same value and same data type; no type casting

## Ternary operator

```javascript
var foo = (isGreen == true) ? 'green' : 'blue'; 

// equivalent to 
var foo; 
if(isGreen == true) { 
     foo = 'green'; 
} else { 
	foo = 'blue'; 
} 

// general form is (condition) ? val_if_true : val_if_false; 
```

## An Assignment ’Trick’

```javascript
var baz = bar || {}; 
// baz = bar if bar != false (with type conversion, so null, '', false, etc.) 
// otherwise baz = {} -- an empty object 

// common use 
function foo(bar) { 
     var baz = bar || {}; 
     return baz.someProperty; 
} 

// equivalent 
function foo(bar) { 
     if(typeof baz == 'object') { 
          return baz.someProperty; 
     } else { 
          return null; 
} 
```

## Function Declarations

```javascript
function sum(a, b) { 
     // do as many statements as needed 
     return a + b; 
} 
// then use like this: 
var total = sum(100, 200); 
```

- Reusable chunks of code
- Arguments pass data to the function
- return a value at the end

## Function Statements

```javascript
var sum = function(a, b) { 
     return a + b; 
} 
// then use like this: 
var total = sum(100, 200); 
```

- Essentially equivalent to other format
- You're defining a variable that will hold a function
- Highlights that functions are 'first class citizens' in JavaScript
- You can pass a function as an argument to another function

## Function Callbacks

```javascript
var getAsyncData = function(fn) { 
     // this function does something that takes a long time to  finish, 
     // such as getting data from the network    
     fn(networkData); 
} 
var saveData = function(data) { 
     // this function does something with the data when it's finally available 
	return successCode; 
} 
// then use like this:
var success = getAsyncData(saveData); 
```

>![image001.png](/assets/images/info/tips.gif) **TIP:** Great when ```getAsyncData()``` might take a long time to run (like when accessing the network).

## Objects

```javascript
var cat = { 
     breed: 'tiger', 
     color: 'orange', 
     hasStripes: true, 
     growl: function() { 
          // make scary noise! 
     } 
} 
if(cat.hasStripes == true) { 
     cat.growl(); 
}
```

## Core vs. Host

- Core JavaScript
  - Overall language rules & syntax
  - Core operators
  - Objects like Date and Math
- Host environment adds its own objects
  - Web browser (DOM)
  - Node.js (server-side functionality)
  - Titanium (Ti object for mobile components)
- Libraries you import (APIs)

## ECMA & JavaScript Evolution

- Original release in late 1995
- Standardized by ECMA in 1998
- Current ECMA standard is ECMAScript 5 (2010)
- JavaScriptCore is Apple's JavaScript engine, used by Titanium on Ios
- V8 is the Chrome JavaScript engine, used by Titanium on Android
- V8 & JSCore, thus Titanium, support nearly all of ECMAScript 5

# VARIABLES

```javascript
var one = '1', two = 2, three='three'; 

// JavaScript will concatenate if either operand is a string 
console.log(one + 1); // = 11 

// it will convert when a NaN value might result 
console.log(one * 2); // = 2 

// you can force a data type 
console.log(parseInt(one) + 1); //s = 2 
console.log(String(1) + one); // = 11 

// unless NaN would result 
console.log(String(one) * 2); // = 2 

isNaN(parseInt(three)); // == true 
```

- Automatic
- Helper functions
- Casting

## Variable Scope

```javascript
var foo = 'bar'; // defined in the global scope 
var fn = function() { 
     var one = 1; // local to the function 
     console.log(foo); // works! 
     oops = 'global'; // omitting 'var' defines 
                              // this in the global scope 
}; 

fn(); // run function, outputs 'bar' 
console.log(oops); // outputs 'global' 
console.log(one); // throws error 
```

- Global scope
- Function scope
- Block scope (ECMA 6)
- "Accidental" globals

## Variable Hoisting

- Var declarations moved to top
- Var initializations are not

```javascript
baz ( foo ) ;
var foo = ‘ bar ’ ;
function baz ( f )  { }

// is treated like 
var foo ;
function baz ( f )  { }
baz  ( foo ) ;
foo = ‘ bar ’ ;
```

- Function declarations are hoisted
- Function statements are not

```javascript
var foo = function() { 
     bar(); 
foo(); // outputs 'I work!' 
baz(); // 'baz is not a function' 
function bar() { 
     console.log('I work!'); 
}}; 

var baz = function() { 
console.log('I do not'); 
};
```

## What's the Output?

```javascript
var is_android = true; 
if(is_android) { 
     function foo() { 
           console.log('I am Android'); 
     } 
} else { 
     function foo() { 
          console.log('I am NOT Android'); 
     } 
} 
foo(); 
```

**Answer**: I am NOT Android – because declaration of foo () is hoisted

# FUNCTIONS

- JS functions can accept variable number of arguments without error
- arguments - array-like object
- But it's not an Array (no properties other than length)

```javascript
function foo(one, two) { 
     console.log(one); 
     console.log(two); 
     if(arguments.length > 2) { 
         console.log(arguments[2]); 
     } 

      // this would fail 
      console.log(arguments.join(', ')); 

      // but this would work 
      var args = Array.prototype.slice.call(arguments); 
      console.log(args.join(', ')); 

} 

foo(1, 2, 3);
```

## Pass by Reference or Value?

```javascript
var cat = { 
color: 'orange' 
}; 
function changeCatColor(feline) { 
     // obj reference passed in 
     feline.color = 'black'; 
     feline.claws = 'sharp'; 
     feline = { 
          color: 'brown' 
     };
} 
changeCatColor(cat); 
console.log(cat.color); // outputs 'black' 
console.log(cat.claws); // outputs 'sharp‘
```

- Simple variables passed by value
- Objects passed by reference
- Pedantically, everything is passed by value, but with objects that value is a reference to the object

```javascript
function changeIt ( y )  {
     y = 5 ;
}
var  x = 4 ;
console.log ( x ) ; // x is equal to 4
changeIt ( x ) ;
console.log ( x ) ; // x is still equal to 4;
```

## Self-calling Functions

- Define, then execute, a function
- Wrap function definition in ()
- Add () at the end (to call it)
- Works with function statements

```javascript
// define & declare Counter 
var Counter = (function() { 
     var privateCounter = 0; 
     return { 
          increment: function() { 
              privateCounter++; 
          }, 
          decrement: function() { 
               privateCounter--; 
          }, 
           value: function() { 
                return privateCounter; 
           } 
      }; 
})(); 
```

# Objects

## Object Literals

- Define objects with {}
- Add properties later or access via dot-notation
- Define properties as map during creation

```javascript
var person = {}; 
// equivalent to 
// var person = new Object(); 
person.name = 'Ralphie'; 

var person = { 
     name: 'Ralphie', 
     speak: function() { 
          console.log('You\’ll shoot your eye out'); 
     } 
}; 
```

## Functions as Constructors

```javascript
function Person(name) { 
      this.name = name; 
} 

var jim = new Person('Jimmy'); 
console.log(jim.name); // outputs 'Jimmy' 

var jane = Person('Jane'); 
console.log(jane.name); // throws error 

// though in browser environment: 
var jane = Person('Jane'); 
console.log(window.name); // outputs 'Jane' 
```

- Functions that create objects
- Use care omitting 'new’
- ```this``` == object being instantiated with ```new```
- ```this``` == global object without ```new```

## Implicit vs. Explicit Returns

```javascript
function Person(name) { 
this.name = name; 
} 
function Android(name) { 
     return { 
          name: name 
     }; 
} 

var jim = new Person('Jimmy'); 
alert(jim.name); // => Jimmy 
var jane = Person('Jane'); 
alert(jane.name); // => undefined! 
alert(window.name); // => 'Jane' 

var data = new Android('Cmdr Data'); 
console.log(data.name); // => Cmdr Data 
var lore = Android('Lore'); 
console.log(lore.name); // => Lore 
```

- Implicit = no return statement
- Used with a constructor, returns the object that was created
- Implicit returns can cause problems — if you later forget 'new'

# MODULES

## CommonJS

- Standard way to create self-contained, exportable functionality. See commonjs.org for the spec.
- Goals:
  - Private scope within the module
  - Explicitly exported API
  - Decoupling and reusability
- Inside a module, exports is an object to which you can attach properties
- You can replace that object by setting module.exports
- Modules "imported" with the require() global function

## Helper / Library Pattern

```javascript

// file is network.js 
exports.getData = function() { 
     // get data from the network 
}; 
exports.postData = function() { 
     // post data to the network 
};
```

```javascript
// how to use it 

var net = require('network'); // no '.js'!! 

var someData = net.getData(); 
button.addEventListener('click', function() { 
     net.postData(someData); 
}); 
```

## Factory Pattern

```javascript
// file is Button.js 

// creates a UI component we'll need many copies of 
var Button = function(title) { 
               return Ti.UI.createButton({ title: title }); 
}; 
module.exports = Button; // return the constructor 
```

```javascript
// how to use it 
var Button = require('ui/Button'); 

// now make some instances 
var button1 = new Button('foo'); 
var button2 = new Button('bar'); 
```

## Modules in Titanium

- Caching — module isn't re-evaluated with subsequent require()'s
- Omit leading '/' ... require('ui/somemodule')
- Paths are relative to Resources directory
- Pass in live data the module will need (e.g. a user object)
- Require in any libraries/modules the module will need (e.g. your database module)

# BEST PRACTICES

## Code for Readability

- Naming variables and objects
- Spacing and indentation
- Pass {} rather than a list of arguments
- Comments

```javascript
var a; // not so good 
var object_user_level_superadmin; // ugh 
var admin; // Goldilocks! 

myFunc(1, 2, 1, 3); // unclear 
myFunc({ 
     height: 1, width: 2, left: 1, right: 3 
}); // much clearer 
```

## Garbage Collection

- Automatic via "mark & sweep“
- Objects collected when no references remain
- Nothing in the global space is ever collected!
- "Force" collection by encapsulating within functions or modules that will go out of scope

## Avoiding Memory Leaks

- Don't store variables in the global scope
- Set objects = null when no longer needed
- Watch for "hidden" references in functions, closures, event listeners, accidental global assignments
- Profile your app

## Performant Coding

>![image001.png](/assets/images/info/important.png) **WARNING:** Ti.include() is deprecated.  Use commonJS instead.

- Defer execution — load modules as needed & don't use Ti.include() 
- Modules cache code so it's not re-evaluated
- Avoid the global scope
- Use closures sparingly
- Avoid eval() and implicit evals
- Don't change data types stored in a variable

## Performant Loops

- Set upper bound before loop
- For/in loops slower than for or while
- Define local references
- Operators a little faster than functions'

```javascript
// with arr.length = 10000 
for(var i=0, j=arr.length; i < j; i++) {} 
// is faster than 
for(var i=0; i < arr.length; i++) {} 

var foo = bar.someproperty.anotherproperty 
while(foo < 10) { } 
// faster than 
while(bar.someproperty.anotherproperty < 10) { } 

for(var i=0; i < 100; i++) { 
     someVal = (a < b) ? a : b; 
     // is a tiny bit faster than 
     someVal = Math.min(a,b); 

      arr[arr.length] = newMember 
      // is faster than 
      arr.push(newMember) 
} 
```

# Summary

In this lesson, you:

- Examined JavaScript language basics
- Gained an understanding of variables and scope
- Learned how to create and use functions
- Learned how to create and use objects and manage inheritance
- Examined CommonJS modules
- Examined code that implements JavaScript best practices

---section

# Questions?