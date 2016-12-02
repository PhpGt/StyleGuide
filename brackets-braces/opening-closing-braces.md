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

## Closing braces should always be placed at the start of their own line.

With respect to the current indentation level, closing braces should always be placed at the start of their own line, with no meaningful tokens before or after the brace on that line.

This rule prevents short functions or blocks from being condensed into one line.

Good example:

```php
class GoodExample {

public function __construct(int $size) {
	if($size === 0) {
		Logger::info("Size is 0.");
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
	if($size === 0) { Logger::info("Size is 0."); }
}

public function aShortFunction():void {	$this->complete(); }

}#
```