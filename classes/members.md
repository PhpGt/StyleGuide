# Members

## Constants should only be declared on a class

Class constants can be read by [importing the class][importing] or fully addressing it by namespace, so there is no reason to ever define a global constant.

## Constants should use `UPPERCASE_UNDERSCORED`

There is no technical requirement for any class member to be defined in any particular case. The benefits of using different naming conventions is that it increases readability for programmers browsing the code, providing as much semantics as possible with little to no extra effort.

Using the uppercase underscored convention allows programmers to infer what is a fixed value.

## Properties should use `$camelCase`

There are many standard libraries that are in use within the PHP.Gt ecosystem that use camelCase property names. Most importantly, property naming convention must follow how libraries such as [Dom][dom] or [Fetch][fetch] are defined, which provide standardised APIs that come from predefined web APIs.

[importing]: http://php.net/manual/en/language.namespaces.importing.php
[dom]: https://php.gt/dom
[fetch]: https://php.gt/fetch
