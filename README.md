# PHP 7 coding styleguide

This guide describes the preferred PHP coding style within core [PHP.Gt](https://github.com/phpgt) repositories and as a basis for other projects' style guides.

Individual developers and teams are likely to have their own strong views on certain coding styles, so this set of documents should be seen as **a guide, not a rulebook**. That being said, everything that is documented here is the preference of core developers, so please consider the points within before submitting pull requests.

The intent of this document is to help guide the style of code contributions to maintain a consistent style throughout repositories, and to define and justify the decisions made within; some preferences of this styleguide are substantially different and in some areas unorthodox. For a more mainstream and widely adopted styleguide, please see [PHP Framework Interop Group's PSR-2][psr2].

[psr2]: http://www.php-fig.org/psr/psr-2/

## Overview

The following example code shows an overview of the style proposed in this guide.

```php
<?php
namespace FastFood\Page;

use FastFood\Logic\OrderLogic;
use FastFood\Menu\MenuFactory;
use Vendor\Food\FoodOrderInterface;

class OrderPage extends OrderLogic implements FoodOrderInterface {
	const TYPE_MAIN = "order-type-main";
	const TYPE_VEGETARIAN = "order-type-vegetarian";
	const TYPE_VEGAN = "order-type-vegan";
	const TYPE_GLUTENFREE = "order-type-glutenfree";

	/** @var OtherClass The other example class in this snippet */
	private $menu;

	public function go():void {
		$this->menu = MenuFactory::create($_GET["type"]);
		$this->sampleMethod($this->menu->getName(), $this->menu->getSize());
		$output = $this->longMethodWithManyArgs(
			$this->getDefaultSize(),
			123,
			"example"
		);
	}

	private function sampleMethod(string $name, int $size = 0):void {
		$max_size = OtherClass::getMaxSize($name);

		if($size === 0) {
			$this->menu->fillEmpty(OtherClass::getDefault());
		}
		elseif($size > $max_size) {
			$size = $max_size;
		}
		else {
			switch($size) {
			case OtherClass::SIZE_INDIVIDUAL:
				$this->menu->setStyle("individual");
				break;

			case OtherClass::SIZE_FAMILY:
				$this->menu->setStyle("family");
				break;

			default:
				$this->menu->setStyle(Menu::SIZE_DEFAULT);
				break;
			}
		}
	}

	public function longMethodWithManyArgs(
		int $first_number,
		int $second_number = 0,
		string $example_string = null
	):Menu {
		$duplicate = MenuFactory::create($this->menu->getType());

		if($duplicate->getSize() !== 0
		&& $duplicate->name === $example_string) {
			return MenuFactory::createDefault();
		}

		return $duplicate;
	}
}
```

## Automatic fixer

To automatically fix code in accordance with this styleguide, a set of [PHP-CS-Fixer rules][PHP-CS-Fixer] have been written. With one command, the fixer can be run against a file or directory.

To use the automatic fixer:

```
# 1. Get a copy of the fixer:
git clone git@github.com:PhpGt/PHP-CS-Fixer
cd PHP-CS-Fixer
composer install

# 2. Run the fixer against a directory:
php gt-fix /path/to/repo/src
```

## Concepts of this styleguide

Please see a simplified bulleted list below. Click the headings for more information, examples and justification behind the decisions.

### [General concepts](general)

+ The first line of all `.php` files should be exactly "`<?php`".
+ Never use the closing PHP tag (`?>`).
+ Never use PHP short tags.
+ All files must only use `UTF-8`, without `BOM`.
+ Always use UTC timezone to store date and time.
+ Every `.php` library file should contain one class exactly.
+ Every `.php` library file should be side effect free.
+ Singular words (e.g. item, stylesheet, user) should be used throughout files and code instead of plurals.
+ Avoid Hungarian Notation, where file/variable names that indicate their type.
+ Use snake_case for variable naming.
+ Never use global variables, except for superglobals.
+ Properties should always be declared.
+ Variables should always be declared at the top of the block they are used in.

### [Indentation and whitespace](indentation-whitespace)

+ Use the tab character for indentation.
+ Avoid "double-indenting" blocks of code where no indentation is necessary for readability.
+ Do not leave whitespace at the end of lines.
+ Be as strict as is sensible to enforce 80 character lines.
+ Limit to four levels of indentation.

### [Brackets and braces](brackets-braces)

+ Opening braces should always be placed at the end of the line.
+ Closing braces should always be placed at the start of their own line.
+ One level of indentation should be applied within, and only within, the braces.
+ Conditionals within brackets should not gain extra indentation when breaking onto separate lines.
+ Never leave conditional statements unbraced or unindented.

### [Spaces](spaces)

+ No extra space should be placed after a control structure keyword or function name.
+ Opening brackets should not have a space after, closing brackets should not hace a space before.
+ Commas separating variable lists should have a space or newline after, no whitespace before.
+ A space should surround binary and ternary, but not unary operators.

### [Directories, files and namespaces](directories-files-namespaces)

+ Directories and files must either be namespace-mapped or web-mapped.
+ Namespaces must map to file paths, as per PSR-4.
+ Namespace-mapped files and directories must use `UpperCamelCase`.
+ Namespaces and classes must use `UpperCamelCase`.
+ Web mapped files and directories must use `lowercase-hyphenated-words`.

### [Classes](classes)

+ The term "class" refers to all classes, interfaces, and traits.
+ A class should only ever be autoloaded - never use `require` or `include`.
+ Constants should only be declared on a class.
+ Constants should use `UPPERCASE_UNDERSCORED`.
+ Properties should use `$lowercase_underscored`.
+ Methods should use `camelCase()`.
+ All parameters should define their type where possible.
+ All methods should define their return type where possible.
+ Methods should avoid becoming longer than 20-50 lines.
+ Classes should have all or no static methods.

### [Databases](databases)

+ Queries should be organised into a Query Collection Hierarchy.
+ Tables should use `lowercase_underscored`.
+ Related should use an underscore to indicate their hierarchy.
+ Columns should use `lowercase_underscored`.
+ Primary keys should be called `id`.
+ Columns can have optional descriptions to uniquely identify their purpose.
+ Foreign key column names should match their referenced column.
+ Foreign key constraint names should reference both tables and columns uniquely.

### [Commenting](commenting)

+ For inline comments, double-slash comments (`//`) should be used.
+ Inline comments should have no indentation, starting from column 1.
+ Inline comments can span multiple lines, prefixed with the double-slash.
+ Block comments should only be used to provide class and method documentation in the form of doc blocks.
+ Comments, along with docblocks, should be sparse and punchy to avoid stale documentation.

### [Data structures](data-structures)

+ Data structures representing collections should be array-accessible.
+ Data structures representing individual items should be property-accessible.
+ Associative arrays should only be used for simple key-value-pairs.
+ Move associative arrays to an object's getter/setter storage where possible.
+ Static classes should only be used when truly stateless.
+ Private methods should be preferred over anonymous functions where appropriate.
+ Anonymous functions should never exceed 5-10 lines.

### [Documentation](documentation)

+ Use full stops to end full sentences.
+ Don't use full stops to end fragmented sentences.
+ Choose either full sentences or fragments in lists (not both).
