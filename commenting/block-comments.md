# Block comments
## Block comments should only be used to provide class and method documentation in the form of doc blocks

Since PHP 7's release, a lot of docblock functionality has become redundant. For example, there is no need to annotate the types of properties or functions' return types, as this is all very clear from the function's signature.

Doc blocks are still useful to document the purpose of classes and functions, although it is always better to have the class name and function name do this for you. Self documenting code is a key point in writing [Clean Code][clean-code].

A good example of good block comments is explaining to future developers (or future you) the consequences or intent for certain classes or functions.

## Comments, along with docblocks, should be sparse and punchy to avoid stale documentation

Always try to explain yourself in code before a comment is written. This avoids comment noise, or comments that become out of date from the code that they represent.

Code should never be commented out. When using version control, just delete the code, as it can be added back later if needed from the source history.

Inline comments should start from column 0 in order to stand out from the flow of the program.

Comments should mainly be used to describe justification for doing something in a particular manner, or explain intent or consequences of calling the code that is not inherently obvious.
 
[clean-code]: https://www.oreilly.com/library/view/clean-code/9780136083238/
