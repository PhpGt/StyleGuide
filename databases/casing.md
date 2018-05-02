# Casing

## Tables should use `SnakeCase`

Table names should be treated similarly to class names, as very commonly a class will be used as a model to a table of the same name.

// TODO: Exception: junction tables

## Columns should use `camelCase`

When columns are referenced in PHP using model classes, they are done so using object properties, so using camel case is consistent with how object properties are written and accessed.

## Primary keys should be called `id`

// TODO.
