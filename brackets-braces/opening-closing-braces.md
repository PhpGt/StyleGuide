# Opening and closing braces

## Opening braces should always be placed at the end of the line.

A consistent use of brace placement is used in this styleguide. With no exceptions, opening braces are always placed at the end of the line before the block they are opening.

In this styleguide, the indentation within functions is also consistent. A new level of indentation should always indicate the start of a new block.

Good example:

```php
class GoodExample {

public function __construct(string $name) {
	try {
		$this->doSomething();
	}
	catch(ExampleException $exception) {
		$this->handleError($exception);
	}
}

public function doSomething() {
	for($i = 0; $i < 10; $i++) {
		ExampleClass::count($i);
	}
}

}#
```

Bad example:

```php
class BadExample
{

public function __construct(string $name)
{
	try
	{
		$this->doSomething();
	}
	catch(ExampleException $exception)
	{
		$this->handleError($exception);
	}
}

public function doSomething()
{
	for($i = 0; $i < 10; $i++)
	{
		ExampleClass::count($i);
	}
}

}#
```

## Closing braces should be placed at the start of their own line.

With respect to the current indentation level, closing braces should be placed at the start of their own line, with no meaningful tokens before or after the brace on that line.

Exception: a `do`'s `while`, or the semicolon of a closure:

```php
do {
	something();
} while($continue);

$closure = function($i, $j) {
	something($i + $j);
};
```

This rule prevents short functions or blocks from being condensed into one line.

Good example:

```php
class GoodExample {

public function __construct(int $size) {
	if($size === 1) {
		Logger::alert("Size is at 1, panic!");
	}
	else if($size < 5) {
		Logger::critical("Size is getting too low!");
	}
	else {
		Logger::info("Size is $size.");
	}

	if($size === 0) {
		Logger::emergency("Game over!");
	}
}

public function aShortFunction():void {
	$this->complete();
}

}#
```

Bad example:

```php
class GoodExample {

public function __construct(int $size) {
	if($size === 1) {
		Logger::alert("Size is at 1, panic!");
	} else if($size < 5) {
		Logger::critical("Size is getting too low!");
	} else {
		Logger::info("Size is $size.");
	}

	if($size === 0) { Logger::emergency("Game over!"); }
}

public function aShortFunction():void {	$this->complete(); }

}#
```