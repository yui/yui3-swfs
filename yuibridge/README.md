YUIBridge (deprecated)
=========
<p>YUIBridge (deprecated) ActionScript library creates a standardized method for sending YUI events from a Flash application. In an ActionScript application, an instance of YUIBridge is created as follows:</p>

	
```
	import com.yahoo.util.YUIBridge
	
	...

	// The scope for 'this' should be either the top-level application
	// or a Sprite that has been placed on the stage.
	
	var yuiBridge:YUIBridge = new YUIBridge(this.stage);
```

<p>Instead of using `ExternalInterface.addCallback` on each method that needs to be exposed to JavaScript, you can instead call a collective `addCallbacks()` method available in YUIBridge:</p>

```
	import com.yahoo.util.YUIBridge
	
	...

	// The scope for 'this' should be either the top-level application
	// or a Sprite that has been placed on the stage.
	
	var yuiBridge:YUIBridge = new YUIBridge(this.stage);
	yuiBridge.addCallbacks({externalMethodName:internalMethod, externalMethodName2:internalMethod2});

});
```

<p>To dispatch YUI events (fired by the instance of the SWF Utility on the JavaScript end, you can call YUIBridge's `sendEvent` method:</p>

```
	import com.yahoo.util.YUIBridge
	
	...

	// The scope for 'this' should be either the top-level application
	// or a Sprite that has been placed on the stage.
	
	var yuiBridge:YUIBridge = new YUIBridge(this.stage);
	yuiBridge.sendEvent({type:'someevent', payload:'some payload'});
});
```

<p>In addition to any custom events you dispatch, YUIBridge also fires a `swfReady` event at initialization time, announcing that the Flash player is ready for communication with JavaScript:</p>
```
YUI({...}).use('swf',function (Y) {

	var myswf = new Y.SWF("#swfContainer", "http://example.com/example.swf");
	myswf.on('swfReady', init);
	
	function init() {
		// Start communicating with the Flash player instance here
		myswf.callSWF("foo", [arg1, arg2]);
	}

});
```

