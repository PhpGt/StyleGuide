# Double-indentation

## Avoid "double-indenting" blocks of code where no indentation is necessary for readability.

The purpose of indenting code is to make it visually clear where a block of control starts and ends. With respect to [using 80 character maximum line lengths][line-length], care should be taken to only indent blocks that actually increase readability.

> Each indentation within code produces a new line of attention for the reader to keep track of while skimming your code. Aiming for less lines of attention produces more readable code.

Within this guide, **only blocks that affect scope or control should be indented**. Certain blocks, such as **switch statements** do not need to have double-indentation, because the contents of the blocks are within the same scope, and scope is perfectly obvious without indentation.

### Good example:

```php
<?php
namespace Example\App;

class GoodExample {
	const EXAMPLE_CONSTANT_ONE = 1;
	const EXAMPLE_CONSTANT_TWO = TWO;
	private $spam;
	private $eggs;

	public function noNeedForIndentation(int $count):void {
		switch($count) {
		case EXAMPLE_CONSTANT_ONE:
			$this->doSomething();
			break;

		case EXAMPLE_CONSTANT_TWO:
			$this->doSomethingElse();
			break;
		}
	}
}
```

Within switch statements, it is easy to scan the eye down the code to see where each case starts, without having to indent the block again.

### Bad example (too many indents):

```php
<?php
namespace Example\App;

class BadExample {

	const EXAMPLE_CONSTANT_ONE = 1;
	const EXAMPLE_CONSTANT_TWO = TWO;
	private $spam;
	private $eggs;

	public function noNeedForIndentation(int $count):void {
		switch($count) {
			case EXAMPLE_CONSTANT_ONE:
				$this->doSomething();
				break;

			case EXAMPLE_CONSTANT_TWO:
				$this->doSomethingElse();
				break;
		}
	}

}
```

As a follow on from this section of the guide, it is recommended to have a [limit of four levels of indentation][line-length] anyway.

[line-length]: line-length.md
[side-effects]: ../general/side-effects.md
