# Double-indentation

## Avoid "double-indenting" blocks of code where no indentation is necessary for readability.

The purpose of indenting code is to make it visually clear where a block of control starts and ends. With respect to [using 80 character maximum line lengths][line-length], care should be taken to only indent blocks that actually increase readability.

Certain control blocks, such as **class definitions** and **switch statements** do not need to have double-indentation, because it is perfectly obvious that code is within the block. For classes, because [every `.php` library file should contain one class exactly][side-effects], the contents of the class block can be left unindented, starting from column 1.

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

}#
```

In the above example, it is obvious that all members of the class (constant, private variables and function) are part of the contained class, because [every PHP library file should always only have one class in it][side-effects]. We can save one level of indentation in every file by not double-indenting the contents of a class.

The hash is added to the closing brace of the class as a helpful indicator to prevent programmers from thinking they have already closed their function's brace.

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

The above example, even though is incredibly over-simplified, is already **four levels of indentation** nested by the time the first execution is made. The amount of indentation required in real-world complex programs is only going to exaggerate this, inevitably hindering readability.

As a follow on from this section of the guide, it is recommended to have a [limit of four levels of indentation][limit-indentation] anyway.

[line-length]: line-length.md
[side-effects]: ../general/side-effects.md
[limit-indentation]: limit-indentation.md
