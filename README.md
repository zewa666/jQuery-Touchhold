jQuery TouchHold Plugin
=======================

jQuery TouchHold provides event bindings for 'tap-and-hold' or 'longtap' events on touch devices. 

Unlike other touch libraries with support for long tap events, jQuery TouchHold allows you to bind two different event handlers: 
* When the user finishes a long tap, a "touchhold.end" event is triggered
* While the user is still touching the screen, a preliminary "touchhold.start" event is triggered signifying that enough time has elapsed for the touch to be considered a long tap, and a second when the user finishes the tap. 

This allows you to accurately imitate native iOS behavior, where a selected element is highlighted before the user takes their finger off the screen (as in native iOS text selection).

jQuery is currently a prerequisite. I haven't tested with Zepto.js, but it's possible it might work.

Usage
-----
To bind an event that fires after a user completes a long tap, you can just write:

```js
	$("#selector").touchhold(function() {});
```

You can essentially treat .touchhold() like any of the default jQuery event binding helpers (.click(), .doubleclick(), etc).

If you want a function to be called when the current touch is long enough to be considered a long touch, just pass the function in as an optional second parameter:

```js
	var foo = function() { console.log("You completed a long tap."); }, 
		bar = function() { console.log("You held down your finger long enough.")}
		
	$("#selector").touchhold(foo, bar);
```

If you only want to bind a function to fire on the timeout, you can pass in your favorite falsy value as the first parameter; as long as it's not a function, it won't get called. 


To Do
-----
* 'touchhold.start' and 'touchhold.end' events can't be bound via .bind or .delegate without having called .touchhold() first on that element.
* Eliminate jQuery dependency