# Inline comments

## For inline comments, double-slash comments (`//`) should be used

Inline comments are used to alert future developers to something **vital** about the code below it. 

**The best comment is a comment that isn't written;** wherever possible, code should be written in small punchy functions that describe themselves. A comment should only be for describing non-obvious code behaviour, or justifying decisions. As inline comments do not roll over onto subsequent lines, they promote shorter sentences which is always a good thing.

## Inline comments should have no indentation, starting from column 1

Any comment in the code should contain important information. Starting the comment from column 1 stands out to developers.

Good example:

```php
class GoodExample {
	public function doSomething(OtherClass $thing, int $type) {
		$detail = $thing->getDetail($type);
		
// It is important to know that $type must be valid, otherwise an exception is thrown, and $thing must roll back.
		try {
			$thing->move();
		}
		catch(Exception $exception) {
			$thing->rollBack();
		}
	}
}
```

## Inline comments can span multiple lines, prefixed with the double-slash

Sometimes writing comments is necessary. When inline comments (comments within the code) are used, always use double-slash commants as these can never be accidentally terminated.

Good example:

```php
class GoodExample {
	public function replaceString(string $input):string {
		$output = preg_replace(Matcher::REGEX, Matcher::REPLACEMENT, $input);

// Note that $output could be null if using simple match like /.*/ or /.+/
		if(is_null($output)) {
			throw new MatcherExcpetion("No match on string: $input");
		}
		
		return $output;
	}
}
```

Bad example:
```php
class GoodExample {
	public function replaceString(string $input):string {
		$output = preg_replace(Matcher::REGEX, Matcher::REPLACEMENT, $input);

/* Note that $output could be null if using simple match like /.*/ or /.+/ */
// SYNTAX ERROR: The comment is broken by the regex.
		if(is_null($output)) {
			throw new MatcherExcpetion("No match on string: $input");
		}
		
		return $output;
	}
}
```
