# General concepts

## [PHP tags](php-tags.md)

+ The first line of all `.php` files should be exactly "`<?php`"
+ Never use the closing PHP tag (`?>`)
+ Never use PHP short tags

## [Standards](standards.md)

+ All files must only use `UTF-8`, without `BOM`
+ Always use UTC timezone to store date and time

## [Side effects](side-effects.md)

+ Every `.php` library file should contain one class exactly
+ Every `.php` library file should be side effect free

## [Naming convention](naming-convention.md)

+ Singular words (e.g. item, stylesheet, user) should be used throughout files and code instead of plurals
+ Avoid Hungarian Notation, where file/variable names that indicate their type

## [Variables](variables.md)

+ Use snake_case for variable naming
+ Never use global variables, except for superglobals
+ Properties should always be declared
+ Variables should always be declared at the top of the block they are used in
