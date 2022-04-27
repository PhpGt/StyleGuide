# Functions

## Limit function length

A function should rarely grow to 50 lines long, and should never be 100 lines long. A rule of thumb is to have a soft limit of 50 lines for function length. Hitting this limit indicates that the function's implementation is too specific and requires refactoring.

Try to keep a function as short as possible. When a function becomes too long, describe what its logical steps are, and use that description to name child functions that can be called in order from the now abstract parent function.

## Ensure return points are consistent

## A function should only ever do one thing, as indicated by its name
