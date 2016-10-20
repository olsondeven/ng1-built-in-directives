# Goal
Prevent a user from cutting/copying/pasting text in the \<input> fields.


## Directives You Might Use
|  Name  | Description |
| ------ | ----------- |
|`ng-copy`| Specify an expression to evaluate when the contents of an element are copied |
|`ng-cut`| Specify an expression to evaluate when the contents of an element are cut |
|`ng-paste`| Specify an expression to evaluate when the contents of an element are pasted |


Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Invoke the `cheating` function on cut/copy/paste, passing in `$event`.

## Solution
```html
<div ng-controller="controllerName">
	<label>Try to cut/copy: <input ng-cut="cheating($event)" ng-copy="cheating($event)" ng-model="data"/></label>
	<button ng-click="randomString()">New string</button>
	<br>
	<label>And paste it here: <input type="text"></label>
	<hr>
	<label>You can't paste anything here: <input ng-paste="cheating($event)" ng-model="typing"></label>
	{{typing}}
</div>
```
