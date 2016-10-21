# Goal
Apply the `active` class to the selected `menu` class item, and display the appropriate content based on the value of `tab`. This can be accomplished using either `ng-switch` or `ng-if`. Try doing it both ways!

## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-switch`| Conditionally swap DOM structure on your template based on a scope expression |
|`ng-if`| If the expression is falsy then the element is removed from the DOM tree. If it is truthy a copy of the compiled element is added to the DOM tree. |
|`ng-class`| Dynamically set CSS classes on an element by binding an expression that represents all classes to be added |
|`ng-click`| Specify an expression to evaluate when the element is clicked |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Remember the syntax for conditionally setting a class is:
```html
ng-class="{className: truthyExpression}"
```

## Hint #2
Set the `ng-switch` tag on the `content` div, and tell it to switch its content based on the `tab variable.

## Hint #3
Set the `ng-switch-when` tag on each of the divs inside the `content` div, providing it with a value of `tab` that it should display on. Use the `ng-switch-default` tag on the `other` div to show this when `tab` doesn't have a value.

## Solution with `ng-switch`
```html
<div id="header" class="row">
	<div class="col-md-1 menu" ng-class="{active: tab == 'Angular'}" ng-click="tab='Angular'"><b>Angular</b></div>
	<div class="col-md-1 menu" ng-class="{active: tab == 'Jquery'}" ng-click="tab='Jquery'"><b>Jquery</b></div>
	<div class="col-md-1 menu" ng-class="{active: tab == 'Bootstrap'}" ng-click="tab='Bootstrap'"><b>Bootstrap</b></div>
</div>
<div id="content" class="row" ng-switch="tab">
	<div class="col-md-4" style="background-color:yellow" ng-switch-when="Angular">
		<h3>Angular JS</h3><br />
		HTML is great for declaring static documents, but it falters when we try to use it for declaring dynamic views in web-applications. AngularJS lets you extend HTML vocabulary for your application. The resulting environment is extraordinarily expressive, readable, and quick to develop.
	</div>
	<div class="col-md-4" style="background-color:yellow" ng-switch-when="Jquery">
		<h3>Jquery</h3><br />
		jQuery is a cross-platform JavaScript library designed to simplify the client-side scripting of HTML. jQuery is the most popular JavaScript library in use today, with installation on 65% of the top 10 million highest-trafficked sites on the Web. jQuery is free, open-source software licensed under the MIT License.
	</div>
	<div class="col-md-4" style="background-color:yellow" ng-switch-when="Bootstrap">
		<h3>Bootstrap</h3><br />
		Bootstrap is a technique of loading a program into a computer by means of a few initial instructions which enable the introduction of the rest of the program from an input device.
	</div>
	<div class="col-md-4" style="background-color:yellow" ng-switch-default>
		<h3>Other</h3><br />
		Choose your own advendure!
	</div>
</div>
```

## Solution with `ng-if`
```html
<div id="header" class="row">
	<div class="col-md-1 menu" ng-class="{active: tab == 'Angular'}" ng-click="tab='Angular'"><b>Angular</b></div>
	<div class="col-md-1 menu" ng-class="{active: tab == 'Jquery'}" ng-click="tab='Jquery'"><b>Jquery</b></div>
	<div class="col-md-1 menu" ng-class="{active: tab == 'Bootstrap'}" ng-click="tab='Bootstrap'"><b>Bootstrap</b></div>
</div>
<div id="content" class="row">
	<div class="col-md-4" style="background-color:yellow" ng-if="tab=='Angular'">
		<h3>Angular JS</h3><br />
		HTML is great for declaring static documents, but it falters when we try to use it for declaring dynamic views in web-applications. AngularJS lets you extend HTML vocabulary for your application. The resulting environment is extraordinarily expressive, readable, and quick to develop.
	</div>
	<div class="col-md-4" style="background-color:yellow" ng-if="tab=='Jquery'">
		<h3>Jquery</h3><br />
		jQuery is a cross-platform JavaScript library designed to simplify the client-side scripting of HTML. jQuery is the most popular JavaScript library in use today, with installation on 65% of the top 10 million highest-trafficked sites on the Web. jQuery is free, open-source software licensed under the MIT License.
	</div>
	<div class="col-md-4" style="background-color:yellow" ng-if="tab=='Bootstrap'">
		<h3>Bootstrap</h3><br />
		Bootstrap is a technique of loading a program into a computer by means of a few initial instructions which enable the introduction of the rest of the program from an input device.
	</div>
	<div class="col-md-4" style="background-color:yellow" ng-if="!tab">
		<h3>Other</h3><br />
		Choose your own advendure!
	</div>
</div>
```
