# Functions

## Limit function length

A function should rarely grow to 50 lines long, and should never be 100 lines long. A rule of thumb is to have a soft limit of 50 lines for function length. Hitting this limit indicates that the function's implementation is too specific and requires refactoring.

Try to keep a function as short as possible. When a function becomes too long, describe what its logical steps are, and use that description to name child functions that can be called in order from the now abstract parent function.

## Ensure return points are consistent

A function that returns something should do so in a consistent manner. There will always be a return statement at the end of the function, but some functions will decide what to return based on some program logic, and when and where to return needs to be decided.

There are two approaches: return only at the end of the function, or return at predictable and easy-to-read locations in the function.

Returning only at the end of the function can be achieved by declaring the variable to return with a default value at the start of the function, and having the logic checks manipulate the variable, before eventually returning it:

```php
function getMessage(string $name, int $age):string {
// First, set the $message variable. It's obvious to future readers that this
// is the variable we will be returning, because of the name of the function
// and the name of this variable.
	$message = "Welcome, $name";
	
// Next, perform any logic that will affect the return variable. This must
// be short and concise. Refactor if the function becomes too long.
	if($age < AGE_THRESHOLD) {
		$message = "Sorry, $name, you are too young to enter";
	}
	
// Finally, return the variable declared at the top of the function.
	return $mesage;
}
```

This style is particularly useful if there are multiple decisions to make that affect the returned value.

The other option is to return early:

```php
function getMessage(string $name, int $age):string {
// Here, we have short, readable conditions that return the value early.
	if($age < AGE_THRESHOLD) {
		return "Sorry, $name, you are too young to enter";
	}
	
// Without any further logic, we return the default value.
	return "Welcome, $name";
}
```

This style is sometimes more readable with simpler data types, and usually creates shorter functions. Either way, ensure you make a decision of what style to use, and maintain consistency throughout your codebase.

## A function should only ever do one thing, as indicated by its name
