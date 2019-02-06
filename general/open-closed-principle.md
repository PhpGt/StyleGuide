# Open-closed principle

> In object-oriented programming, the open/closed principle states "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"; that is, such an entity can allow its behaviour to be extended without modifying its source code. (Source: [Wikipedia][wiki-open-closed])

It is important to use the techniques offered by using object oriented programming to encapsulate data within your application, but not to prevent future extension of your code and its functionality. This page of the styleguide adds points to keep the open-closed principle in mind.

## Avoid using final keyword unless necessary

Making a class `final` does not treat it as `const` - final classes are still immutable and anywhere in code that has reference to them can manipulate the public properties and call the public functions.

Making a class final means that nowhere else in code can `extend` the class. There may be certain times that this is important, for example when enforcing security restrictions, but in general unless there is reason to make a class final, it breaks the open-closed principle.

## Avoid calling functions in global namespace

In PHP, namespaces are separated using the backslash character (`\`).

Putting a backslash before a function will ensure the function is called in the global namespace, even if there is a function by the same name in the current namespace. Doing this ensures your application is _closed for extension_ in the same way that marking a class as `final` is, and should be avoided so that future developers have the oportunity to extend functionality without having to modify the source.

[wiki-open-closed]: https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle
