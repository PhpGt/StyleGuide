# Methods

## Methods should use `camelCase()`.

There are many standard libraries that are in use within the PHP.Gt ecosystem that use camelCase methods. Most importantly, method naming convention must follow how libraries such as [Dom][dom] or [Fetch][fetch] are defined, which provide standardised APIs that come from predefined web APIs.

## All parameters should hint their type where possible.

Hinting the type of function parameters improves readability for both humans and programming tools. Ambiguity is reduced, which in turn reduces code complexity and increases code quality.

Using type hints also self-documents functions, removing the need to use DocBlock comments to indicate what types are expected.

Unlike using DocBlocks, if an incorrect type is passed at runtime, the program is halted.

## All methods should define their return type where possible.

Hinting the return type of functions improves readability for both humans and programming tools. Ambiguity is reduced, which in turn reduces code complexity and increases code quality.

Using type hints also self-documents functions, removing the need to use DocBlock comments to indicate what types are expected.

Unlike using DocBlocks, if an incorrect type is returned at runtime, the program is halted.

## Methods should avoid becoming longer than 20-50 lines.

The sweet spot for method line length is between 5 and 15 lines. Having short functions benfits the code in many ways:

+ Forces breaking out abstraction into separate function calls which increases readability (and scanability)
+ Easy to fit onto a screen, for example in a code review session
+ Forces the _function_ of a method to be obvious

In [_Clean Code: A Handbook of Agile Software Craftsmanship_][clean-code-book], Robert Martin says:

> The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that. Functions should not be 100 lines long. Functions should hardly ever be 20 lines long.

There is no one rule that produces better quality code, but **use your own common sense** when deciding when it's time to break a function down into smaller functions, and use this guide's short recommendation as an excuse to address your code's complexity when functions reach 50 lines long.

## Classes should have all or no static methods.

It is easy to say [static methods are evil][evil-static], but without concrete justification. The rule of thumb promoted in this guide it to never mix static with non-static methods within the same class, as it leads to confusion and unreadability.

Good example (note that factory methods are within their own class, within their own file):

```php
class FoodOrder {
	public function __construct(Food $main, Food $side, Drink $drink) {
		// ...
	}
	
	public function cook() {
		// Do the cooking!
	}
}
```

```php
class FoodOrderFactory {
	public static function createFromMenu(MenuItem $menu):FoodOrder {
		$main = static::getMainCourseFromMenu($menu);
		$side = static::getSideDishFromMenu($menu);
		$drink = static::getDrinkChoiceFromMenu($menu);
		
		return new FoodOrder($main, $side, $drink);
	}
	
	public static function createFromCsv(string $csv):FoodOrder {
		list($main, $side, $drink) = static::parseCsv($csv);
	
		return new FoodOrder($main, $side, $drink);
	}
	
	protected static function getMainCourseFromMenu(MenuItem $menu):Food {
		// ...
	}
	
	protected static function getSideDishFromMenu(MenuItem $menu):Food {
		// ...
	}
	
	protected static function getDrinkChoiceFromMenu(MenuItem $menu):Food {
		// ...
	}
	
	protected static function parseCsv(string $csv):array {
		// ...
	}
}
```

Bad example:

```php
class FoodOrder {
	public function __construct(Food $main, Food $side, Drink $drink) {
		// ...
	}
	
	public static function createFromMenu(MenuItem $menu):FoodOrder {
		$main = static::getMainCourseFromMenu($menu);
		$side = static::getSideDishFromMenu($menu);
		$drink = static::getDrinkChoiceFromMenu($menu);
		
		return new FoodOrder($main, $side, $drink);
	}
	
	public static function createFromCsv(string $csv):FoodOrder {
		list($main, $side, $drink) = static::parseCsv($csv);
	
		return new FoodOrder($main, $side, $drink);
	}
	
	protected static function getMainCourseFromMenu(MenuItem $menu):Food {
		// ...
	}
	
	protected static function getSideDishFromMenu(MenuItem $menu):Food {
		// ...
	}
	
	protected static function getDrinkChoiceFromMenu(MenuItem $menu):Food {
		// ...
	}
	
	protected static function parseCsv(string $csv):array {
		// ...
	}
	
	public function cook() {
		// Do the cooking!
	}
}
```

[dom]: https://php.gt/dom
[fetch]: https://php.gt/fetch
[clean-code-book]: https://books.google.co.uk/books/about/Clean_Code.html?id=dwSfGQAACAAJ&redir_esc=y
[evil-static]: https://www.google.co.uk/search?q=static+methods+are+evil
