# Goal
Prevent users from typing in non-numeric values, and limit the length of the input to 2.

![Result](http://i.giphy.com/FybgHxyxwgOR2.gif)

## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-keydown`/`ng-keyup`/`ng-keypress`| Specify an expression to evaluate upon keydown/keyup/keypress |
|`ng-mousedown`/`ng-mouseenter`/`ng-mouseleave`/`ng-mousemove`/`ng-mouseover`/`ng-mouseup`| Specify an expresson to evaluate on mousedown/mouseenter/mouseleave/mousemove/mouseover/mouseup |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Call both functions on keydown (separated by a `;`) and pass in `$event`.

## Hint #2
If the key was non-numeric or the length is already 2, prevent the default behavior of the event using `e.preventDefault()`.

## Solution
```html
<div ng-controller="myController">
	<h3>Numeric TextBox Validation on Keydown</h3>
	Age: <input type="text" ng-keydown="isNumeric($event); checkLength($event)" />
</div>
```

```javascript
$scope.isNumeric = function (e) {
	// if the key is NOT a number NOR backspace
	if (!((e.keyCode >= 48 && e.keyCode <= 57) || (e.keyCode >= 96 && e.keyCode <= 105) || (e.keyCode == 8))) {
		console.log('keypressed: ', e.key);
		console.log('length:', len);
		e.preventDefault();
	}
}
$scope.checkLength = function (e) {
	// if the key IS a number and the length is less than 2
	if (((e.keyCode >= 48 && e.keyCode <= 57) || (e.keyCode >= 96 && e.keyCode <= 105)) && len < 2) {
		len++;
		console.log('keypressed: ', e.key);
		console.log('length:', len);
	}
	// if the key is backspace and length > 0
	else if (e.keyCode == 8 && len > 0) {
		len--;
		console.log('keypressed: ', e.key);
		console.log('length:', len);
	}
	// if the length is already 2
	else if (len == 2) {
		console.log('keypressed: ', e.key);
		console.log('length:', len);
		e.preventDefault();
	}
}
```

