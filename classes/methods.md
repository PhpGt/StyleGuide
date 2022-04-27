# Methods

## Methods should use `camelCase()`

There are many standard libraries that are in use within the PHP.Gt ecosystem that use camelCase methods. Most importantly, method naming convention must follow how libraries such as [Dom][dom] or [Fetch][fetch] are defined, which provide standardised APIs that come from predefined web APIs.

## All parameters should hint their type where possible

Hinting the type of function parameters improves readability for both humans and programming tools. Ambiguity is reduced, which in turn reduces code complexity and increases code quality.

Using type hints also self-documents functions, removing the need to use DocBlock comments to indicate what types are expected.

Unlike using DocBlocks, if an incorrect type is passed at runtime, the program is halted.

## All methods should define their return type where possible

Hinting the return type of functions improves readability for both humans and programming tools. Ambiguity is reduced, which in turn reduces code complexity and increases code quality.

Using type hints also self-documents functions, removing the need to use DocBlock comments to indicate what types are expected.

Unlike using DocBlocks, if an incorrect type is returned at runtime, the program is halted.

## Methods should avoid becoming longer than 20-50 lines

The sweet spot for method line length is between 5 and 15 lines. Having short functions benefits the code in many ways:

+ Forces breaking out abstraction into separate function calls which increases readability (and scanability)
+ Easy to fit onto a screen, for example in a code review session
+ Forces the _function_ of a method to be obvious

In [_Clean Code: A Handbook of Agile Software Craftsmanship_][clean-code-book], Robert Martin says:

> The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that. Functions should not be 100 lines long. Functions should hardly ever be 20 lines long.

There is no one rule that produces better quality code, but **use your own common sense** when deciding when it's time to break a function down into smaller functions, and use this guide's short recommendation as an excuse to address your code's complexity when functions reach 50 lines long.

## Public functions should show the headlines of a class's functionality

This is sometimes referred to as the step-down rule. A class's functionality should be obvious by quickly scanning through its public functions. To aid readability, a class's public method(s) are its headlines. They should only be a few lines long, and their implementation should be an abstraction of private methods on the class. This allows developers to read the intent of functions much easier, and can optionally get more detail by jumping to the definition of the abstractions.

Abstractions should be written as private methods, stored in order of their execution. This acts like a newspaper: the headline is at the top, and if the reader decides they need more information, they can deep-dive into the content, but this should always be the decision of the reader, to avoid overwhelming them.

[dom]: https://php.gt/dom
[fetch]: https://php.gt/fetch
[clean-code-book]: https://books.google.co.uk/books/about/Clean_Code.html?id=dwSfGQAACAAJ&redir_esc=y
