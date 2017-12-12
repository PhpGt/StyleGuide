# Outline

## The term "class" refers to all classes, interfaces, and traits.

Throughout the StyleGuide, the term "class" refers to classes, interfaces, traits and other similar structures.

## A class should only ever be autoloaded - never use `require` or `include`.

Apart from one exception, the Composer autoloader, there should never be any use of `require` or `include` statements. Every class within the system should be addressable using autoloaders, using the [PSR-4 Autoloader standard][psr-4] where possible.

If PSR-4 is not adhered to for some reason, such as utilising [Path Mapping][path-mapping] class names that reference URLs to class names, there should be a formal alternative autoloader that has well defined, documented and predictable behaviour.

[psr-4]: https://github.com/PhpGt/Csrf/issues/46
[path-mapping]: https://github.com/PhpGt/StyleGuide/blob/master/directories-files-namespaces/path-mapping.md
