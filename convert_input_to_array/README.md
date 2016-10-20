# Goal
Convert inputs separated by commas, newlines, or spaces into arrays.

## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-model`| Bind an `input`, `select`, `textarea` to a property on the $scope |
|`ng-list`| Specify a delimiter to convert between a delimited string and an array of strings |
|`ng-trim`| If the value is set to false, AngularJS won't trim the input automatically |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
`ng-trim` is `true` by default. Only change it to `false` if you need to.

## Hint #2
The newline character is represented by `&#10;`. 

## Solution
```html
<div>
	<p>Add all the cities you've lived in, separated by commas</p>
	<label>Cities: <input type="text" ng-model="cities" ng-list></label>
	<p>{{cities}}</p>
</div>
<hr>
<div>
	<p>Add a list of email addresses, each one on a new line</p>
		<label>Emails: <textarea ng-model="emails" ng-trim="false" ng-list="&#10;" rows="4", cols="20"></textarea></label>
		<p>{{emails}}</p>
</div>
<hr>
<div>
	<p>Write your full name</p>
	<label>Name: <input type="text" ng-trim="false" ng-model="name" ng-list=" "></label>
	<p>{{name}}</p>
</div>
```