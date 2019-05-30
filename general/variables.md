# Variables

## Use camelCase for variable naming

There are many standard libraries that are in use within the PHP.Gt ecosystem that use camelCase property names. Most importantly, property naming convention must follow how libraries such as [Dom](https://php.gt/dom) or [Fetch](https://php.gt/fetch) are defined, which provide standardised APIs that come from predefined web APIs.

## Never use global variables. Use a class to handle superglobals

PHP supports object oriented programming, but global variables undermine some benefits introduced by OOP. Superglobals, such as `$_GET`, `$_COOKIE`, etc. should be handled by middleware before accessing.

Source code is most readable when scope is limited. Globals can be read _and_ modified anywhere in any class, which makes it very difficult to track down usage.

There are many other cons for using globals, but in short, always think really hard when you're about to use a global variable.

## Properties should always be declared

PHP allows any property to be set on an object, from anywhere in the code. Some say this is a feature; some consider it bad practice. To aid readability and maintainability, always ensure that a class has the property declared before it is accessed or assigned.

## Variables should always be declared at the top of the block they are used in

To aid readability and maintainability, wherever a variable is used it should be assigned at the top of the block it is available to.

Languages like Java and C have their variables block scoped. Block scoping means that variables declared in a block between braces, including within `if` and `for` blocks, **cannot** be accessed from outside of that block.

In PHP however, variables are function scoped, meaning that all variables within a function are available to that function. It becomes difficult to read code where a variable is declared for the first time within a nested block of code, to then be later used in a parent block. To avoid unreadability, always declare variables at the top of the most-outer block they are used.
