# Line length

## Do not leave whitespace at the end of lines.

Git will warn you about patches that introduce trailing whitespace, and can optionally strip the trailing whitespace for you; however, if applying a series of patches, this may make later patches in the series fail by changing their context lines.

## Be as strict as is sensible to enforce 80 character lines.

When declaring functions with long names and/or multiple parameters, especially when using type hinting, it is very easy to hit the 80 character ruler. When function declarations would be wider than 80 characters, always break the parameters into separate lines, as shown below:

Good example (wrapped due to 80 character ruler):

```php
public function aQuiteLongFunctionName(
	ExampleClass $first_parameter,
	string $second_parameter,
	int $size = 0
):ExampleClass {
	$this->example();
}
```

Bad example (function parameters require scrolling/wrapping):

```php
public function aQuiteLongFunctionName(ExampleClass $first_parameter, string $second_parameter, int $size = 0):ExampleClass {
	$this->example();
}
```

Function body width is less strict. If absolutely necessary, the contents of a function can span over 80 characters, but hitting the 80 character ruler is a good excuse to re-assess the complexity of your current function, or refactor the amount of indentation.

## Limit to three levels of indentation.

Each level of indentation can be seen as a new level of abstraction to a function's complexity. It is best practice for every function to do one thing and one thing only, limiting its abstraction to one.

One level of abstraction means just the one level of indentation, but this isn't always feasible in the real world, so the guideline maximum of three indentation levels is introduced to minimise function complexity.

**Less indentation forces simplification through refactoring.**

Good example:

```php
public function makeConnection(Settings $settings):Connection {
	$connection = $this->checkConnectionInitialised();
	$this->openConnection($connection);
	$this->waitForConnection($connection);

	return $connection;
}
```

Bad example:

```php
public function makeConnection(Settings $settings):Connection {
	if(is_null($this->connection)) {
		$this->connection = new Connection();

		if($settings->type === Settings::TYPE_INBOUND) {
			if(!$settings->read_only) {
				$this->connection->accept_inbound = true;
			}
		}
	}

	try {
		$this->connection->open($settings);

		if(!$this->connection->listen()) {
			foreach($this->connection->poolList as $pool) {
				if(!$pool->queued) {
					$this->connection->freePool($pool);
				}
			}
		}
	}
	catch(ConnectionException $exception) {
		$this->response->showError($exception->getMessage());
	}

	while(count($this->connection->waiting_pool) > 0) {
		sleep(1);
	}

	return $this->connection;
}
```
