# Members

## Constants should only be declared on a class

Class constants can be read by [importing the class][importing] or fully addressing it by namespace, so there is no reason to ever define a global constant.

## Constants should use `UPPERCASE_UNDERSCORED`

There is no technical requirement for any class member to be defined in any particular case. The benefits of using different naming conventions is that it increases readability for programmers browsing the code, providing as much semantics as possible with little to no extra effort.

Using the uppercase underscored convention allows programmers to infer what is a fixed value.

## Properties should use `$camelCase`

There are many standard libraries that are in use within the PHP.Gt ecosystem that use camelCase property names. Most importantly, property naming convention must follow how libraries such as [Dom][dom] or [Fetch][fetch] are defined, which provide standardised APIs that come from predefined web APIs.

## Classes should have all or no static members

It is easy to say [static members are evil][evil-static], but without concrete justification. The rule of thumb promoted in this guide it to never mix static with non-static members within the same class, as it leads to confusion and unreadability.

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

[evil-static]: https://www.google.co.uk/search?q=static+methods+are+evil
[importing]: http://php.net/manual/en/language.namespaces.importing.php
[dom]: https://php.gt/dom
[fetch]: https://php.gt/fetch
