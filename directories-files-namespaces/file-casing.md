# File casing

## Files and directories should be lowercase-hyphenated where not namespace-mapped.

By default, all files and directories should be lowercase wherever appropriate. Where words need to be split, a hyphen should be used.

+ `/var/www/example.com/src/asset/logo.png`
+ `/var/www/example.com/src/page/about-us.html` 
+ `/var/www/example.com/src/page/blog/index.php`
+ `/var/www/example.com/src/page/items-for-sale.html`

## Namespace-mapped files and directories must use `UpperCamelCase`.

All PHP files and directories within the namespace root directory of a project should respect the same casing as the namespaces and class names contained.

Namespaces and classes are written in UpperCamelCase, so where files or directories are used in a namespaced path, UpperCamelCase should be used. As in [PSR-4][psr-4], the filename of a PHP class file should be identical to the class name.

For example, assuming the "ExampleApp" namespace root is the src/class directory:

`/var/www/example.com/src/class/Model/Vehicle.php`

```php
<?php
namespace ExampleApp\Model;

class Vehicle {
// ...
}
```

`/var/www/example.com/src/class/Analytics/TrackingCookie.php`

```php
namespace ExampleApp\Analytics;

class TrackingCookie {
// ...
}
``` 
## Web-mapped files and directories must use `lowercase-hyphenated-words`.

PHP is commonly used as a web language, and when PHP scripts or their HTML counterparts are loaded by a router for a web request, their filenames should map to the requested URL in context of the page root of the project.

Assuming the page root of the project is `src/page`, a requested URL of `http://example.com/shop/item` should match to `src/page/shop/item.html` and/or `src/page/shop/item.php`. Where a URL can be accessed with a deeper path, `index` files should be used.

Examples: 

+ `http://example.com/` => `src/page/index.html`, `src/page/index.php`
+ `http://example.com/about-us` => `src/page/about-us.html`, `src/page/about-us.php`
+ `http://example.com/shop` => `src/page/shop/index.html`, `src/page/shop/index.php`

[psr-4]: http://www.php-fig.org/psr/psr-4/
