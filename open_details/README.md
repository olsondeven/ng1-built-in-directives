# Goal
Use the checkbox to open/close all lists.

![Result](http://i.giphy.com/41q9DMP8M4STS.gif)

## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-open`| If the expression is truthy, then special attribute "open" will be set on the element |
|`ng-model`| Bind an `input`, `select`, `textarea` (or custom form control) to a property on the $scope |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Bind a property to the \<input> using `ng-model` and use that property to set the `ng-open`.

## Solution
```html
<body ng-app>
	Expand all: <input type="checkbox" ng-model="open"><br/>
	<details id="details" ng-open="open">
		<summary>Colors</summary>
		<ul>
			<li>Brown</li>
			<li>Black</li>
			<li>White</li>
			<li>Slate Grey</li>
		</ul>
	</details>
	<details id="details" ng-open="open">
		<summary>Sizes</summary>
		<ul>
			<li>XS</li>
			<li>SM</li>
			<li>MD</li>
			<li>LG</li>
		</ul>
	</details>
</body>
```

