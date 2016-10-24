# Goal
Update the view to display the selected choice sandwich. See what you can come up with on your own before looking at the hints/solution below.

![Result](http://i.giphy.com/kdleEaUwcZlV6.gif)

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
Invoke the `choose` function on `ng-change`, passing in 2 arguments.

## Hint #3
Set/update the `choice` variable in the `choose` function based on the value(s) passed into the `choose` function.

## Hint #4
Use `ng-show` to only show the choice div once `choice` has been set.

## Solution
```html
<div class="container">
	<div>
		<h3>Build Your Sandwich</h3>
		<label>Meat:
			<input type="radio" name="meat" value="Chicken" ng-model="meatChoice" ng-change="choose(meatChoice, condChoice)"> Chicken</input>
			<input type="radio" name="meat" value="Turkey" ng-model="meatChoice" ng-change="choose(meatChoice, condChoice)"> Turkey</input>
		</label><br>
		<label>Condiment:
			<input type="radio" name="cond" value="Ketchup" ng-model="condChoice" ng-change="choose(meatChoice, condChoice)"> Ketchup</input>
			<input type="radio" name="cond" value="Mustard" ng-model="condChoice" ng-change="choose(meatChoice, condChoice)"> Mustard</input>
			<input type="radio" name="cond" value="" ng-model="condChoice" ng-change="choose(meatChoice, condChoice)"> None</input>
		</label><br>
	</div>
	<div ng-show="choice">
		{{choice}}
	</div>
</div>
```
```javascript
$scope.choose = function(meat, cond) {
	if (!cond) {
		$scope.choice = 'You chose a ' + meat + ' sandwich.';
	} else if (!meat) {
		$scope.choice = cond + ' by itself is disgusting.'
	} else {
		$scope.choice = 'You chose a ' + meat + ' sandwich with ' + cond + '.';
	}
}
```