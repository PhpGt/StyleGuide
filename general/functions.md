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

The name of a function should reveal its intention. This can lead to more verbosity in your code, but that's a good thing. The length of a function's name is usually inversely proportional to the length of the function, because a more specific function name tends to do less, and a function that does less is always a cleaner decision.

Consider two scenarios. The first, a function that returns differently depending on a set of circumstances:

```php
function getMenuItems(string $constraint = null):array {
	$items = MenuFactory::getAll();
	
	if($constraint === "vegetarian") {
		$items = array_filter($items, fn($item) => !$item->containsMeat());
	}
	if($constraint === "gluten-free") {
		$items = array_filter($items, fn($item) => !$item->containsGluten());
	}
	
	return $items;
}
```

From a reader's perspective, one needs to read the whole function to understand the context and meaning of the `$constraint` variable. Compare this to the second style, where a separate function describes each constraint:

```php
function getAllMenuItems():array {
	return MenuFactory::getAll();
}

function getVegetarianMenuItems():array {
	return array_filter(MenuFactory::getAll(), fn($item) => !$item->containsMeat());
}

function getGlutenFreeMenuItems():array {
	return array_filter(MenuFactory::getAll(), fn(item) => !$item->containsGluten());
}
```

This second example immediately explains what each function is doing, and means each function can be reduced to a single line of code. 

Always be as specific as possible with the name of a function, so it describes exactly what it is doing, favouring multiple, longer function names over a single function that does more than one thing.

Another rule of thumb is to be wary of words like "and" and "or" in function names, as these indicate that the function does more than one thing.

A benefit of this extra verbosity is that your code becomes extra searchable by IDEs. In the above examples, the multiple functions allow developers to search for functions containing the word "vegetarian", allowing for much faster navigation through the code.

## Functions should either mutate or query the system, never both

For clarity throughout your code, a function's implementation should take the form of a mutator or query. This is sometimes referred to as "[command/query separation][command-query-separation]".

A "mutator", or "command" performs an action, changing the state of the system. For example, `$userRepo->createNewUser("cody")`, `$shop->emptyCart()`, `$user->setVisibility(true)`, `$ui->showNotification("Item added to cart")`.

A "query" retrieves information without having any side effects. For example, `$userRepo->getUserById(105)`, `$item->containsMeat()`, `$input->validate()`.

[command-query-separation]: https://www.martinfowler.com/bliki/CommandQuerySeparation.html
