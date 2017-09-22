# Brace indentation

## One level of indentation should be applied within, and only within, the braces.

Always ensure that within any block of braces, exactly one level of indentation is used. New indentation should never be added without the use of surrounding brances where the language permits them.

Bad example: 

```php
<?php
class GoodExample extends Something {
	public function braceExample() {
		$maximum = 0;
		
		while($maximum < $this->total;) {
			if(!$this->elementExistsAtIndex($i)) {
				break;
			}
		}
		
		$this->initialise();

// Note the extra level of indentation, without any reason to do so:
			for($i = 0; $i < $maximum; $i++) {
				$this->setNew($i);
			}
			
		$this->complete();
	}
}
```

## Conditionals within brackets should not gain extra indentation when breaking onto separate lines.

When breaking long conditionals over multiple lines, the horizontal flow of the code should not be interrupted.

Good example:

```php
if($details instanceof GoodExample
&& $details->canDoSomething()
&& $details->maximum < $maximum) {
	$details->doSomethingElse();
}
```

Bad example:

```php
if($details instanceof GoodExample
	&& $details->canDoSomething()
	&& $details->maximum < $maximum) {
	$details->doSomethingElse();
}
```

## Never leave conditional statements unbraced or unindented.

Braces allow multiple statments to be bundled into a single execution path for a conditional or loop. In PHP and many other programming languages, it is possible to omit braces. When no braces are used, the interpreter will treat the single next statement as the execution path for that conditional or loop.

This is bad practice as it is less readable and can cause unexpected errors when refactoring. Always use braces and correct indentation.

Good example:

```php
while($details->is_alive) {
	if(empty($details->message_queue)) {
		continue;
	}
	
	foreach($details->message_queue as $message) {
		processMessage($message);
	}
}
```

Bad example:

```php
while($details->is_alive) {
	if(empty($details->message_queue)) continue;
	foreach($details->message_queue as $message) processMessage($message);
}
```
