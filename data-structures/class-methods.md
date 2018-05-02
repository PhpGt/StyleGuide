# Class methods

## Static classes should only be used when truly stateless

Following this styleguide, [classes should have all or no static methods](../classes/methods.md), not both.

A class should only ever be static if it has no side effects to the state of the program. 

If calling any method of a static class updates internal data within the class, or persistent data is stored which affects subsequent flows of the program, the class should not be static as it represents/stores state.

## Private methods should be preferred over anonymous functions where appropriate

Accessing private/protected methods within the same class is allowed in an object oriented programming language. Having anonymous functions inline within code can cause maintenance issues and lowers refactorability.

Where possible, extract anonymous functions into their own named functions so they can be referred to by name.

## Anonymous functions should never exceed 5-10 lines

Sometimes the use of anonymous functions is required, but it should be important to keep the length of the functions incredibly short. If an anonymous function performs more than one function, split out the functionality into a private function within the class it is being called from, or introduce a new static utility class to contain the functionality.

Long anonymous functions become difficult to read and maintain, and are usually a good indicator of badly formed code.