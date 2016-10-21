# Goal
Prevent users from typing in non-numeric values, and limit the length of the input to 2.

## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-keydown`/`ng-keyup`/`ng-keypress`| Specify an expression to evaluate upon keydown/keyup/keypress |
|`ng-mousedown`/`ng-mouseenter`/`ng-mouseleave`/`ng-mousemove`/`ng-mouseover`/`ng-mouseup`| Specify an expresson to evaluate on mousedown/mouseenter/mouseleave/mousemove/mouseover/mouseup |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Call both functions on keydown and pass in `$event`.

## Hint #2
Prevent the default behavior of the event using `e.preventDefault()`.

## Solution
```html
<div ng-controller="myController">
	<h3>Numeric TextBox Validation on Keydown</h3>
	Age: <input type="text" ng-keydown="isNumeric($event); checkLength($event)" />
</div>
```

```javascript
$scope.isNumeric = function (e) {
	if (!((e.keyCode >= 48 && e.keyCode <= 57) || (e.keyCode >= 96 && e.keyCode <= 105) || (e.keyCode == 8))) {
		 e.preventDefault();
	}
}
var len = 0;
$scope.checkLength = function (e) {
	if (((e.keyCode >= 48 && e.keyCode <= 57) || (e.keyCode >= 96 && e.keyCode <= 105) || (e.keyCode == 8))) {
		len++;
	}
	if (len > 2) {
		e.preventDefault();
	}
}
```

