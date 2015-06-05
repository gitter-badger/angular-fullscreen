AngularJS HTML5 Fullscreen 
=======

[![Join the chat at https://gitter.im/francesco-strazzullo/angular-fullscreen](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/francesco-strazzullo/angular-fullscreen?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

An AngularJS service and a directive to quickly use the HTML5 fullscreen API and set the fullscreen to the document or to a specific element.

## Example
Live demo: http://www.fabiobiondi.com/demo/github/angular-fullscreen/demo/

## Usage
Add AngularJS and the angular-fullscreen.js to your main file (index.html)
	
```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.2.1/angular.min.js"></script>
<script src="angular-fullscreen.js"></script>
```


Set `FBAngular` as a dependency in your module:

```javascript
var app = angular.module('YourApp', ['FBAngular'])
```

## Fullscreen Directive
Set the `fullscreen` attribute to a specific element:

```html
<img id="img1" src="imgs/P1030188.JPG" fullscreen />
```
The only requirement is to set a different ID to all elements that you will flag as `fullscreen`.


## Fullscreen Service
You can also use the `Fullscreen` service into your controller:

Controller:
```javascript
function MainCtrl($scope, Fullscreen) {

   $scope.goFullscreen = function () {

      if (Fullscreen.isEnabled())
         Fullscreen.cancel();
      else
         Fullscreen.all();

      // Set Fullscreen to a specific element (bad practice)
      // Fullscreen.enable( document.getElementById('img') )

   }

}
```

HTML:
```html
<button ng-click="goFullscreen()">Enable/Disable fullscreen</button>
```

## Alternative Approach
You may pass in the name of a scope property to watch. When the property
becomes truthy, the element will become full screen:

Controller:
```javascript
function MainCtrl($scope) {
    // Initially, do not go into full screen
    $scope.isFullscreen = false;

    $scope.toggleFullScreen = function() {
        $scope.isFullscreen = !$scope.isFullscreen;
    }
}
```

HTML:
```html
<div fullscreen="isFullscreen">Lorem ipsum...</div>
<button ng-click="toggleFullScreen()">Toggle Full Screen</button>
```

#### Available Methods

Method | Details
:---------------------- | :------ 
all()                  		 | enable document fullscreen
enable(elementID)	 | enable fullscreen to a specific element
cancel()			 | disable fullscreen
isEnabled()			 | return true if fullscreen is enabled, otherwise false



## Example
You can check out this live example here: 
http://www.fabiobiondi.com/demo/github/angular-fullscreen/demo/
