# Goal
When the form is invalid, show the warnings and disable the button. When the form is valid, do not show the warnings, and on submission, display the saved user.

![Result] (http://i.giphy.com/yFzpR80HvfTFu.gif)

## Directives You Might Use
|  Name  | Description |
| ------ | ----------- |
|`ng-submit`| Specify an expression to evaluate on form submission |
|`ng-disabled`| If the expression is truthy, then the disabled attribute will be set on the element |
|`ng-model`| Bind an `input`, `select`, `textarea` (or custom form control) to a property on the $scope |
|`ng-show`| If the expression is truthy then the element is shown or hidden respectively |
|`ng-if`| If the expression is falsy then the element is removed from the DOM tree. If it is truthy a copy of the compiled element is added to the DOM tree. |


Basic examples of these directives have been included. If running these with live-server, run `live-server <name-of-file>`.

## Hint #1
Invoke the `submit` function on form submission.

## Hint #2
Bind the username input to the userName property of an object called `user`. Bind the password input to the password property of `user`. 

## Hint #3
Only show the warnings if there are errors in the form. Error detection takes the form
```html
nameOfYourForm.nameOfInputField.$error.theAttributeItDidNotSatisfy
```
Only show the `submitted` div if a user has been submitted

## Hint #4
Disable the button if the form is not valid. Form validation (a boolean) takes the form
```html
nameOfYourForm.$valid
```

## Solution
```html
<div>
	<form name="myForm" ng-submit="submit(user)">
		<label>User Name: <input class="form-control" type="text" name="uname" required ng-model="user.userName"></label>
		<br>
		<span class="warn" ng-show="myForm.uname.$error.required">Username is required!</span>
		<br />
		<label>Password: <input class="form-control" type="password" name="password" required ng-model="user.password" minlength="5"></label>
		<br>
		<span class="warn" ng-show="myForm.password.$error.required">Password is required!</span>
		<span class="warn" ng-show="myForm.password.$error.minlength">Password is too short!</span>
		<br />
		<button class="btn" ng-disabled="!myForm.$valid" type="submit">Save</button>
	</form>
</div>
<div id="submitted" ng-if="submittedUser">
	User: {{submittedUser}}
</div>
```
