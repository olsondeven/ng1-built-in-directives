# Goal
- Set the `background` property on the divs with the `set1` class using data returned from an API call. Do the same thing for the `set2` class. 
- Once the data comes back, hide the loading spinner and show the div with the `data` id. 
- Add the class that corresponds to the selected option onto the `set1` images.
-  Assign the class of `round` to the even items in the `set2` class, and the class of `sm` to the odd items.


## Directives You Might Use
|  Name  | Description |
| ------ | ----------- |
|`ng-show` | If the expression is truthy then the element is shown or hidden respectively |
|`ng-hide` | If the expression is truthy then the element is shown or hidden respectively |
|`ng-style` | Specify an expression which evaluates to an object whose keys are CSS style names and values are corresponding values for those CSS keys. |
|`ng-class` | Dynamically set CSS classes on an element by binding an expression that represents all classes to be added |
|`ng-init` | Evaluate an expression in the current $scope when the element is initialized |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Use this syntax to set a style using a scope variable:
```html
ng-style="{'background': 'url('+someScopeVariableGoesHere+') no-repeat'}"
```

## Hint #2
Once the data comes back, your $scope variables are defined. Use the existence (or non-existence) of one of these for your `ng-show`/`ng-hide`.

## Hint #3
The selected option is bound to the $scope variable `boxSize`, and the value corresponds to a classname. Set this classname onto the `set1` images. 

## Hint #4
Assign `ng-class-even` and `ng-class-odd` on the `set2` images.

## Solution
```html
<div ng-controller="myCtrl" ng-init="boxSize='sm'">
	<h1 id='loading' ng-hide="front">Your images are loading <i class="fa fa-spin fa-spinner"></i></h1>
	<div id="data" ng-show="front">
		<select ng-model="boxSize" >
			<option value="sm">small</option>
			<option value="md">medium</option>
			<option value="lg">large</option>
		</select>
		<div ng-style="{'display':'flex'}">
			<div class="set1" id="front" ng-style="{'background': 'url('+front+') no-repeat'}" ng-class="boxSize">
			</div>
			<div class="set1" id="back" ng-style="{'background': 'url('+back+') no-repeat'}" ng-class="boxSize">
			</div>
			<div class="set1" id="front-shiny" ng-style="{'background': 'url('+frontShiny+') no-repeat'}" ng-class="boxSize">
			</div>
			<div class="set1" id="back-shiny" ng-style="{'background': 'url('+backShiny+') no-repeat'}" ng-class="boxSize">
			</div>
		</div>
		<hr>
		<div ng-style="{'display':'flex'}">
			<div id="pictures" ng-repeat="pic in all">
				<div class="set2" ng-style="{'background': 'url('+pic+') no-repeat'}" ng-class-even="'round'" ng-class-odd="'sm'">
				</div>
			</div>
		</div>
	</div>
</div>
```
