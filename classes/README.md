# Classes

## [Outline](outline.md)

+ The term "class" refers to all classes, interfaces, and traits.
+ A class should only ever be autoloaded - never use `require` or `include`.

## [Members](members.md)

+ Constants should only be declared on a class.
+ Constants should use `UPPERCASE_UNDERSCORED`.
+ Properties should use `$camelCase`.

## [Methods](methods.md)

+ Methods should use `camelCase()`.
+ All parameters should define their type where possible.
+ All methods should define their return type where possible.
+ Methods should avoid becoming longer than 20-50 lines.
+ Classes should have all or no static methods.
