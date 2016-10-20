# Goal
Update the view to display the selected choice (if one is selected). See what you can come up with on your own before looking at the hints/solution below.

## Directives You Might Use
| Name | Description |
| ---- | ----------- |
|`ng-change`| Specify an expression to evaluate upon change in input value |
|`ng-model`| Bind an `input`, `select`, `textarea` to a property on the $scope. |
|`ng-show`| If the expression is truthy then the element is shown or hidden respectively |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
`ng-change` requires there to be an `ng-model` on the element as well. 

## Hint #2
Invoke the `choose` function on `ng-change`.

## Hint #3
Set/update the `choice` variable in the `choose` function based on the value passed in from `ng-model`.

## Hint #4
Use `ng-show` to only show the choice div once `choice` has been set.

## Solution
```html
<div class="container">
	<div>
		<label>Choice 1: <input type="radio" name="choice" value="Option 1" ng-model="choice1" ng-change="choose(choice1)"></label><br>
		<label>Choice 2: <input type="radio" name="choice" value="Option 2" ng-model="choice2" ng-change="choose(choice2)"></label><br>
		<label>Choice 3: <input type="radio" name="choice" value="Option 3" ng-model="choice3" ng-change="choose(choice3)"></label><br>
	</div>
	<div ng-show="choice">
		{{choice}}
	</div>
</div>
```

