# Naming convention

## Singular words (e.g. item, stylesheet, user) should be used throughout files and code instead of plurals.

Directories containing a type or category of file, for example Stylesheet files, Page Logic PHP scripts, or static asset files should be singular words, for example: `style`, `page`, `asset`, rather than `styles`, `pages`, `assets`.

Variables containing a collection of values or references should be named as a singular collection in preference of a plural word, for example: `$nameList`, `$stylesheetList`, `$elementList`, rather than `$names`, `$stylesheets`, `$elements`.

Naming collections as a "list" rather than a plural helps readability, especially when iterating over collections.

Using list (more readable):

```php
foreach($ingredientList as $ingredient) {
	$dish->add($ingredient);
}
```

Using plural (less readable, error prone):

```php
foreach($ingredients as $ingredient) {
	$dish->add($ingredients);
}
```

## Avoid Hungarian Notation, where file/variable names that indicate their type.

Variables have types and files have extensions. This is enough to infer its type. Hungarian Notation is a naming convention in which the name of an entity indicates its type or intended use. This is a dated convention and should be avoided.

In the above example, collections of variables are preferred to be suffixed with "list". In some languages, this would violate the anti-Hungarian Notation due to the native type of `List`, but in PHP there is no List so we can be safe in using the word for this purpose.

On that note, avoid calling things `$somethingArray`. Implying that the variable is an array makes refactoring more difficult and error prone, when in the future the variable may not be an array any more.