# General concepts.

## [PHP tags](php-tags.md).

+ The first line of all `.php` files should be exactly: `<?php`.
+ Never use the closing PHP tag (`?>`).
+ Never use PHP short tags.

## [Standards](standards.md).

+ All files must only use `UTF-8`, without `BOM`.
+ Always use UTC timezone to store date and time.

## [Side effects](side-effects.md).

+ Every `.php` file should contain one class exactly.
+ Every `.php` file should be side effect free, apart from bare-minimum essential entry point files.

## [Naming convention](naming-convention.md).

+ Singular words (e.g. item, stylesheet, user) should be used throughout files and code instead of plurals.

## [Variables](variables.md).

+ Never use global variables, except for superglobals.
+ Properties should always be declared.
+ Variables should always be declared at the top of the scope they are used in.
