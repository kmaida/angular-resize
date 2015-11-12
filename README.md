#angular-resize

AngularJS service implementation of debounced `window resize` event handler.

Inject the `resize` service into your application module:

```
angular.module('myApp', ['resize']);
```

Inject the `resize` service into your application where you'd like to implement it.

```
angular
	.module('myApp')
	.controller('MainCtrl', function(resize) {
		resize.init({
			scope: $scope,
			resizedFn: function() { //window was resized! },
			debounce: 200
		});
	});
```

##Options

###scope

* Type: `scope object`
* Default: *none*

`scope` is needed to unbind the `resize` listener when `$scope` is destroyed. This prevents the event handler from 
leaking into undesired areas of your single page application.

###resizedFn

* Type: `function`
* Default: *none*

`resizedFn` is the debounced function you'd like to run as your `resize` handler. This function will run when the 
viewport is resized.

###debounce

* Type: `integer`
* Units: `milliseconds`
* Default: `100`

`debounce` is the number in milliseconds to wait before executing the `resizedFn` function while the window is 
actively being resized. If no value is provided, a default of `100` will be used. `0` is an acceptable (but 
inadvisable) valid value if no debouncing is desired.