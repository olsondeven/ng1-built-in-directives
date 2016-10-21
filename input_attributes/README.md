# Goal
Connect the account type to the value of `$scope.admin`. For users, the email is required, account # is readonly, and the subscription is checked. For admin, the email is readonly, and the subscription is unchecked.

## Directives You Might Use
|  Name  | Description |
| ------ | ----------- |
|`ng-value`| Specify an expression whose value will be bound to the "value" attribute of the element |
|`ng-required`| If the expression is truthy, then the "required" attribute will be applied to an input element |
|`ng-readonly`| If the expression is truthy, then special attribute "readonly" will be set on the element |
|`ng-checked`| If the expression is truthy, then the checked attribute will be set on the element |
|`ng-model`| Bind an `input`, `select`, `textarea` (or custom form control) to a property on the $scope. |

Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Use `ng-model` and `ng-value` on the radio buttons to change the value of `$scope.admin`.

## Hint #2
Set the readonly and required attributes based on if `$scope.admin` is true or false.

## Hint #3
Set the value of the account number and make it readonly if `$scope.admin` is false.

## Hint #4
Check the subscription box with `ng-checked` if `$scope.admin` is false.

## Solution
```html
<form ng-submit="submit()">
	<label>Account Type: <br>
		<input type="radio" name="type" ng-model="admin" ng-value="true"> Admin 
		<input type="radio" name="type" ng-model="admin" ng-value="false"> User
	</label> <br>
	<label>Name: <input type="text" class="form-control" ng-model="name"></label><br>
	<label>Email: <input type="email" class="form-control" ng-model="email" ng-readonly="admin==true" ng-required="admin==false"></label><br>
	<label>Account # (office use only): <input type="text" class="form-control" ng-value="acctNum" ng-readonly="admin==false"></label><br>
	<input type="checkbox" ng-model="subscribe" ng-checked="admin==false"> Send me tons of unnecessary junk mail. <br>
	<button type="submit" class="btn btn-success">Submit</button>
</form>
```
