# Arrays

## Data structures representing collections should be array-accessible and/or iterable

In PHP, arrays are actually "ordered maps" that are used to contain a collection of items. When designing your own data structures, if an object represents a collection of items it should be array-accessible, using the most appropriate interface:

+ `ArrayAccess` for collections that are referred to by index
+ `Iterator` for collections that will be used within loops

Not all types of collection should be both an `ArrayAccess` and an `Iterator`. For example, imagine a class that represents a large dataset from a database. It may make sense to only implement the `Iterator` functions, so the data can be streamed rather than all loaded into memory at once. 

## Data structures representing individual items should use getter functions

When designing your own data structures, if an object represents a single item, its data attributes should be accessed via getter functions, rather than as an array-like object, or as public properties where acceptable.

Public properties should be used sparingly, and when they are needed it is recommended to consider [read-only properties][read-only] or [magic methods][magic-methods] to provide access to an object's internal data, rather than exposing properties directly. This allows for exposing read-only properties as well as improving maintainability when code is refactored in the future.

When getter functions are used on objects with unknown/arbitrary data contents, such as a database row, the getters should be provided using a [type safe interface][type-safe-getter].

## Associative arrays should only be used for simple key-value-pairs

Storing data within a native array in PHP should only be done when dealing with simple key-value-pairs, and should always be wrapped by an object's getters/setters. This allows for improving and refactoring the functionality of an object without having backwards breaking side effects.

## Use built-in functions rather than operators to manipulate array contents

It's possible to __union__ two arrays with the `+`, and __push_ an item into an array with `[] =`, but this style of coding has low readability. Unless a union is expected, use the `array_merge` function, and always use `array_push` or `array_unshift` to add an item into an array (even if there's only one item being added).

[magic-methods]: https://php.net/manual/en/language.oop5.magic.php
[read-only]: https://www.php.net/manual/en/language.oop5.properties.php#language.oop5.properties.readonly-properties
[type-safe-getter]: https://www.php.gt/typesafegetter
