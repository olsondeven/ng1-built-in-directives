# Goal
Initialize the country \<select> to India, and set the options for the state \<select> without cluttering the html with a ton of \<option> tags. You'll want to use an Angular filter (like the one already being used on the State `ng-model`) to make sure you're only providing options that correspond to the selected Country.


## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-selected`| If the expression is truthy, then special attribute "selected" will be set on the element |
|`ng-options`| Dynamically generate a list of \<option> elements for the \<select> element |
|`ng-init`| Evaluate an expression in the current $scope when the element is initialized |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Set the default/selected option (using `ng-selected`) for the country `select` element by checking if `Country` is undefined.

## Hint #2
For using an array of objects in `ng-options` the syntax is:
```html
ng-options="item.prop as item.prop for item in items"
```

## Solution
```html
<div ng-controller="myCtrl">
	Country <select ng-model="Country">
		<option value="India" ng-selected="!Country">India</option>
		<option value="Canada">Canada</option>
	</select><br /><br />
	State <select ng-model="(States | filter: Country)[0].Name" ng-options="state.Name as state.Name for state in States | filter: Country">
	</select>
</div>
```