# Goal
- Toggle data display on button click. Make sure you disable a button if it's effect is already the current state. 
- Autofill the form by double clicking on one of the employees and call the submit function when you click the confirm button.

## Directives You Might Use
|  Name  | Description |
| ------ | ----------- |
|`ng-click`| Specify an expression to evaluate when the element is clicked |
|`ng-dblclick`| Specify an expression to evaluate when an element is double-clicked |
|`ng-disabled`| If the expression is truthy, then the disabled attribute will be set on the element |


Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Show the details div when you click the Details button. Hide it when you click the Hide button.

## Hint #2
Disable the buttons based on the truthy-ness or falsy-ness of the $scope variable `visible` which should be toggled in the `slide` function.

## Hint #3
Pass in the `winner` to the `dblClick` function on the \<select> element, and pass in the name of the winner (whether autofilled or manually entered) to the `submit` function.


## Solution
```html
<body ng-controller="mainCtrl">
	<div class="container">
		<div class="row text-center">
			<div class="col-md-12">
				<br />
				<button class="btn btn-success" ng-disabled="!visible" ng-click="slide()">Details</button>
				<button class="btn btn-success" ng-disabled="visible" ng-click="slide()">Hide</button>
				<br />
				<div class="details" style="border: solid black">
					<div style="padding:40px">
						<p>LearnKode is a website for Beginner and Professional to learn AngularJS step by step and the biggest advantage is that while learning you can experiment your code Online.</p>
						<p>Check us out at</p>
						<p><a href="www.learnkode.com" title="">www.learnkode.com</a> </p>
					</div>
				</div>
			</div>
		</div>
	</div>
	<hr>
	<div>
		Double click to select a winner: <br />
		<select size="6" ng-model="winner" ng-dblclick="dblClick(winner)" ng-options="employee as employee.name for employee in employees"></select>
		<form>
			<label>Employee Name: <input type="text" ng-model="chosen.name" required></label><br>
			<label>Employee Email: <input type="email" ng-model="chosen.email" required></label><br>
			<label>Years of Experience: <input type="text" ng-model="chosen.experience" required></label><br>
			<button type="submit" ng-click="submit(chosen.name)">Confirm Winner Selection</button>
		</form>
	</div>
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
	<script>
		var app = angular.module("app", []);
		app.controller('mainCtrl', ['$scope', function ($scope) {
			$scope.slide = function () {
				$('.details').slideToggle('slow')
				$scope.visible = !$scope.visible;
			}

			$scope.employees = [
				{ name: 'John Smith', email: 'john@smith.com', experience: 4 },
				{ name: 'Jane Doe' , email: 'jane@doe.com', experience: 5},
				{ name: 'Peter Knox' , email: 'peter@knox.com', experience: 1},
				{ name: 'Josh Mikelson' , email: 'josh@mikelson', experience: 3} ,
				{ name: 'Stephanie Lewis', email: 'stephanie@lewis.com', experience: 4 }
			];
		
			$scope.dblClick = function (employee) {
				$scope.chosen = {
					name: employee.name,
					email: employee.email,
					experience: employee.experience
				}
			}

			$scope.submit = function (name) {
				alert('You have chosen ' + name + ' as the winner!')
			}
		}]);
	</script>
</body>
```
