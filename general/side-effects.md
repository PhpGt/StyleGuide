# Side effects

## Every `.php` library file should contain one class exactly

If a repository is a _library_, **every PHP file** should declare one class exactly and cause no other side effects.

If a repository is a _project_, the same should be true for the majority of PHP files, with only bare-minimum essential entry point PHP files executing logic with side effects. PHP project files with side effects **must not** declare new classes.

## Every `.php` library file should be side effect free

The term "side effects" means execution of logic **merely from including the file**.

For example, the following file has a side effect of outputting content to STDOUT:

```
<?php
echo "Hello, World!";
```

Including the above file affects output, whereas including the following file does not:

```
<?php
class Greeter {
	public function sayHello() {
		echo "Hello, World!";
	}
}
```

A software "library" means a repository of code that has no functionality without being included and used by a software project as a dependency.

A software "project" means a repository of code that has its own functionality and can include other software libraries as dependencies.

An example "library": [phpgt/dom: The DOM API for PHP 7 applications.][phpgt/dom]. The DOM library does not have any functionality of its own, but can be used by projects to manipulate HTML documents using the contained classes. All files within the library can be included without any side effects.

An example "project": [phpgt/webengine: Rapid development engine for PHP 7 applications.][phpgt/webengine]. The webengine project can be used to load and serve web applications. Most files within the project can be included without any side effects, apart from a few procedural style files used to initiate web requests, or serve web pages.

[phpgt/dom]: https://github.com/phpgt/dom
[phpgt/webengine]: https://github.com/phpgt/webengine
